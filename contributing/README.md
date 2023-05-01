# Contributing to WireMock

[![a](https://img.shields.io/badge/slack-Join%20us-brightgreen?style=flat&logo=slack)](http://slack.wiremock.org/)

WireMock exists and continues to thrive due to the efforts of over 150 contributors,
and we continue to welcome contributions to its evolution.
Regardless of your expertise and time you could dedicate,
there're opportunities to participate and help the project!

## Ways to contribute

You can help make WireMock a better tool in a number of ways:

- Help other WireMock users and sharing tips
- Write or improve documentation
- Raise an issue if you discover a bug
- Contribute bug fixes, new features or enhancements
- Spread the word about WireMock, share your stories and contributions

## Helping users

- Join the [community Slack channel](http://slack.wiremock.org/),
  especially the `#help` channel we use for random Q&A
- Subscribe to the [`#wiremock` tag on StackOverflow](https://stackoverflow.com/questions/tagged/wiremock).
  Many questions are raised there, and it is a good opportunity to get StackOverflow medals :smile:
- If you have expertise with a particular WireMock component, e.g. _WireMock Java_ or the _Python WireMock Client_,
   maintainers will appreciate
  your help with triage of issue reports and feature requests!
  You can periodically check the components or subscribe to the repositories.

There is also a `#help-contributing` channel where newcomer contributors ask questions.
Make sure to join it too if you are interested in code or documentation.

## WireMock structure

[WireMock Ecosystem](https://github.com/wiremock/ecosystem) includes a lot of various components:
implementations, SDKs, extensions and integrations with other tools.
There are many repositories, and only a fraction of them, though the key ones,
are a part of the [WireMock organization](https://github.com/wiremock) on GitHub.
When contributing to WireMock, make sure to consult with the contributing guidelines of the repositories.

How to find a repository? There are a few options:

1. See the links below for key components
2. Consult with the [WireMock Ecosystem](https://github.com/wiremock/ecosystem) that provides links to the repositories
3. Ask in the `#help-contributing` channel

## Contributing to documentation

### WireMock Website

Most of WireMock's documentation is published on `wiremock.org`,
which is a static website built using Jekyll.
The website sources are located here: [wiremock/wiremock.org](https://github.com/wiremock/wiremock.org).
All the documentation is located under the `_docs` directory as Markdown files,
and it can be edited with all modern text editors and IDEs.

You can extend or modify documentation by submitting a pull request against the repository.
To do so, you can either fork and clone the repository and do edits in your branch,
or just use GitHub's web interface for small patches.

### Tutorials and Guides

We are happy to include new WireMock tutorials and to publish them from our resources:
websites, GitHub org, and YouTube videos.
We will be also happy to reference and repost tutorials published on the different platforms.

> **NOTE:** We are currently working on the new structure for Tutorials and Quick Start guides on the website.
> If you are intersted to write one, please join the `#help-contributing` channel and let us know there.

### Built-in docs

Some documentation is generated from code, for example Javadoc
This documentation can be (and should be) edited along with code so that it could be published later to the websites.

- [Unofficial Javadoc site](https://javadoc.io/doc/com.github.tomakehurst/wiremock).
  See [wiremock/wiremock.org #32](https://github.com/wiremock/wiremock.org/issues/32) for hosting an official Javadoc site.

Note that the [WireMock Admin REST API specification]((https://wiremock.org/docs/api/)) is currently stored under the 
website repository ([repo](https://github.com/wiremock/wiremock.org/tree/main/swagger)),
and hence should be updated in subsequent pull requests.

### Other documentation

WireMock components and repositories might have their own documentation,
for example `README.md` files in the repository roots.
These are also valuable pieces of documentation, and contributions are welcome!
Please consult with repository contributing guidelines.

## Code contributions

### Before opening a PR

When proposing new features or enhancements, we strongly recommend opening an issue first so that the problem being solved
and the implementation design can be discussed. This helps to avoid time being invested in code that is never eventually
merged, and also promotes better designs by involving the community more widely.

For straightforward bug fixes where the issue is clear and can be illustrated via a failing unit or acceptance test, please
just open a PR.

### Code style

_WireMock Java_ uses the [Google Java style guide](https://google.github.io/styleguide/javaguide.html) and this is enforced in
the build via the Gradle [Spotless plugin](https://github.com/diffplug/spotless).
Other repositories might have different code styles defined by the language standards or their maintainers.

For _WireMock Java_, When running pre-commit checks, if there are any formatting failures the Spotless plugin can fix them for you:

```bash
./gradlew spotlessApply
```

There's also an [IntelliJ plugin](https://plugins.jetbrains.com/plugin/8527-google-java-format) for the same purpose.

### Test coverage is expected

_WireMock Java_ and other implementations have a fairly comprehensive test suite which
ensures it remains robust and correct as the codebase evolves.
In particular, there are acceptance tests for almost all features,
where a full WireMock server is started up and tested via its public APIs.

New features should by default come with acceptance tests covering the major positive and negative cases.
Unit tests should also be used judiciously where non-trivial logic would benefit from finer-grained checking.

When making performance enhancements a representative benchmark test should be developed using an appropriate tool, and
the results before and after applying the change attached to the associated PR.

### Documentation is expected

WireMock is built for developers by developers,
and it is our own interest to ensure the project and the tools we provide
have good documentation.

For newly introduced features,
it is expected that documentation is created before releasing the feature.
When the documentation is located within the same repository,
it should be updated as a part of the pull request.
Otherwise, for example for the `wiremock.org` documentation patches,
it is recommended to create a downstream pull request
so that the feature and the docs could be reviewed at the same time.

- [Website Sources on GitHub](https://github.com/wiremock/wiremock.org)
- [OpenAPI Specification sources](https://github.com/wiremock/wiremock.org/tree/main/swagger)

## Help to spread the word

As any open source project, we need to promote ourselves to remain relevant
and to attract more users and contributors.

- Follow us on social media and help to promote content.
  See the links [here](https://github.com/wiremock/community).
- Write about WireMock in your blog or social media accounts.
  Use the `#wiremock` hashtag where possible,
  and let us know about new publications on Slack (`#general` channel)
- Speak about WireMock and its applications at conferences, podcasts, online and local meetups.

If you would like to present or write something about WireMock and need help,
let us know in the `#community-management` channel.
We also plan to organize our own webinars and distribute swag to the most active contributors,
stay tuned!

## Community building

The open source community around WireMock keeps growing,
and we invite those people who are interested in community building, program management, and mentoring.
We have a list of the current and upcoming community initiatives on the [community dashboard](https://github.com/wiremock/community).
Feedback and ideas are always welcome!

If you are interested, join the `#community-management` channel on Slack.
