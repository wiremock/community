# WireMock Community Governance

This document describes governance principles of the WireMock community.
This governance structure is expected to evolve
over time while the community grows.
In particular, technical steering and governance board entities are considered.

## Roles and definitions

### Community Member

All individuals or organizations somehow interacting with WireMock
and its community resources are considered community members.
It includes but not limited to all WireMock users and contributors,
all members of the [WireMock Community Slack](http://slack.wiremock.org/),
etc.

### Contributors

Any WireMock community member, individual or organization,
actively participating in the community and
doing substantial contributions there.
Contributions mean anything providing value to the community,
including but not limited to:
any kinds of Git commits, documentation, testing,
speaking and writing about the project,
submitting issues and feedback,
sponsoring contributions and development,
participating in conversations and helping users,
etc.

Contributors participate in decision making,
are eligible and invited to publish their affiliation with the project.
The contributors represent the project within the area of their contributions
though the official representation needs to be confirmed by the _BDFL_.
Should the community-wide elections be introduced in the future,
all contributors will be eligible to register as voters and to
participate in these elections.

Contributor guidelines are documented [here](../contributing/).

### Committers

Sub-group of contributors doing changes in WireMock repositories,
including production code, test and software delivery pipelines,
documentation, artwork, etc.
These changes are done through Git commits, hence the name.
This role is used in some areas like community analytics,
but otherwise it not differentiated from other _Contributors_.

### Component Maintainers (a.k.a. Maintainers)

Individuals who maintain particular components of the WireMock ecosystem.
They have full decision making power within their components,
including promoting contributors to the maintainer status and
defining the criteria for it.

### Core Maintainers

Maintainers of core and mission critical components of WireMock, including
_WireMock Java_, _WireMock Docker_, the website, project infrastructure, etc.
They also manage the community's public roadmap.
Core maintainers are identified and assigned by the _BDFL_.
They might be requested to sign the _Contributor License Agreement_.

Normally core maintainers have administrative access to the
WireMock GitHub organization and other community infrastructure
like social media, distribution repos, accounts, etc.
They can assist _maintainers_ and _contributors_
with providing the necessary access and permissions.

## WireMock [Java] co-maintainer

A subtype of the core maintainer specifically for the WireMock Core (a.k.a. WireMock Java).
See the [WireMock Contributor Guide](https://github.com/wiremock/wiremock/blob/master/CONTRIBUTING.md)

### Community Managers

A subtype of the core maintainer.
Community Managers are specifically focused on enabling all contributors and maintainers,
facilitating the roadmap
and growing the community and WireMock adoption.
They act as a point of contact for community members,
and expected to monitor the `#help` and `#help-contributing` channels
and ensure that all community members get necessary assistance.

### BDFL

_Benevolent dictator for life (BDFL)_ -
[Tom Akehurst](https://github.com/tomakehurst), the project founder,
who retains the final say in disputes or arguments within the community
when the consensus cannot be reached
([Wikipedia](https://en.wikipedia.org/wiki/Benevolent_dictator_for_life)).
The BDFL, based on conversations with users and contributors,
defines the technical direction of the project
and also assigns _core maintainers_.

## Decision Making

Community-wide decisions are made by a consensus of _Contributors_.
If this consensus cannot be reached,
the decision can be made by the _BDFL_.

Key discussions and decisions should happen asynchronously in communication channels
like community Slack, GitHub Issues or pull requests.
Note that the community Slack conversation history is limited,
and hence key takeaways should be documented on GitHub.

The decisions are then documented in the respective GitHub issues and the community documentation.

## Public Roadmap

The WireMock community and project have a
[public roadmap](https://github.com/orgs/wiremock/projects/4)
maintained by _Core Maintainers_.
This roadmap is a non-binding list of key initiatives happening
in WireMock,
including major releases and key deliverables for users and community members.

The key purpose of the roadmap is to provide insights about what's going on in the community,
and to facilitate communities,
We make no commitment on delivery dates or on the fact of delivery.
All community members are welcome to contribute to the items listed on the roadmap.

Roadmap items are generally expected to have clear scope and to
provide links to the discussion channels and, ideally, contributing guidelines.

## Code of Conduct

The WireMock community has adopted the Code of Conduct based on the
[Contributor Covenant](https://www.contributor-covenant.org/), version 2.1,
available at [this page](https://www.contributor-covenant.org/version/2/1/code_of_conduct.html).

We as contributors, maintainers and community leaders pledge to
make participation in our community a harassment-free experience for everyone,
regardless of age, body size, visible or invisible disability,
ethnicity, sex characteristics, gender identity and expression,
level of experience, education, socio-economic status,
nationality, personal appearance, race, caste, color, religion, or
sexual identity and orientation.
We pledge to act and interact in ways that contribute to an open, welcoming, diverse, inclusive, and healthy community.

Read the full Code of Conduct and learn more about our standards,
escalation ways and enforcement processes
[here](https://github.com/wiremock/.github/blob/main/CODE_OF_CONDUCT.md).

## Contributor License Agreement

At the moment the project does not requires all _Committers_ to
sign a Contributor License Agreement (CLA),
and does not enforce the [Developer Certificate of Origin (DCO)](https://developercertificate.org/).
It is likely to change in the future.

_Core Maintainer_ and other contributors might be requested to sign the CLA
before being granted access to particular community resources.
The decision on that is made by the _BDFL_.
