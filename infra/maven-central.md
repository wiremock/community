# WireMock on Maven Central

WireMock has a lot of Java/JVM components,
and we do provide some automation for releasing to
the `org.wiremock` group which is administered by the
WireMock BDFL and other repository admins.

## Repository structure

- `org.wiremock` as a root. Core components like `wiremock` or `wiremock-standalone` will be under this root
  - `org.wiremock.extensions` - groupID for extensions
  - `org.wiremock.tools` - groupID for any associated developer tools (e.g. Maven plugins)
  - `org.wiremock.integrations.{type}` - groupID for integration libraries
    - `{type}`- A subgroup defining type of the integration, for example `testcontainers`, `springboot` or `kotlin`

## Setting up the release automation

### Getting access for a project

1. Submit a ticket using the _Maven Central Hosting_ issue template,
   provide all data there
2. If the repository is not on the `wiremock` GitHub organization,
   you will need to transfer it first.
3. COMING SOON - Sign the Contributor License Agreement.
   We need it to provide such an advanced permission like releasing with
   WireMock community signing keys.
4. Wait till the request is processed.
   The team will take care of OSSRH requests and provision secret variables
5. Setup the release automation on GitHub Releases

### Setting up GitHub Actions

The WireMock repository admins will provision 4 secret variables to the repository:

- `OSSRH_USERNAME` - username to be used for upload
- `OSSRH_TOKEN` - token/password to be used
- `OSSRH_GPG_SECRET_KEY` - private GPG key, all JARs deployed to Maven Central must be signed with it
- `OSSRH_GPG_SECRET_KEY_PASSWORD` - Password key for this secret

So, you will need to setup release steps in GitHub Actions to do the deployment.
We are yet to release custom GitHub Actions,
so for now you will need to copy&paste the code.
Normally we recommend releasing to both GitHub Packages and Maven Central,
hence some magic is needed.

#### For Maven

Example: [wiremock/wiremock-testcontainers-java](https://github.com/wiremock/wiremock-testcontainers-java)

```yaml
    steps:
      - name: Checkout
        uses: actions/checkout@v3

      - name: Configure Git user
        run: |
            git config user.email "actions@github.com"
            git config user.name "GitHub Actions"

      - id: install-secret-key
        name: Install gpg secret key
        run: |
          # Install gpg secret key
          cat <(echo -e "${{ secrets.OSSRH_GPG_SECRET_KEY }}") | gpg --batch --import
          # Verify gpg secret key
          gpg --list-secret-keys --keyid-format LONG

      - name: Setup Java
        uses: actions/setup-java@v3
        with:
          java-version: 11
          server-id: github
          distribution: 'temurin'
          cache: maven
 
      - name: Set Release Version
        id: vars
        shell: bash
        run: |
          echo "VERSION=${{ github.event.inputs.version }}" >> $GITHUB_OUTPUT
          mvn -ntp --batch-mode versions:set -DnewVersion=${{ github.event.inputs.version }}
          git diff-index --quiet HEAD || git commit -m "Releasing version ${{ github.event.inputs.version }}" pom.xml
        
      - name: Publish to GitHub Packages
        run: mvn -ntp --batch-mode -Dgpg.passphrase="${{ secrets.OSSRH_GPG_SECRET_KEY_PASSWORD }}" clean deploy -Prelease
        env:
          GITHUB_TOKEN: ${{ github.token }}

      - name: Set up Java for publishing to Maven Central
        uses: actions/setup-java@v3
        with:
          java-version: '11'
          distribution: 'temurin'
          server-id: ossrh
          server-username: MAVEN_USERNAME
          server-password: MAVEN_PASSWORD
      - name: Publish to the Maven Central
        run: mvn --batch-mode -Dgpg.passphrase="${{ secrets.OSSRH_GPG_SECRET_KEY_PASSWORD }}" clean deploy -Prelease,mavencentral-release
        env:
          MAVEN_USERNAME: ${{ secrets.OSSRH_USERNAME }}
          MAVEN_PASSWORD: ${{ secrets.OSSRH_TOKEN }}
```

#### For Gradle

See [wiremock/wiremock-state-extension](https://github.com/wiremock/wiremock-state-extension) for the example of the Gradle build definition.
See [wiremock/ecosystem #19](https://github.com/wiremock/ecosystem/issues/19) for the specialized Convention plugin which will make it easier.

GitHub Action Sample:

```yaml
name: Release

on:
  release:
    types: [published]

jobs:
  publish:
    runs-on: ubuntu-latest
    permissions:
      contents: read
      packages: write
    steps:
      - uses: actions/checkout@v3
      - name: Set up Java
        uses: actions/setup-java@v3
        with:
          java-version: '11'
          distribution: 'adopt'
      - name: Validate Gradle wrapper
        uses: gradle/wrapper-validation-action@v1

      - name: Determine new version
        id: new_version
        run: |
          NEW_VERSION=$(echo "${GITHUB_REF}" | cut -d "/" -f3)
          echo "new_version=${NEW_VERSION}" >> $GITHUB_OUTPUT

      - name: Publish package
        id: publish_package
        uses: gradle/gradle-build-action@v2.9.0
        with:
          arguments: -Pversion=${{ steps.new_version.outputs.new_version }} publish closeAndReleaseStagingRepository

        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          OSSRH_USERNAME: ${{ secrets.OSSRH_USERNAME }}
          OSSRH_TOKEN: ${{ secrets.OSSRH_TOKEN }}
          OSSRH_GPG_SECRET_KEY: ${{ secrets.OSSRH_GPG_SECRET_KEY }}
          OSSRH_GPG_SECRET_KEY_PASSWORD: ${{ secrets.OSSRH_GPG_SECRET_KEY_PASSWORD }}
```
