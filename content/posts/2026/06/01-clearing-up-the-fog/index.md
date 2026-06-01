+++
date = '2026-06-01T22:17:46+07:00'
draft = false
title = 'Clearing Up the Fog'
authors = ["malfisya", "silkeh"]
tags = [
    "linux",
    "solus",
]
+++
![](clearing-up-the-fog-banner.jpg "Morning fog at some trees by Keravanjoki river in Vantaa, Finland")

Hello everyone! We want to talk about our licensing situation and our plan regarding it. Let's dive in!

## What licensing situation?

If you don't know, Solus started its life as [Evolve OS](/2013/12/13/coming-soon/). Due to a [trademark dispute](/2015/04/12/whats-in-a-name/), the name was then changed to Solus. More than 10 years passed, and Solus is still here. During its life, the development of Solus and its related projects has happened in various places. They have included IRC, Matrix, Github, and Phabricator, to name a few. 

One of the most vital parts that make Solus the distribution you love is our package recipes, `package.yml`. First, it lived at GitHub under the Evolve OS organization, and then under Solus Project. Then, we moved our development to a self-hosted instance of Phabricator (`dev.getsol.us`). [When the development restarted in 2023](/2023/04/18/a-new-voyage/), it was decided to move back to GitHub again under a new GetSolus organization. During these migrations, there were some pieces that got left behind unintentionally. Most notably, the license files for our package recipes. 

In the Evolve OS and Solus Project days, all those `package.yml` files lived in one repository (monorepo) which included its license file. At that time, the packages repository was licensed under [GNU General Public License Version 2 (GPL-2.0-or-later)](https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html#SEC1). When the migration to Phabricator took place, each package recipe was split into its own repository. However, the license file wasn’t carried over with those recipes. Now that we are back on GitHub and using monorepo again, our [getsolus/packages](https://github.com/getsolus/packages) repository no longer includes a license. That is a problem.

## What kind of problem ?

### It creates ambiguity

The ambiguity came from whether or not our packages recipes are actually open-source. A software license is what distinguishes open-source from closed-source software. Typically, an open-source project will use one (or more) [OSI Approved Licenses](https://opensource.org/licenses). While our package repository is publicly accessible, it doesn't include a license file, which brings confusion as to whether the code is free to use or not.

### It creates a confusing contributor environment

One of the beauties of open-source is allowing people to explore, modify, and contribute back to the code. As such, we are always grateful and encouraged that people contribute to Solus. However, our current situation introduces uncertainty about whether contributed code has been properly licensed.

In most open-source projects, contributors implicitly agree to license their contributions under the same license as the rest of the project. For example, if people contributed lines of code to a project licensed under GPL-2.0-or-later, they implicitly agree to the license stipulated. Some projects go further by enforcing a [Contributor License Agreement (CLA)](https://en.wikipedia.org/wiki/Contributor_license_agreement) to explicitly define contributors’ rights and obligations.

Since we don't enforce a CLA, and our packages repository lacked a license during a certain period, contributions in that timeframe fall into a legal grey area.

### It hinders knowledge sharing

As you may be already aware, we plan to adopt [AerynOS](https://aerynos.com/) tooling in the future. We already use [`ent`](https://github.com/AerynOS/ent/) and [`boulder`](https://aerynos.com/tooling/boulder/) in limited scope within our packaging infrastructure. We will also convert our `package.yml` into AerynOS package recipe format gradually.

When that transition happens, we want to be able to share our package recipes with AerynOS, as well as benefit from theirs. However, if the current licensing situation remains unresolved, it will block us from doing so.

## Okay, it is a problem. Do you have a plan?

Yes, we do. Despite this not being a great situation to be in, it also presents an opportunity. Since we need to clear up the licensing situation anyway, we can take this chance to chose a license that better fits our goals. 

As a result, we plan to relicense our packages repository under the [Mozilla Public License, version 2.0 (MPL-2.0)](https://www.mozilla.org/en-US/MPL/2.0/). We chose this license because it strikes a good balance between so-called 'copyleft' protections, and permissability, and it allows us to share code between Solus and AerynOS. Specifically, the `MPL-2.0`:

- Ensures that Solus is, and will always be, free and open source.
- Requires any modifications to be done under the same license, keeping it free and open source even if not developed by Solus.
- Offers enough freedom to not be restricted by it, especially in the current mixed-license situation.
- Explicitly allows mixing the license with the GPL, which still applies to older contributions to Solus.
- Is also used by AerynOS, which makes it easy to exchange work between Solus and AerynOS.

More details about the license can be found by reading [the license itself](https://www.mozilla.org/en-US/MPL/2.0/) or the [frequently asked questions](https://www.mozilla.org/en-US/MPL/2.0/FAQ/) about the license.

That doesn't mean we can just apply the license to the package repository: we need contributors to explicitly agree to it and help us to make that change, which can be done in the following ways:

- By commenting on [this GitHub issue](https://github.com/getsolus/packages/issues/7815), which also details the rest of the plan.
- By consenting to the change in the next contribution to the packages repository.
- By replying to an email that we will send in the future.
  
## Should I do anything?

- For contributors: You can consent to the license change by the methods mentioned above. We need your consent for this change to happen.
- For regular users and non-contributors: You **don't** have to do anything. This project doesn't affect your daily use of Solus.

## Conclusion
In short, we want to clear up the “fog” around the licensing situation that surfaced through our migrations so everything is unambiguous going forward. Relicensing under MPL-2.0 gives us that clarity. It ensures that our work remains open, contributions are properly defined, and collaboration can happen with confidence.

If you have contributed in the past, we appreciate your work and your patience as we resolve this. And if you are considering contributing, we hope this change makes it easier to do so with certainty. With new license in place, we’ve got a clear path forward for contributions and collaboration. 

That is all from us. Hope you all have a good day. Cheers!

## Support us!

Solus is a volunteer-run project, and we rely on donations from the community to keep the lights on. We understand that donating money can be tough, especially in these challenging times. As such, we are very grateful to everyone who contributes financially to the project. If you would like to support our work, please consider donating to our [OpenCollective](https://opencollective.com/getsolus).

<sub>*This article was first published as [blog](https://getsol.us/2026/05/clearing-up-the-fog/) on Solus website at 11-05-2026*</sub>
