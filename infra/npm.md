
# NPM resources

## npmjs org

We have a WireMock organization on NPM:
[~wiremock](https://www.npmjs.com/org/wiremock).
This will be used for official NPM releases like the Testcontainers module and other distributions.

For deployments from GitHub Actions, there is an `${{ secrets.NPM_PUBLISH_TOKEN }}` environment variable that can be enabled for your repository upon request.
This token will be renewed by the team periodically.
