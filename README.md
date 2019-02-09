# @seantrane/github-label-presets

> :octocat: GitHub Labels that are logical, colorful and sensible.

[![Build Status](https://travis-ci.com/seantrane/github-label-presets.svg?branch=master)](https://travis-ci.com/seantrane/github-label-presets) [![devDependencies Status](https://david-dm.org/seantrane/github-label-presets/dev-status.svg)](https://david-dm.org/seantrane/github-label-presets?type=dev) [![Greenkeeper badge](https://badges.greenkeeper.io/seantrane/github-label-presets.svg)](https://greenkeeper.io/) [![semantic-release](https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg)](https://github.com/semantic-release/semantic-release)

[![npm latest version](https://img.shields.io/npm/v/@seantrane/github-label-presets/latest.svg)](https://www.npmjs.com/package/@seantrane/github-label-presets) [![npm next version](https://img.shields.io/npm/v/@seantrane/github-label-presets/next.svg)](https://www.npmjs.com/package/@seantrane/github-label-presets) [![npm downloads per week](https://img.shields.io/npm/dw/@seantrane/github-label-presets.svg)](https://www.npmjs.com/package/@seantrane/github-label-presets) [![npm total downloads](https://img.shields.io/npm/dt/@seantrane/github-label-presets.svg)](https://www.npmjs.com/package/@seantrane/github-label-presets)

## About <a id="about"></a>

**TL;DR:** _Want [beautiful GitHub Labels like these](https://github.com/seantrane/github-label-presets/labels)?_ Want to have them unobtrusively synced with your repos? Want to persist them indefinitely? Want to maintain your own labels? If the answers have been yes, this is definitely not _too long_, please read on.

1. Run; `npm install -g github-label-sync`
2. Provide env-vars; `GITHUB_ACCESS_TOKEN`, `GITHUB_NAME`, `REPO`
3. Run; `github-label-sync -l 'https://git.io/fAe5i' ${GITHUB_NAME}/${REPO}`

### Details

The default GitHub Labels are, well... not ideal. This has been described many times:

- [Sane GitHub Labels](https://medium.com/@dave_lunny/sane-github-labels-c5d2e6004b63)
- [How we organize GitHub issues: A simple styleguide for tagging](https://robinpowered.com/blog/best-practice-system-for-organizing-and-tagging-github-issues/)

There are many very good examples of GitHub Label strategies. Almost all of them are an improvement over the default. But for several reasons or another few, in practice, none of them have felt truly great or sustainable.

#### Principles

`@seantrane/github-label-presets` were designed according to the following thoughts and principles:

- GitHub Labels are used for both Issues and Pull Requests (PR), therefore the label context should be agnostic.
- An Issue/PR without labels should not require labels to solicit attention, therefore the default state should be label-less.
- Issue/PR labels should only provide important context; priority, effort and the state of solution and/or decision-making.
- _"High Priority"_, sure, but _"Low Priority"_ is a joke; go label-less instead.
- Labels and their associated colors should have a logical connection that is intuitive at-a-glance.
- Labels should be lowercase. It's easier to type and less competitive with Label-names.
- Prefixes matter. Labels get chaotic without them. The chosen are;
  - `effort` = relative effort involved, fibonacci from `1` to `13`
  - `priority` = designate immediacy; `now`, `2day` or `soon`
  - `state` = describe decision; `approved`, `blocked`, `inactive` or `pending`
  - `type` = describe type; `bug`, `chore`, `discussion`, `docs`, `feature`, `fix`, `security`, `testing`
  - `work` = describe situation; `chaotic`, `complex`, `complicated` or `obvious`
- The only labels without prefixes are; `breaking`, `good first issue`, `greenkeeper`, `help` and `semantic-release`

#### Label Groups

| Standard | Effort | Priority | State | Type | Work |
| -------- | ------ | -------- | ----- | ---- | ---- |
| Standard labels commonly used in most repositories. | Describes the relative effort to complete an issue or pull request. | Priority labels, but focused on describing the immediacy of attention required. | Describes the _decision_ state of the issue or pull request. | Describes the _type_ of issue or pull request. | Describes the kind of work involved in resolving the issue, using the [Cynefin framework](https://en.wikipedia.org/wiki/Cynefin_framework). |
| ![Standard Labels](https://github.com/seantrane/github-label-presets/raw/master/docs/images/github-labels-standard.png) | ![Effort Labels](https://github.com/seantrane/github-label-presets/raw/master/docs/images/github-labels-effort.png) | ![Priority Labels](https://github.com/seantrane/github-label-presets/raw/master/docs/images/github-labels-priority.png) | ![State Labels](https://github.com/seantrane/github-label-presets/raw/master/docs/images/github-labels-state.png) | ![Type Labels](https://github.com/seantrane/github-label-presets/raw/master/docs/images/github-labels-type.png) | ![Work Labels](https://github.com/seantrane/github-label-presets/raw/master/docs/images/github-labels-work.png) |

#### How It Works

- [`github-label-sync`](https://github.com/Financial-Times/github-label-sync) is used to _synchronize your GitHub labels with as few destructive operations as possible - similar labels get renamed_.
- The [label config](https://github.com/Financial-Times/github-label-sync#label-json) is loaded via path or URL, or more specifically; the config file supplied by [`@seantrane/github-label-presets`](https://github.com/seantrane/github-label-presets).
- The `github-label-sync -l 'https://git.io/fAe5i' ${GITHUB_NAME}/${REPO}` command is run to have the label config applied to _your_ `profile/repo`.
- The command can be run anywhere and anytime, but it's recommended during a CI plan. This will automatically keep your labels clean and synchronized with your chosen configuration - depending on how often your plan is run, of course.

## Usage <a id="usage"></a>

**Required:** [Generate a GitHub Access Token](https://github.com/settings/tokens), provide it via `GITHUB_ACCESS_TOKEN` environment variable. _If you cannot provide token as env-var, you may also pass it via CLI._

1. Install `npm install -g github-label-sync`
2. Dry-run `github-label-sync -d -l 'https://git.io/fAe5i' <github_name>/<github_repo>`
3. Run `github-label-sync -l 'https://git.io/fAe5i' <github_name>/<github_repo>`
4. _optional:_ provide token via param; `github-label-sync -a <github_token> -l ...`

### CI/CD

You can use your CI/CD process to automate the periodic syncing of your repository labels. This can help persist order automatically.

#### Travis CI

Make sure `GITHUB_ACCESS_TOKEN` env-var is available.

```yaml
before_install: npm install -g github-label-sync
script: github-label-sync -d -l 'https://git.io/fAe5i' <github_name>/<github_repo>
deploy:
  provider: script
  script: github-label-sync -l 'https://git.io/fAe5i' <github_name>/<github_repo>
```

### Config your own...

You can provide your own `labels.json` via the `[ -l, --lables ]` argument.

## Contribute <a id="contribute"></a>

Contributions are always appreciated. Read [CONTRIBUTING.md](https://github.com/seantrane/github-label-presets/blob/master/CONTRIBUTING.md) documentation to learn more.

## Changelog <a id="changelog"></a>

Release details are documented in the [CHANGELOG.md](https://github.com/seantrane/github-label-presets/blob/master/CHANGELOG.md) file, and on the [GitHub Releases page](https://github.com/seantrane/github-label-presets/releases).

---

## License <a id="license"></a>

[ISC License](https://github.com/seantrane/github-label-presets/blob/master/LICENSE)

Copyright (c) 2018 [Sean Trane Sciarrone](https://github.com/seantrane)
