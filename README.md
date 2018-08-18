# @seantrane/github-label-presets

> :octocat: GitHub Labels that are logical, colorful and sensible.

[![Build Status](https://travis-ci.com/seantrane/github-label-presets.svg?branch=master)](https://travis-ci.com/seantrane/github-label-presets) [![devDependencies Status](https://david-dm.org/seantrane/github-label-presets/dev-status.svg)](https://david-dm.org/seantrane/github-label-presets?type=dev) [![Greenkeeper badge](https://badges.greenkeeper.io/seantrane/github-label-presets.svg)](https://greenkeeper.io/) [![semantic-release](https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg)](https://github.com/semantic-release/semantic-release)

[![npm latest version](https://img.shields.io/npm/v/@seantrane/github-label-presets/latest.svg)](https://www.npmjs.com/package/@seantrane/github-label-presets) [![npm next version](https://img.shields.io/npm/v/@seantrane/github-label-presets/next.svg)](https://www.npmjs.com/package/@seantrane/github-label-presets) [![npm downloads per week](https://img.shields.io/npm/dw/@seantrane/github-label-presets.svg)](https://www.npmjs.com/package/@seantrane/github-label-presets) [![npm total downloads](https://img.shields.io/npm/dt/@seantrane/github-label-presets.svg)](https://www.npmjs.com/package/@seantrane/github-label-presets)

## About <a id="about"></a>

**TL;DR:** _Want [beautiful GitHub Labels like these](https://github.com/seantrane/github-label-presets/labels)?_ Want to have them unobtrusively synced with your repos? Want to persist them indefinitely? Want to maintain your own labels? If the answers have been yes, this is definitely not _too long_, please read on.

**TL;DR:2** Really? Still _too long_? From your repo directory, run; `npm install -g @azu/github-label-setup && github-label-setup --token <gh_token> -l @seantrane/github-label-presets`

### Details

The default GitHub Labels are, well... not ideal. This has been described many times:

- [Sane GitHub Labels](https://medium.com/@dave_lunny/sane-github-labels-c5d2e6004b63)
- [How we organize GitHub issues: A simple styleguide for tagging](https://robinpowered.com/blog/best-practice-system-for-organizing-and-tagging-github-issues/)

There are many very good examples of GitHub Label strategies. Almost all of them are an improvement over the default. But for several reasons or another few, in practice, none of them have felt truly great or sustainable.

`@seantrane/github-label-presets` were designed according to the following thoughts and principles:

- GitHub Labels are used for both Issues and Pull Requests (PR), therefore the label context should be agnostic.
- An Issue/PR without labels should not require labels to solicit attention, therefore the default state is label-less.
- A glance at an Issue/PR with labels should provide; priority, effort and the state of solution and/or decision-making.
- _"High Priority"_, sure, but _"Low Priority"_ is a joke; go label-less.
- Labels and their associated colors should have a logical connection that is intuitive at-a-glance.
- Labels should be lowercase; easier to type, less competitive with Label-names.
- Prefixes matter. Labels get chaotic without them. The chosen are;
  - `effort` = relative effort involved, fibonacci from `1` to `13`
  - `priority` = designate immediacy; `now`, `2day` or `soon`
  - `state` = describe decision; `approved`, `blocked`, `inactive` or `pending`
  - `type` = describe type; `bug`, `chore`, `discussion`, `docs`, `feature`, `fix`, `security`, `testing`
  - `work` = describe situation; `chaotic`, `complex`, `complicated` or `obvious`
- The only labels without prefixes are; `breaking`, `good first issue`, `greenkeeper`, `help`, `stale` and `semantic-release`

The _GitHub Label presets_ are meant to be used with one of two packages:

- [github-label-sync](https://github.com/Financial-Times/github-label-sync)
  - _Synchronise your GitHub labels with as few destructive operations as possible - similar labels get renamed._
  - Load [label config](https://github.com/Financial-Times/github-label-sync#label-json) via path or URL.
  - Run on specified repo via CLI parameter.
- [@azu/github-label-setup](https://github.com/azu/github-label-setup) _(a wrapper of `github-label-sync`)_
  - _Opinionated GitHub label setup tool._
  - Works without config, using [default opinionated labels](https://github.com/azu/github-label-setup#default-labels).
  - Load [label config](https://github.com/Financial-Times/github-label-sync#label-json) via path, URL or [npm package](https://github.com/azu/github-label-setup#npm-packages-for-labels).

## Usage <a id="usage"></a>

**Required:** [Generate a GitHub Access Token](https://github.com/settings/tokens), provide it via `GITHUB_ACCESS_TOKEN` environment variable. _If you cannot provide token as env-var, you may also pass it via CLI._

### via `github-label-sync` <a id="usage-github-label-sync"></a>

1. Install `npm install -g github-label-sync`
2. Dry-run `github-label-sync -l https://github.com/seantrane/github-label-presets/blob/master/labels.json  <github_name>/<github_repo>`
3. Run `github-label-sync -l https://github.com/seantrane/github-label-presets/blob/master/labels.json  <github_name>/<github_repo>`
4. _optional:_ provide token via param; `github-label-sync -a <gh_token> -l ...`

### via `@azu/github-label-setup` <a id="usage-github-label-setup"></a>

1. Run `npm install -g @azu/github-label-setup`
2. Go to your git-initiated project repository.
3. Dry-run `github-label-setup -d -l @seantrane/github-label-presets`
4. Run `github-label-setup -l @seantrane/github-label-presets`
5. _optional:_ provide token via param; `github-label-setup --token <gh_token> -l ...`

### CI/CD

You can use your CI/CD process to automate the periodic syncing of your repository labels. This can help persist order automatically.

### Config your own...

You can provide your own `labels.json`, to either tool, via the `[ -l, --lables ]` argument.

## Contribute <a id="contribute"></a>

Contributions are always appreciated. Read [CONTRIBUTING.md](https://github.com/seantrane/balanced-theme-for-atom/blob/master/CONTRIBUTING.md) documentation to learn more.

## Changelog <a id="changelog"></a>

Release details are documented in the [CHANGELOG.md](https://github.com/seantrane/balanced-theme-for-atom/blob/master/CHANGELOG.md) file, and on the [GitHub Releases page](https://github.com/seantrane/balanced-theme-for-atom/releases).

---

## License <a id="license"></a>

MIT License

Copyright (c) 2018 Sean Trane Sciarrone

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NON-INFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
