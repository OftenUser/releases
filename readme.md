> **Warning**
>
> This repository is now _deprecated_ and the npm package will no longer be updated. If you want to access a full list of all Electron releases, please refer to https://releases.electronjs.org/releases.json instead.

# electron-releases

![Test](https://github.com/electron/releases/workflows/Test/badge.svg)

> Complete and up-to-date info about every release of Electron.

This package:

- Includes all [GitHub Releases](https://developer.github.com/v3/repos/releases/#get-a-single-release) data about Electron.
- Does not include draft releases.
- Includes prereleases which are not published to npm.
- Tracks which versions are published to npm.
- Tracks [npm dist-tags](https://docs.npmjs.com/cli/dist-tag) like `latest` and `beta`.
- Includes V8, Chromium, and Node.js version data.
- Includes [GitHub-flavored HTML](https://ghub.io/hubdown) for each release's changelog.
- Ignores npm versions from the days before [Electron was `electron`](https://electronjs.org/blog/npm-install-electron).
- Is [updated regularly](#updates).

## Sources

This module collects metadata from various sources:

- [GitHub Releases of `electron/electron`](https://github.com/electron/electron)
- [dist-tags from npm registry for `electron`](https://registry.npmjs.com/electron)
- [dist-tags from npm registry `electron-prebuilt`](https://registry.npmjs.com/electron-prebuilt)
- [Dependency data for Chromium, Node.js, V8, etc](https://atom.io/download/electron/index.json)

## Installation

```sh
npm i electron-releases
```

## Usage

The module exports an array of release objects:

```js
const releases = require('electron-releases')

// find newest version:
releases[0].tag_name // => 'v1.8.2-beta.3'

// find `latest` on npm, which is not necessarily the most recent release:
releases.find(release => release.npm_dist_tag === 'latest')

// find `beta` on npm:
releases.find(release => release.npm_dist_tag === 'beta')
```

### Lite Version

The default export is about 75MB, as it includes a lot of metadata from the
GitHub API like release assets.

If you just need the basic info like version numbers, npm dist tags, and publish dates, there's a much smaller (< 500K) dataset you can use:

```js
require('electron-releases/lite.json')
```

You can also get this at [unpkg.com/electron-releases/lite.json](https://unpkg.com/electron-releases/lite.json)

### Data

Each release contains all the data returned by the
[GitHub Releases API](https://docs.github.com/en/free-pro-team@latest/rest/reference/repos#releases),
plus some extra properties:

- `version` (String) - the same thing as `dist_tag`, but without the `v` for convenient [semver comparisons](https://github.com/npm/node-semver#usage).
- `npm_dist_tags` (Array<String>) - an array of [npm dist-tags](https://docs.npmjs.com/cli/dist-tag) like `"latest"` or `"beta"`. Most releases will have an empty array for this property.
- `npm_package_name` (String) - For packages published to npm, this will be `electron` or `electron-prebuilt`. For packages not published to npm, this property will not exist.
- `total_downloads` (Number) - Total downloads of all assets in the release that
  have a [detectable platform](https://github.com/zeke/platform-utils#api) in their
  filename like `.zip`, `.dmg`, `.exe`, `.rpm`, `.deb`, etc.
- `deps` (Object) - version numbers for Electron dependencies.
  - `v8` (String)
  - `chromium` (String)
  - `node` (String)
  - etc..

## Updates

This module is self-publishing. It runs in a GitHub Action cron job every
six hours. A new version of this module is published if any of
the following change:

- number of Electron releases on GitHub
- number of Electron releases on npm
- npm `electron@beta` version
- npm `electron@latest` version

If none of these has changed, the build process aborts and runs again ten minutes
later. For more detail, see [script/release.sh](script/release.sh)

The Heroku app is also synced to the GitHub repo, so every push to the
`master` branch will automatically deploy a new version of this app.

### Manually update

If you need to modify any file in the `script` folder, you'll also want
to manually regenerate this module's output files. You can do so with
the following steps:

1. Create a [personal access token](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/#creating-a-token). Note that if Electron maintainers must enable SSO
for the `electron` org for this token to work.
1. Copy the `.env.example` file into a separate `.env` file.
    ```sh
    cp .env.example .env
    ```
1. Paste your token into the `GH_TOKEN` field of the `.env` file.
1. Build the module.
    ```sh
    npm run build
    ```
1. Check if all tests passed:
    ```sh
    npm test
    ```

## Tests

```sh
npm install
npm test
```

## License

MIT

## Releases

<!-- START RELEASES TABLE -->
|Tag|Published|npm|Prerelease|Module Version|Node|Chrome|Downloads|
|----|----|----|----|----|----|----|----|
|[v24.0.0-nightly.20221216](https://github.com/electron/electron/releases/tag/v24.0.0-nightly.20221216)|December 16, 2022|nightly|yes|114|18.12.1|110.0.5451.0|529|
|[v24.0.0-nightly.20221215](https://github.com/electron/electron/releases/tag/v24.0.0-nightly.20221215)|December 15, 2022||yes|114|18.12.1|110.0.5451.0|238|
|[v24.0.0-nightly.20221214](https://github.com/electron/electron/releases/tag/v24.0.0-nightly.20221214)|December 14, 2022||yes|114|18.12.1|110.0.5451.0|168|
|[v24.0.0-nightly.20221213](https://github.com/electron/electron/releases/tag/v24.0.0-nightly.20221213)|December 13, 2022||yes|114|18.12.1|110.0.5451.0|248|
|[v24.0.0-nightly.20221208](https://github.com/electron/electron/releases/tag/v24.0.0-nightly.20221208)|December 8, 2022||yes|114|18.12.1|110.0.5451.0|332|
|[v24.0.0-nightly.20221207](https://github.com/electron/electron/releases/tag/v24.0.0-nightly.20221207)|December 7, 2022||yes|114|18.12.1|110.0.5451.0|169|
|[v24.0.0-nightly.20221206](https://github.com/electron/electron/releases/tag/v24.0.0-nightly.20221206)|December 6, 2022||yes|114|18.12.1|110.0.5451.0|309|
|[v24.0.0-nightly.20221205](https://github.com/electron/electron/releases/tag/v24.0.0-nightly.20221205)|December 5, 2022||yes|114|18.12.1|110.0.5415.0|259|
|[v24.0.0-nightly.20221202](https://github.com/electron/electron/releases/tag/v24.0.0-nightly.20221202)|December 2, 2022||yes|114|18.12.1|110.0.5415.0|381|
|[v24.0.0-nightly.20221201](https://github.com/electron/electron/releases/tag/v24.0.0-nightly.20221201)|December 1, 2022||yes|114|18.12.1|110.0.5415.0|176|
|[v23.0.0-nightly.20221130](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221130)|November 30, 2022||yes|110|18.12.1|110.0.5415.0|334|
|[v23.0.0-nightly.20221129](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221129)|November 29, 2022||yes|110|18.12.1|110.0.5415.0|309|
|[v23.0.0-nightly.20221128](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221128)|November 28, 2022||yes|110|18.12.1|110.0.5415.0|319|
|[v23.0.0-nightly.20221125](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221125)|November 25, 2022||yes|110|18.12.1|110.0.5415.0|355|
|[v23.0.0-nightly.20221124](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221124)|November 24, 2022||yes|110|18.12.1|110.0.5415.0|322|
|[v23.0.0-nightly.20221123](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221123)|November 23, 2022||yes|110|18.12.1|110.0.5415.0|175|
|[v23.0.0-nightly.20221122](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221122)|November 23, 2022||yes|110|18.12.1|110.0.5415.0|283|
|[v23.0.0-nightly.20221121](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221121)|November 21, 2022||yes|110|18.10.0|110.0.5415.0|173|
|[v23.0.0-nightly.20221118](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221118)|November 19, 2022||yes|110|18.10.0|110.0.5415.0|333|
|[v23.0.0-nightly.20221117](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221117)|November 17, 2022||yes|110|18.10.0|109.0.5382.0|183|
|[v23.0.0-nightly.20221116](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221116)|November 16, 2022||yes|110|18.10.0|109.0.5382.0|315|
|[v23.0.0-nightly.20221115](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221115)|November 15, 2022||yes|110|18.10.0|109.0.5382.0|330|
|[v23.0.0-nightly.20221114](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221114)|November 14, 2022||yes|110|18.10.0|109.0.5382.0|322|
|[v23.0.0-nightly.20221111](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221111)|November 11, 2022||yes|110|18.10.0|109.0.5382.0|376|
|[v23.0.0-nightly.20221110](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221110)|November 10, 2022||yes|110|16.17.1|109.0.5382.0|316|
|[v23.0.0-nightly.20221109](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221109)|November 9, 2022||yes|110|16.17.1|109.0.5382.0|323|
|[v23.0.0-nightly.20221108](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221108)|November 8, 2022||yes|110|16.17.1|109.0.5382.0|311|
|[v23.0.0-nightly.20221107](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221107)|November 7, 2022||yes|110|16.17.1|109.0.5382.0|311|
|[v23.0.0-nightly.20221104](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221104)|November 4, 2022||yes|110|16.17.1|109.0.5382.0|365|
|[v23.0.0-nightly.20221103](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221103)|November 3, 2022||yes|110|16.17.1|109.0.5382.0|184|
|[v23.0.0-nightly.20221102](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221102)|November 2, 2022||yes|110|16.17.1|109.0.5382.0|167|
|[v23.0.0-nightly.20221101](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221101)|November 1, 2022||yes|110|16.17.1|109.0.5382.0|328|
|[v23.0.0-nightly.20221031](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221031)|October 31, 2022||yes|110|16.17.1|109.0.5382.0|386|
|[v23.0.0-nightly.20221028](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221028)|October 28, 2022||yes|110|16.17.1|109.0.5382.0|347|
|[v23.0.0-nightly.20221027](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221027)|October 27, 2022||yes|110|16.17.1|109.0.5382.0|310|
|[v23.0.0-nightly.20221026](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221026)|October 27, 2022||yes|110|16.17.1|108.0.5355.0|271|
|[v23.0.0-nightly.20221024](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221024)|October 24, 2022||yes|110|16.17.1|108.0.5355.0|354|
|[v23.0.0-nightly.20221021](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221021)|October 21, 2022||yes|110|16.17.1|108.0.5355.0|367|
|[v23.0.0-nightly.20221020](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221020)|October 20, 2022||yes|110|16.17.1|108.0.5355.0|325|
|[v23.0.0-nightly.20221019](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221019)|October 19, 2022||yes|110|16.17.1|108.0.5355.0|325|
|[v23.0.0-nightly.20221018](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221018)|October 18, 2022||yes|110|16.17.1|108.0.5355.0|411|
|[v23.0.0-nightly.20221017](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221017)|October 17, 2022||yes|110|16.17.1|108.0.5329.0|334|
|[v23.0.0-nightly.20221014](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221014)|October 14, 2022||yes|110|16.17.1|108.0.5329.0|402|
|[v23.0.0-nightly.20221013](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221013)|October 13, 2022||yes|110|16.17.1|108.0.5329.0|319|
|[v23.0.0-nightly.20221012](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221012)|October 12, 2022||yes|110|16.17.1|108.0.5329.0|327|
|[v23.0.0-nightly.20221011](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221011)|October 11, 2022||yes|110|16.17.1|108.0.5329.0|161|
|[v23.0.0-nightly.20221010](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221010)|October 11, 2022||yes|110|16.17.1|108.0.5329.0|287|
|[v23.0.0-nightly.20221007](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221007)|October 7, 2022||yes|110|16.17.1|108.0.5329.0|399|
|[v23.0.0-nightly.20221006](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221006)|October 6, 2022||yes|110|16.17.1|108.0.5329.0|325|
|[v23.0.0-nightly.20221005](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221005)|October 5, 2022||yes|110|16.17.1|108.0.5329.0|188|
|[v23.0.0-nightly.20221004](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221004)|October 4, 2022||yes|110|16.17.1|108.0.5329.0|327|
|[v23.0.0-nightly.20221003](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20221003)|October 3, 2022||yes|110|16.17.1|107.0.5286.0|192|
|[v23.0.0-nightly.20220930](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20220930)|September 30, 2022||yes|110|16.17.1|107.0.5286.0|384|
|[v23.0.0-nightly.20220929](https://github.com/electron/electron/releases/tag/v23.0.0-nightly.20220929)|September 29, 2022||yes|110|16.17.1|107.0.5286.0|360|
|[v23.0.0-alpha.3](https://github.com/electron/electron/releases/tag/v23.0.0-alpha.3)|December 14, 2022|alpha, alpha-23-x-y|yes|113|18.12.1|110.0.5451.0|2206|
|[v23.0.0-alpha.2](https://github.com/electron/electron/releases/tag/v23.0.0-alpha.2)|December 8, 2022||yes|113|18.12.1|110.0.5451.0|1232|
|[v23.0.0-alpha.1](https://github.com/electron/electron/releases/tag/v23.0.0-alpha.1)|December 6, 2022||yes|113|18.12.1|110.0.5415.0|1363|
|[v22.0.0](https://github.com/electron/electron/releases/tag/v22.0.0)|November 30, 2022|latest, 22-x-y|no|110|16.17.1|108.0.5359.62|204682|
|[v22.0.0-nightly.20220928](https://github.com/electron/electron/releases/tag/v22.0.0-nightly.20220928)|2022-09-28||yes|110|16.17.1|107.0.5286.0|197|
|[v22.0.0-nightly.20220927](https://github.com/electron/electron/releases/tag/v22.0.0-nightly.20220927)|2022-09-27||yes|110|16.17.1|107.0.5286.0|325|
|[v22.0.0-nightly.20220926](https://github.com/electron/electron/releases/tag/v22.0.0-nightly.20220926)|2022-09-26||yes|110|16.17.1|107.0.5286.0|330|
|[v22.0.0-nightly.20220923](https://github.com/electron/electron/releases/tag/v22.0.0-nightly.20220923)|2022-09-23||yes|109|16.17.0|107.0.5286.0|388|
|[v22.0.0-nightly.20220922](https://github.com/electron/electron/releases/tag/v22.0.0-nightly.20220922)|September 22, 2022||yes|109|16.17.0|107.0.5286.0|319|
|[v22.0.0-nightly.20220921](https://github.com/electron/electron/releases/tag/v22.0.0-nightly.20220921)|September 21, 2022||yes|109|16.17.0|107.0.5286.0|331|
|[v22.0.0-nightly.20220920](https://github.com/electron/electron/releases/tag/v22.0.0-nightly.20220920)|September 20, 2022||yes|109|16.17.0|107.0.5286.0|333|
|[v22.0.0-nightly.20220919](https://github.com/electron/electron/releases/tag/v22.0.0-nightly.20220919)|2022-09-19||yes|109|16.17.0|107.0.5286.0|326|
|[v22.0.0-nightly.20220916](https://github.com/electron/electron/releases/tag/v22.0.0-nightly.20220916)|2022-09-16||yes|109|16.17.0|107.0.5286.0|374|
|[v22.0.0-nightly.20220915](https://github.com/electron/electron/releases/tag/v22.0.0-nightly.20220915)|2022-09-15||yes|109|16.17.0|107.0.5286.0|341|
|[v22.0.0-nightly.20220914](https://github.com/electron/electron/releases/tag/v22.0.0-nightly.20220914)|2022-09-14||yes|109|16.17.0|107.0.5286.0|322|
|[v22.0.0-nightly.20220913](https://github.com/electron/electron/releases/tag/v22.0.0-nightly.20220913)|2022-09-13||yes|109|16.17.0|107.0.5286.0|386|
|[v22.0.0-nightly.20220912](https://github.com/electron/electron/releases/tag/v22.0.0-nightly.20220912)|2022-09-12||yes|109|16.17.0|107.0.5286.0|314|
|[v22.0.0-nightly.20220909](https://github.com/electron/electron/releases/tag/v22.0.0-nightly.20220909)|September 9, 2022||yes|109|16.17.0|107.0.5286.0|384|
|[v22.0.0-nightly.20220908](https://github.com/electron/electron/releases/tag/v22.0.0-nightly.20220908)|September 8, 2022||yes|109|16.17.0|107.0.5274.0|330|
|[v22.0.0-nightly.20220905](https://github.com/electron/electron/releases/tag/v22.0.0-nightly.20220905)|September 5, 2022||yes|109|16.17.0|106.0.5216.0|518|
|[v22.0.0-nightly.20220902](https://github.com/electron/electron/releases/tag/v22.0.0-nightly.20220902)|September 2, 2022||yes|109|16.17.0|106.0.5216.0|365|
|[v22.0.0-nightly.20220901](https://github.com/electron/electron/releases/tag/v22.0.0-nightly.20220901)|September 1, 2022||yes|109|16.17.0|106.0.5216.0|379|
|[v22.0.0-nightly.20220831](https://github.com/electron/electron/releases/tag/v22.0.0-nightly.20220831)|August 31, 2022||yes|109|16.17.0|106.0.5216.0|382|
|[v22.0.0-nightly.20220830](https://github.com/electron/electron/releases/tag/v22.0.0-nightly.20220830)|August 30, 2022||yes|109|16.17.0|106.0.5216.0|321|
|[v22.0.0-nightly.20220829](https://github.com/electron/electron/releases/tag/v22.0.0-nightly.20220829)|2022-08-29||yes|109|16.16.0|106.0.5216.0|320|
|[v22.0.0-nightly.20220825](https://github.com/electron/electron/releases/tag/v22.0.0-nightly.20220825)|2022-08-26||yes|109|16.16.0|106.0.5216.0|360|
|[v22.0.0-nightly.20220824](https://github.com/electron/electron/releases/tag/v22.0.0-nightly.20220824)|2022-08-24||yes|109|16.16.0|106.0.5216.0|343|
|[v22.0.0-nightly.20220823](https://github.com/electron/electron/releases/tag/v22.0.0-nightly.20220823)|2022-08-23||yes|109|16.16.0|106.0.5216.0|305|
|[v22.0.0-nightly.20220822](https://github.com/electron/electron/releases/tag/v22.0.0-nightly.20220822)|August 22, 2022||yes|109|16.16.0|106.0.5216.0|315|
|[v22.0.0-nightly.20220817](https://github.com/electron/electron/releases/tag/v22.0.0-nightly.20220817)|August 17, 2022||yes|109|16.16.0|105.0.5187.0|417|
|[v22.0.0-nightly.20220816](https://github.com/electron/electron/releases/tag/v22.0.0-nightly.20220816)|2022-08-16||yes|109|16.16.0|105.0.5187.0|323|
|[v22.0.0-nightly.20220815](https://github.com/electron/electron/releases/tag/v22.0.0-nightly.20220815)|2022-08-15||yes|109|16.16.0|105.0.5187.0|317|
|[v22.0.0-nightly.20220812](https://github.com/electron/electron/releases/tag/v22.0.0-nightly.20220812)|2022-08-12||yes|109|16.16.0|105.0.5187.0|423|
|[v22.0.0-nightly.20220811](https://github.com/electron/electron/releases/tag/v22.0.0-nightly.20220811)|2022-08-11||yes|109|16.16.0|105.0.5187.0|366|
|[v22.0.0-nightly.20220810](https://github.com/electron/electron/releases/tag/v22.0.0-nightly.20220810)|2022-08-10||yes|109|16.16.0|105.0.5187.0|363|
|[v22.0.0-nightly.20220809](https://github.com/electron/electron/releases/tag/v22.0.0-nightly.20220809)|2022-08-09||yes|109|16.16.0|105.0.5187.0|185|
|[v22.0.0-nightly.20220808](https://github.com/electron/electron/releases/tag/v22.0.0-nightly.20220808)|August 8, 2022||yes|109|16.16.0|105.0.5187.0|361|
|[v22.0.0-beta.8](https://github.com/electron/electron/releases/tag/v22.0.0-beta.8)|November 24, 2022|beta, beta-22-x-y|yes|110|16.17.1|108.0.5359.48|3308|
|[v22.0.0-beta.7](https://github.com/electron/electron/releases/tag/v22.0.0-beta.7)|November 21, 2022||yes|110|16.17.1|108.0.5359.48|1643|
|[v22.0.0-beta.6](https://github.com/electron/electron/releases/tag/v22.0.0-beta.6)|November 18, 2022||yes|110|16.17.1|108.0.5359.40|2751|
|[v22.0.0-beta.5](https://github.com/electron/electron/releases/tag/v22.0.0-beta.5)|November 11, 2022||yes|110|16.17.1|108.0.5359.40|3096|
|[v22.0.0-beta.4](https://github.com/electron/electron/releases/tag/v22.0.0-beta.4)|November 9, 2022||yes|110|16.17.1|108.0.5359.29|4281|
|[v22.0.0-beta.3](https://github.com/electron/electron/releases/tag/v22.0.0-beta.3)|October 31, 2022||yes|110|16.17.1|108.0.5359.10|4308|
|[v22.0.0-beta.2](https://github.com/electron/electron/releases/tag/v22.0.0-beta.2)|October 28, 2022||yes|110|16.17.1|108.0.5359.10|3518|
|[v22.0.0-beta.1](https://github.com/electron/electron/releases/tag/v22.0.0-beta.1)|October 25, 2022||yes|110|16.17.1|108.0.5359.10|2416|
|[v22.0.0-alpha.8](https://github.com/electron/electron/releases/tag/v22.0.0-alpha.8)|October 24, 2022|alpha-22-x-y|yes|110|16.17.1|108.0.5359.10|1581|
|[v22.0.0-alpha.7](https://github.com/electron/electron/releases/tag/v22.0.0-alpha.7)|October 20, 2022||yes|110|16.17.1|108.0.5355.0|1873|
|[v22.0.0-alpha.6](https://github.com/electron/electron/releases/tag/v22.0.0-alpha.6)|October 17, 2022||yes|110|16.17.1|108.0.5329.0|2077|
|[v22.0.0-alpha.5](https://github.com/electron/electron/releases/tag/v22.0.0-alpha.5)|October 13, 2022||yes|110|16.17.1|108.0.5329.0|1986|
|[v22.0.0-alpha.4](https://github.com/electron/electron/releases/tag/v22.0.0-alpha.4)|October 11, 2022||yes|110|16.17.1|108.0.5329.0|1940|
|[v22.0.0-alpha.3](https://github.com/electron/electron/releases/tag/v22.0.0-alpha.3)|October 6, 2022||yes|110|16.17.1|108.0.5329.0|2252|
|[v22.0.0-alpha.1](https://github.com/electron/electron/releases/tag/v22.0.0-alpha.1)|September 28, 2022||yes|110|16.17.1|107.0.5286.0|3276|
|[v21.3.3](https://github.com/electron/electron/releases/tag/v21.3.3)|December 1, 2022|21-x-y|no|109|16.16.0|106.0.5249.199|69142|
|[v21.3.1](https://github.com/electron/electron/releases/tag/v21.3.1)|November 23, 2022||no|109|16.16.0|106.0.5249.181|85195|
|[v21.3.0](https://github.com/electron/electron/releases/tag/v21.3.0)|November 17, 2022||no|109|16.16.0|106.0.5249.181|135388|
|[v21.2.3](https://github.com/electron/electron/releases/tag/v21.2.3)|November 9, 2022||no|109|16.16.0|106.0.5249.168|93137|
|[v21.2.2](https://github.com/electron/electron/releases/tag/v21.2.2)|November 2, 2022||no|109|16.16.0|106.0.5249.168|105007|
|[v21.2.1](https://github.com/electron/electron/releases/tag/v21.2.1)|October 31, 2022||no|109|16.16.0|106.0.5249.165|47855|
|[v21.2.0](https://github.com/electron/electron/releases/tag/v21.2.0)|October 19, 2022||no|109|16.16.0|106.0.5249.119|123382|
|[v21.1.1](https://github.com/electron/electron/releases/tag/v21.1.1)|October 12, 2022||no|109|16.16.0|106.0.5249.103|125622|
|[v21.1.0](https://github.com/electron/electron/releases/tag/v21.1.0)|October 5, 2022||no|109|16.16.0|106.0.5249.91|111944|
|[v21.0.1](https://github.com/electron/electron/releases/tag/v21.0.1)|September 28, 2022||no|109|16.16.0|106.0.5249.61|176254|
|[v21.0.0](https://github.com/electron/electron/releases/tag/v21.0.0)|September 26, 2022||no|109|16.16.0|106.0.5249.51|65191|
|[v21.0.0-nightly.20220802](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220802)|August 2, 2022||yes|107|16.16.0|105.0.5187.0|543|
|[v21.0.0-nightly.20220801](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220801)|August 1, 2022||yes|107|16.16.0|105.0.5187.0|356|
|[v21.0.0-nightly.20220728](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220728)|July 28, 2022||yes|107|16.16.0|105.0.5187.0|453|
|[v21.0.0-nightly.20220727](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220727)|2022-07-27||yes|107|16.16.0|105.0.5187.0|373|
|[v21.0.0-nightly.20220726](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220726)|2022-07-26||yes|107|16.16.0|105.0.5187.0|347|
|[v21.0.0-nightly.20220725](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220725)|2022-07-25||yes|107|16.15.1|105.0.5187.0|412|
|[v21.0.0-nightly.20220722](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220722)|2022-07-22||yes|107|16.15.1|105.0.5187.0|393|
|[v21.0.0-nightly.20220721](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220721)|2022-07-21||yes|107|16.15.1|105.0.5187.0|366|
|[v21.0.0-nightly.20220720](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220720)|2022-07-20||yes|107|16.15.1|105.0.5187.0|343|
|[v21.0.0-nightly.20220719](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220719)|2022-07-19||yes|107|16.15.1|105.0.5173.0|357|
|[v21.0.0-nightly.20220708](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220708)|July 8, 2022||yes|107|16.15.1|105.0.5129.0|277|
|[v21.0.0-nightly.20220707](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220707)|July 7, 2022||yes|107|16.15.1|105.0.5129.0|356|
|[v21.0.0-nightly.20220706](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220706)|2022-07-06||yes|107|16.15.1|105.0.5129.0|172|
|[v21.0.0-nightly.20220705](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220705)|2022-07-05||yes|107|16.15.1|105.0.5129.0|180|
|[v21.0.0-nightly.20220704](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220704)|July 4, 2022||yes|107|16.15.1|105.0.5129.0|168|
|[v21.0.0-nightly.20220701](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220701)|July 1, 2022||yes|107|16.15.1|105.0.5129.0|227|
|[v21.0.0-nightly.20220630](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220630)|June 30, 2022||yes|107|16.15.1|105.0.5129.0|375|
|[v21.0.0-nightly.20220629](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220629)|June 29, 2022||yes|107|16.15.1|105.0.5129.0|355|
|[v21.0.0-nightly.20220628](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220628)|June 29, 2022||yes|107|16.15.1|105.0.5129.0|351|
|[v21.0.0-nightly.20220627](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220627)|2022-06-27||yes|107|16.15.1|104.0.5073.0|357|
|[v21.0.0-nightly.20220624](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220624)|2022-06-24||yes|107|16.15.1|104.0.5073.0|397|
|[v21.0.0-nightly.20220623](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220623)|2022-06-23||yes|107|16.15.1|104.0.5073.0|359|
|[v21.0.0-nightly.20220622](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220622)|June 22, 2022||yes|107|16.15.1|104.0.5073.0|358|
|[v21.0.0-nightly.20220621](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220621)|2022-06-21||yes|107|16.15.1|104.0.5073.0|160|
|[v21.0.0-nightly.20220620](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220620)|2022-06-20||yes|107|16.15.1|104.0.5073.0|167|
|[v21.0.0-nightly.20220617](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220617)|2022-06-17||yes|107|16.15.1|104.0.5073.0|400|
|[v21.0.0-nightly.20220616](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220616)|2022-06-16||yes|107|16.15.1|104.0.5073.0|351|
|[v21.0.0-nightly.20220615](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220615)|2022-06-15||yes|107|16.15.1|104.0.5073.0|354|
|[v21.0.0-nightly.20220614](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220614)|2022-06-14||yes|107|16.15.1|104.0.5073.0|340|
|[v21.0.0-nightly.20220613](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220613)|2022-06-13||yes|107|16.15.1|104.0.5073.0|293|
|[v21.0.0-nightly.20220610](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220610)|2022-06-10||yes|107|16.15.1|104.0.5073.0|356|
|[v21.0.0-nightly.20220609](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220609)|2022-06-09||yes|107|16.15.1|104.0.5073.0|301|
|[v21.0.0-nightly.20220608](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220608)|2022-06-08||yes|107|16.15.1|104.0.5073.0|297|
|[v21.0.0-nightly.20220607](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220607)|2022-06-07||yes|107|16.15.1|104.0.5073.0|296|
|[v21.0.0-nightly.20220606](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220606)|June 6, 2022||yes|107|16.15.1|104.0.5073.0|299|
|[v21.0.0-nightly.20220603](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220603)|June 3, 2022||yes|107|16.15.0|104.0.5073.0|417|
|[v21.0.0-nightly.20220602](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220602)|June 3, 2022||yes|107|16.15.0|104.0.5073.0|297|
|[v21.0.0-nightly.20220531](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220531)|May 31, 2022||yes|107|16.15.0|103.0.5044.0|328|
|[v21.0.0-nightly.20220530](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220530)|May 30, 2022||yes|107|16.15.0|103.0.5044.0|308|
|[v21.0.0-nightly.20220527](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220527)|May 27, 2022||yes|107|16.15.0|103.0.5044.0|359|
|[v21.0.0-nightly.20220526](https://github.com/electron/electron/releases/tag/v21.0.0-nightly.20220526)|May 26, 2022||yes|107|16.15.0|103.0.5044.0|308|
|[v21.0.0-beta.8](https://github.com/electron/electron/releases/tag/v21.0.0-beta.8)|September 22, 2022|beta-21-x-y|yes|109|16.16.0|106.0.5249.40|2928|
|[v21.0.0-beta.7](https://github.com/electron/electron/releases/tag/v21.0.0-beta.7)|September 19, 2022||yes|109|16.16.0|106.0.5249.40|2385|
|[v21.0.0-beta.6](https://github.com/electron/electron/releases/tag/v21.0.0-beta.6)|September 15, 2022||yes|109|16.16.0|106.0.5249.40|1502|
|[v21.0.0-beta.5](https://github.com/electron/electron/releases/tag/v21.0.0-beta.5)|September 12, 2022||yes|109|16.16.0|106.0.5216.0|1673|
|[v21.0.0-beta.4](https://github.com/electron/electron/releases/tag/v21.0.0-beta.4)|September 8, 2022||yes|109|16.16.0|106.0.5216.0|2960|
|[v21.0.0-beta.3](https://github.com/electron/electron/releases/tag/v21.0.0-beta.3)|September 7, 2022||yes|109|16.16.0|106.0.5216.0|1545|
|[v21.0.0-beta.2](https://github.com/electron/electron/releases/tag/v21.0.0-beta.2)|September 1, 2022||yes|109|16.16.0|106.0.5216.0|2145|
|[v21.0.0-beta.1](https://github.com/electron/electron/releases/tag/v21.0.0-beta.1)|August 30, 2022||yes|109|16.16.0|106.0.5216.0|1506|
|[v21.0.0-alpha.6](https://github.com/electron/electron/releases/tag/v21.0.0-alpha.6)|August 30, 2022|alpha-21-x-y|yes|109|16.16.0|106.0.5216.0|1466|
|[v21.0.0-alpha.5](https://github.com/electron/electron/releases/tag/v21.0.0-alpha.5)|August 23, 2022||yes|109|16.16.0|105.0.5187.0|1942|
|[v21.0.0-alpha.4](https://github.com/electron/electron/releases/tag/v21.0.0-alpha.4)|August 18, 2022||yes|109|16.16.0|105.0.5187.0|1615|
|[v21.0.0-alpha.3](https://github.com/electron/electron/releases/tag/v21.0.0-alpha.3)|August 15, 2022||yes|109|16.16.0|105.0.5187.0|1516|
|[v21.0.0-alpha.2](https://github.com/electron/electron/releases/tag/v21.0.0-alpha.2)|August 11, 2022||yes|109|16.16.0|105.0.5187.0|1608|
|[v21.0.0-alpha.1](https://github.com/electron/electron/releases/tag/v21.0.0-alpha.1)|AAugust 3, 2022||yes|109|16.16.0|105.0.5187.0|2199|
|[v20.3.8](https://github.com/electron/electron/releases/tag/v20.3.8)|November 30, 2022|20-x-y|no|107|16.15.0|104.0.5112.124|26483|
|[v20.3.7](https://github.com/electron/electron/releases/tag/v20.3.7)|2022-11-23||no|107|16.15.0|104.0.5112.124|9584|
|[v20.3.6](https://github.com/electron/electron/releases/tag/v20.3.6)|2022-11-21||no|107|16.15.0|104.0.5112.124|41103|
|[v20.3.5](https://github.com/electron/electron/releases/tag/v20.3.5)|2022-11-09||no|107|16.15.0|104.0.5112.124|35835|
|[v20.3.4](https://github.com/electron/electron/releases/tag/v20.3.4)|2022-11-02||no|107|16.15.0|104.0.5112.124|16901|
|[v20.3.3](https://github.com/electron/electron/releases/tag/v20.3.3)|2022-10-19||no|107|16.15.0|104.0.5112.124|32155|
|[v20.3.2](https://github.com/electron/electron/releases/tag/v20.3.2)|2022-10-12||no|107|16.15.0|104.0.5112.124|22208|
|[v20.3.1](https://github.com/electron/electron/releases/tag/v20.3.1)|2022-10-05||no|107|16.15.0|104.0.5112.124|64413|
|[v20.3.0](https://github.com/electron/electron/releases/tag/v20.3.0)|2022-09-28||no|107|16.15.0|104.0.5112.124|35763|
|[v20.2.0](https://github.com/electron/electron/releases/tag/v20.2.0)|September 22, 2022||no|107|16.15.0|104.0.5112.124|89516|
|[v20.1.4](https://github.com/electron/electron/releases/tag/v20.1.4)|2022-09-14||no|107|16.15.0|104.0.5112.114|145855|
|[v20.1.3](https://github.com/electron/electron/releases/tag/v20.1.3)|2022-09-08||no|107|16.15.0|104.0.5112.114|89209|
|[v20.1.2](https://github.com/electron/electron/releases/tag/v20.1.2)|2022-09-07||no|107|16.15.0|104.0.5112.114|28836|
|[v20.1.1](https://github.com/electron/electron/releases/tag/v20.1.1)|August 31, 2022||no|107|16.15.0|104.0.5112.102|95008|
|[v20.1.0](https://github.com/electron/electron/releases/tag/v20.1.0)|2022-08-24||no|107|16.15.0|104.0.5112.102|89338|
|[v20.0.3](https://github.com/electron/electron/releases/tag/v20.0.3)|2022-08-17||no|107|16.15.0|104.0.5112.81|163634|
|[v20.0.2](https://github.com/electron/electron/releases/tag/v20.0.2)|2022-08-10||no|107|16.15.0|104.0.5112.81|156009|
|[v20.0.1](https://github.com/electron/electron/releases/tag/v20.0.1)|August 3, 2022||no|107|16.15.0|104.0.5112.81|112485|
|[v20.0.0](https://github.com/electron/electron/releases/tag/v20.0.0)|August 1, 2022||no|107|16.15.0|104.0.5112.65|74925|
|[v20.0.0-nightly.20220524](https://github.com/electron/electron/releases/tag/v20.0.0-nightly.20220524)|May 24, 2022||yes|107|16.15.0|103.0.5044.0|413|
|[v20.0.0-nightly.20220523](https://github.com/electron/electron/releases/tag/v20.0.0-nightly.20220523)|2022-05-23||yes|107|16.15.0|103.0.5044.0|331|
|[v20.0.0-nightly.20220520](https://github.com/electron/electron/releases/tag/v20.0.0-nightly.20220520)|2022-05-20||yes|107|16.15.0|103.0.5044.0|364|
|[v20.0.0-nightly.20220519](https://github.com/electron/electron/releases/tag/v20.0.0-nightly.20220519)|2022-05-19||yes|107|16.15.0|103.0.5044.0|304|
|[v20.0.0-nightly.20220518](https://github.com/electron/electron/releases/tag/v20.0.0-nightly.20220518)|2022-05-18||yes|107|16.15.0|103.0.5044.0|393|
|[v20.0.0-nightly.20220517](https://github.com/electron/electron/releases/tag/v20.0.0-nightly.20220517)|2022-05-17||yes|107|16.15.0|102.0.4999.0|327|
|[v20.0.0-nightly.20220516](https://github.com/electron/electron/releases/tag/v20.0.0-nightly.20220516)|2022-05-16||yes|107|16.15.0|102.0.4999.0|180|
|[v20.0.0-nightly.20220513](https://github.com/electron/electron/releases/tag/v20.0.0-nightly.20220513)|2022-05-13||yes|107|16.15.0|102.0.4999.0|386|
|[v20.0.0-nightly.20220512](https://github.com/electron/electron/releases/tag/v20.0.0-nightly.20220512)|2022-05-12||yes|107|16.15.0|102.0.4999.0|384|
|[v20.0.0-nightly.20220511](https://github.com/electron/electron/releases/tag/v20.0.0-nightly.20220511)|2022-05-11||yes|107|16.15.0|102.0.4999.0|441|
|[v20.0.0-nightly.20220509](https://github.com/electron/electron/releases/tag/v20.0.0-nightly.20220509)|May 9, 2022||yes|107|16.14.2|102.0.4999.0|319|
|[v20.0.0-nightly.20220506](https://github.com/electron/electron/releases/tag/v20.0.0-nightly.20220506)|May 6, 2022||yes|107|16.14.2|102.0.4999.0|340|
|[v20.0.0-nightly.20220505](https://github.com/electron/electron/releases/tag/v20.0.0-nightly.20220505)|May 5, 2022||yes|107|16.14.2|102.0.4999.0|190|
|[v20.0.0-nightly.20220504](https://github.com/electron/electron/releases/tag/v20.0.0-nightly.20220504)|May 4, 2022||yes|107|16.14.2|102.0.4999.0|151|
|[v20.0.0-nightly.20220503](https://github.com/electron/electron/releases/tag/v20.0.0-nightly.20220503)|May 3, 2022||yes|107|16.14.2|102.0.4999.0|296|
|[v20.0.0-nightly.20220502](https://github.com/electron/electron/releases/tag/v20.0.0-nightly.20220502)|May 2, 2022||yes|107|16.14.2|102.0.4999.0|291|
|[v20.0.0-nightly.20220429](https://github.com/electron/electron/releases/tag/v20.0.0-nightly.20220429)|April 29, 2022||yes|107|16.14.2|102.0.4999.0|180|
|[v20.0.0-nightly.20220428](https://github.com/electron/electron/releases/tag/v20.0.0-nightly.20220428)|April 28, 2022||yes|107|16.14.2|102.0.4999.0|302|
|[v20.0.0-nightly.20220427](https://github.com/electron/electron/releases/tag/v20.0.0-nightly.20220427)|April 27, 2022||yes|107|16.14.2|102.0.4999.0|288|
|[v20.0.0-nightly.20220426](https://github.com/electron/electron/releases/tag/v20.0.0-nightly.20220426)|April 27, 2022||yes|107|16.14.2|102.0.4999.0|290|
|[v20.0.0-nightly.20220425](https://github.com/electron/electron/releases/tag/v20.0.0-nightly.20220425)|April 26, 2022||yes|107|16.14.2|102.0.4999.0|290|
|[v20.0.0-nightly.20220421](https://github.com/electron/electron/releases/tag/v20.0.0-nightly.20220421)|April 21, 2022||yes|107|16.14.2|102.0.4989.0|411|
|[v20.0.0-nightly.20220420](https://github.com/electron/electron/releases/tag/v20.0.0-nightly.20220420)|April 20, 2022||yes|107|16.14.2|102.0.4989.0|187|
|[v20.0.0-nightly.20220419](https://github.com/electron/electron/releases/tag/v20.0.0-nightly.20220419)|April 19, 2022||yes|107|16.14.2|102.0.4989.0|328|
|[v20.0.0-nightly.20220418](https://github.com/electron/electron/releases/tag/v20.0.0-nightly.20220418)|April 18, 2022||yes|107|16.14.2|102.0.4989.0|338|
|[v20.0.0-nightly.20220415](https://github.com/electron/electron/releases/tag/v20.0.0-nightly.20220415)|April 15, 2022||yes|107|16.14.2|102.0.4989.0|382|
|[v20.0.0-nightly.20220414](https://github.com/electron/electron/releases/tag/v20.0.0-nightly.20220414)|April 15, 2022||yes|107|16.14.2|102.0.4989.0|332|
|[v20.0.0-nightly.20220411](https://github.com/electron/electron/releases/tag/v20.0.0-nightly.20220411)|April 11, 2022||yes|107|16.14.2|102.0.4971.0|424|
|[v20.0.0-nightly.20220330](https://github.com/electron/electron/releases/tag/v20.0.0-nightly.20220330)|March 30, 2022||yes|107|16.14.2|102.0.4962.3|649|
|[v20.0.0-beta.13](https://github.com/electron/electron/releases/tag/v20.0.0-beta.13)|July 28, 2022|beta-20-x-y|yes|107|16.15.0|104.0.5112.57|2983|
|[v20.0.0-beta.12](https://github.com/electron/electron/releases/tag/v20.0.0-beta.12)|July 25, 2022||yes|107|16.15.0|104.0.5112.48|2947|
|[v20.0.0-beta.11](https://github.com/electron/electron/releases/tag/v20.0.0-beta.11)|July 21, 2022||yes|107|16.15.0|104.0.5112.48|3134|
|[v20.0.0-beta.10](https://github.com/electron/electron/releases/tag/v20.0.0-beta.10)|July 18, 2022||yes|107|16.15.0|104.0.5112.48|2875|
|[v20.0.0-beta.9](https://github.com/electron/electron/releases/tag/v20.0.0-beta.9)|July 14, 2022||yes|107|16.15.0|104.0.5112.39|2022|
|[v20.0.0-beta.8](https://github.com/electron/electron/releases/tag/v20.0.0-beta.8)|July 11, 2022||yes|107|16.15.0|104.0.5073.0|4241|
|[v20.0.0-beta.7](https://github.com/electron/electron/releases/tag/v20.0.0-beta.7)|July 8, 2022||yes|107|16.15.0|104.0.5073.0|1685|
|[v20.0.0-beta.6](https://github.com/electron/electron/releases/tag/v20.0.0-beta.6)|July 7, 2022||yes|107|16.15.0|104.0.5073.0|1454|
|[v20.0.0-beta.5](https://github.com/electron/electron/releases/tag/v20.0.0-beta.5)|July 4, 2022||yes|107|16.15.0|104.0.5073.0|1652|
|[v20.0.0-beta.4](https://github.com/electron/electron/releases/tag/v20.0.0-beta.4)|June 30, 2022||yes|107|16.15.0|104.0.5073.0|1375|
|[v20.0.0-beta.3](https://github.com/electron/electron/releases/tag/v20.0.0-beta.3)|June 27, 2022||yes|107|16.15.0|104.0.5073.0|1784|
|[v20.0.0-beta.2](https://github.com/electron/electron/releases/tag/v20.0.0-beta.2)|June 23, 2022||yes|107|16.15.0|104.0.5073.0|1811|
|[v20.0.0-beta.1](https://github.com/electron/electron/releases/tag/v20.0.0-beta.1)|June 21, 2022||yes|107|16.15.0|104.0.5073.0|1770|
|[v20.0.0-alpha.7](https://github.com/electron/electron/releases/tag/v20.0.0-alpha.7)|June 20, 2022|alpha-20-x-y|yes|107|16.15.0|104.0.5073.0|1894|
|[v20.0.0-alpha.6](https://github.com/electron/electron/releases/tag/v20.0.0-alpha.6)|June 16, 2022||yes|107|16.15.0|104.0.5073.0|1626|
|[v20.0.0-alpha.5](https://github.com/electron/electron/releases/tag/v20.0.0-alpha.5)|June 13, 2022||yes|107|16.15.0|104.0.5073.0|1692|
|[v20.0.0-alpha.4](https://github.com/electron/electron/releases/tag/v20.0.0-alpha.4)|June 9, 2022||yes|107|16.15.0|104.0.5073.0|1613|
|[v20.0.0-alpha.3](https://github.com/electron/electron/releases/tag/v20.0.0-alpha.3)|June 6, 2022||yes|107|16.15.0|104.0.5073.0|1889|
|[v20.0.0-alpha.2](https://github.com/electron/electron/releases/tag/v20.0.0-alpha.2)|June 3, 2022||yes|107|16.15.0|104.0.5073.0|1500|
|[v20.0.0-alpha.1](https://github.com/electron/electron/releases/tag/v20.0.0-alpha.1)|May 25, 2022||yes|107|16.15.0|103.0.5044.0|2325|
|[v19.1.9](https://github.com/electron/electron/releases/tag/v19.1.9)|November 30, 2022|19-x-y|no|106|16.14.2|102.0.5005.167|31125|
|[v19.1.8](https://github.com/electron/electron/releases/tag/v19.1.8)|November 28, 2022||no|106|16.14.2|102.0.5005.167|33950|
|[v19.1.7](https://github.com/electron/electron/releases/tag/v19.1.7)|November 23, 2022||no|106|16.14.2|102.0.5005.167|12166|
|[v19.1.6](https://github.com/electron/electron/releases/tag/v19.1.6)|November 16, 2022||no|106|16.14.2|102.0.5005.167|14564|
|[v19.1.5](https://github.com/electron/electron/releases/tag/v19.1.5)|November 9, 2022||no|106|16.14.2|102.0.5005.167|14117|
|[v19.1.4](https://github.com/electron/electron/releases/tag/v19.1.4)|November 2, 2022||no|106|16.14.2|102.0.5005.167|39195|
|[v19.1.3](https://github.com/electron/electron/releases/tag/v19.1.3)|October 12, 2022||no|106|16.14.2|102.0.5005.167|67061|
|[v19.1.2](https://github.com/electron/electron/releases/tag/v19.1.2)|October 5, 2022||no|106|16.14.2|102.0.5005.167|13243|
|[v19.1.1](https://github.com/electron/electron/releases/tag/v19.1.1)|September 28, 2022||no|106|16.14.2|102.0.5005.167|41439|
|[v19.1.0](https://github.com/electron/electron/releases/tag/v19.1.0)|September 23, 2022||no|106|16.14.2|102.0.5005.167|43028|
|[v19.0.17](https://github.com/electron/electron/releases/tag/v19.0.17)|September 14, 2022||no|106|16.14.2|102.0.5005.167|97661|
|[v19.0.16](https://github.com/electron/electron/releases/tag/v19.0.16)|2022-09-08||no|106|16.14.2|102.0.5005.167|39331|
|[v19.0.15](https://github.com/electron/electron/releases/tag/v19.0.15)|2022-08-31||no|106|16.14.2|102.0.5005.167|37051|
|[v19.0.14](https://github.com/electron/electron/releases/tag/v19.0.14)|2022-08-24||no|106|16.14.2|102.0.5005.167|26030|
|[v19.0.13](https://github.com/electron/electron/releases/tag/v19.0.13)|2022-08-17||no|106|16.14.2|102.0.5005.167|57977|
|[v19.0.12](https://github.com/electron/electron/releases/tag/v19.0.12)|2022-08-10||no|106|16.14.2|102.0.5005.167|87366|
|[v19.0.11](https://github.com/electron/electron/releases/tag/v19.0.11)|August 3, 2022||no|106|16.14.2|102.0.5005.167|121736|
|[v19.0.10](https://github.com/electron/electron/releases/tag/v19.0.10)|July 27, 2022||no|106|16.14.2|102.0.5005.167|147312|
|[v19.0.9](https://github.com/electron/electron/releases/tag/v19.0.9)|2022-07-21||no|106|16.14.2|102.0.5005.167|137517|
|[v19.0.8](https://github.com/electron/electron/releases/tag/v19.0.8)|2022-07-06||no|106|16.14.2|102.0.5005.148|310759|
|[v19.0.7](https://github.com/electron/electron/releases/tag/v19.0.7)|June 30, 2022||no|106|16.14.2|102.0.5005.134|138919|
|[v19.0.6](https://github.com/electron/electron/releases/tag/v19.0.6)|2022-06-22||no|106|16.14.2|102.0.5005.115|195380|
|[v19.0.5](https://github.com/electron/electron/releases/tag/v19.0.5)|2022-06-20||no|106|16.14.2|102.0.5005.115|40664|
|[v19.0.4](https://github.com/electron/electron/releases/tag/v19.0.4)|2022-06-08||no|106|16.14.2|102.0.5005.63|194193|
|[v19.0.3](https://github.com/electron/electron/releases/tag/v19.0.3)|2022-06-03||no|106|16.14.2|102.0.5005.63|121423|
|[v19.0.2](https://github.com/electron/electron/releases/tag/v19.0.2)|June 1, 2022||no|106|16.14.2|102.0.5005.63|43919|
|[v19.0.1](https://github.com/electron/electron/releases/tag/v19.0.1)|May 25, 2022||no|106|16.14.2|102.0.5005.61|63541|
|[v19.0.0](https://github.com/electron/electron/releases/tag/v19.0.0)|May 23, 2022||no|106|16.14.2|102.0.5005.61|95889|
|[v19.0.0-nightly.20220329](https://github.com/electron/electron/releases/tag/v19.0.0-nightly.20220329)|March 29, 2022||yes|106|16.14.2|102.0.4962.3|635|
|[v19.0.0-nightly.20220328](https://github.com/electron/electron/releases/tag/v19.0.0-nightly.20220328)|March 29, 2022||yes|106|16.14.2|102.0.4962.3|359|
|[v19.0.0-nightly.20220325](https://github.com/electron/electron/releases/tag/v19.0.0-nightly.20220325)|2022-03-25||yes|106|16.14.2|102.0.4961.0|423|
|[v19.0.0-nightly.20220324](https://github.com/electron/electron/releases/tag/v19.0.0-nightly.20220324)|2022-03-24||yes|106|16.14.2|100.0.4894.0|358|
|[v19.0.0-nightly.20220323](https://github.com/electron/electron/releases/tag/v19.0.0-nightly.20220323)|March 23, 2022||yes|106|16.13.2|100.0.4894.0|191|
|[v19.0.0-nightly.20220322](https://github.com/electron/electron/releases/tag/v19.0.0-nightly.20220322)|March 23, 2022||yes|106|16.13.2|100.0.4894.0|333|
|[v19.0.0-nightly.20220321](https://github.com/electron/electron/releases/tag/v19.0.0-nightly.20220321)|2022-03-21||yes|106|16.13.2|100.0.4894.0|360|
|[v19.0.0-nightly.20220318](https://github.com/electron/electron/releases/tag/v19.0.0-nightly.20220318)|2022-03-18||yes|106|16.13.2|100.0.4894.0|394|
|[v19.0.0-nightly.20220317](https://github.com/electron/electron/releases/tag/v19.0.0-nightly.20220317)|2022-03-17||yes|106|16.13.2|100.0.4894.0|359|
|[v19.0.0-nightly.20220316](https://github.com/electron/electron/releases/tag/v19.0.0-nightly.20220316)|2022-03-16||yes|106|16.13.2|100.0.4894.0|494|
|[v19.0.0-nightly.20220315](https://github.com/electron/electron/releases/tag/v19.0.0-nightly.20220315)|2022-03-15||yes|106|16.13.2|100.0.4894.0|356|
|[v19.0.0-nightly.20220314](https://github.com/electron/electron/releases/tag/v19.0.0-nightly.20220314)|2022-03-14||yes|106|16.13.2|100.0.4894.0|204|
|[v19.0.0-nightly.20220311](https://github.com/electron/electron/releases/tag/v19.0.0-nightly.20220311)|2022-03-11||yes|106|16.13.2|100.0.4894.0|375|
|[v19.0.0-nightly.20220310](https://github.com/electron/electron/releases/tag/v19.0.0-nightly.20220310)|March 10, 2022||yes|106|16.13.2|100.0.4894.0|191|
|[v19.0.0-nightly.20220309](https://github.com/electron/electron/releases/tag/v19.0.0-nightly.20220309)|2022-03-09||yes|106|16.13.2|100.0.4894.0|396|
|[v19.0.0-nightly.20220308](https://github.com/electron/electron/releases/tag/v19.0.0-nightly.20220308)|2022-03-08||yes|106|16.13.2|100.0.4894.0|352|
|[v19.0.0-nightly.20220209](https://github.com/electron/electron/releases/tag/v19.0.0-nightly.20220209)|February 9, 2022||yes|106|16.13.2|99.0.4767.0|1401|
|[v19.0.0-nightly.20220208](https://github.com/electron/electron/releases/tag/v19.0.0-nightly.20220208)|2022-02-08||yes|106|16.13.2|99.0.4767.0|315|
|[v19.0.0-nightly.20220207](https://github.com/electron/electron/releases/tag/v19.0.0-nightly.20220207)|2022-02-07||yes|106|16.13.2|99.0.4767.0|325|
|[v19.0.0-nightly.20220204](https://github.com/electron/electron/releases/tag/v19.0.0-nightly.20220204)|2022-02-04||yes|106|16.13.2|99.0.4767.0|445|
|[v19.0.0-nightly.20220203](https://github.com/electron/electron/releases/tag/v19.0.0-nightly.20220203)|2022-02-03||yes|106|16.13.2|99.0.4767.0|329|
|[v19.0.0-nightly.20220202](https://github.com/electron/electron/releases/tag/v19.0.0-nightly.20220202)|February 2, 2022||yes|103|16.13.2|99.0.4767.0|321|
|[v19.0.0-beta.8](https://github.com/electron/electron/releases/tag/v19.0.0-beta.8)|2022-05-19|beta-19-x-y|yes|106|16.14.2|102.0.5005.49|3720|
|[v19.0.0-beta.7](https://github.com/electron/electron/releases/tag/v19.0.0-beta.7)|2022-05-16||yes|106|16.14.2|102.0.5005.40|3687|
|[v19.0.0-beta.6](https://github.com/electron/electron/releases/tag/v19.0.0-beta.6)|2022-05-12||yes|106|16.14.2|102.0.5005.40|3088|
|[v19.0.0-beta.5](https://github.com/electron/electron/releases/tag/v19.0.0-beta.5)|May 9, 2022||yes|106|16.14.2|102.0.5005.40|3251|
|[v19.0.0-beta.4](https://github.com/electron/electron/releases/tag/v19.0.0-beta.4)|May 5, 2022||yes|106|16.14.2|102.0.5005.27|4837|
|[v19.0.0-beta.3](https://github.com/electron/electron/releases/tag/v19.0.0-beta.3)|May 2, 2022||yes|106|16.14.2|102.0.4999.0|2313|
|[v19.0.0-beta.2](https://github.com/electron/electron/releases/tag/v19.0.0-beta.2)|2022-04-29||yes|106|16.14.2|102.0.4999.0|1928|
|[v19.0.0-beta.1](https://github.com/electron/electron/releases/tag/v19.0.0-beta.1)|2022-04-28||yes|106|16.14.2|102.0.4999.0|2137|
|[v19.0.0-alpha.5](https://github.com/electron/electron/releases/tag/v19.0.0-alpha.5)|2022-04-25|alpha-19-x-y|yes|106|16.14.2|102.0.4989.0|2260|
|[v19.0.0-alpha.4](https://github.com/electron/electron/releases/tag/v19.0.0-alpha.4)|2022-04-21||yes|106|16.14.2|102.0.4989.0|2666|
|[v19.0.0-alpha.3](https://github.com/electron/electron/releases/tag/v19.0.0-alpha.3)|2022-04-18||yes|106|16.14.2|102.0.4971.0|2171|
|[v19.0.0-alpha.2](https://github.com/electron/electron/releases/tag/v19.0.0-alpha.2)|2022-04-15||yes|106|16.14.2|102.0.4971.0|2482|
|[v19.0.0-alpha.1](https://github.com/electron/electron/releases/tag/v19.0.0-alpha.1)|March 30, 2022||yes|106|16.14.2|102.0.4962.3|2850|
|[v18.3.15](https://github.com/electron/electron/releases/tag/v18.3.15)|September 27, 2022|18-x-y|no|103|16.13.2|100.0.4896.160|91123|
|[v18.3.14](https://github.com/electron/electron/releases/tag/v18.3.14)|September 24, 2022||no|103|16.13.2|100.0.4896.160|5621|
|[v18.3.13](https://github.com/electron/electron/releases/tag/v18.3.13)|September 14, 2022||no|103|16.13.2|100.0.4896.160|24000|
|[v18.3.12](https://github.com/electron/electron/releases/tag/v18.3.12)|September 8, 2022||no|103|16.13.2|100.0.4896.160|10896|
|[v18.3.11](https://github.com/electron/electron/releases/tag/v18.3.11)|August 31, 2022||no|103|16.13.2|100.0.4896.160|12553|
|[v18.3.9](https://github.com/electron/electron/releases/tag/v18.3.9)|August 17, 2022||no|103|16.13.2|100.0.4896.160|40637|
|[v18.3.8](https://github.com/electron/electron/releases/tag/v18.3.8)|August 10, 2022||no|103|16.13.2|100.0.4896.160|12824|
|[v18.3.7](https://github.com/electron/electron/releases/tag/v18.3.7)|August 3, 2022||no|103|16.13.2|100.0.4896.160|42659|
|[v18.3.6](https://github.com/electron/electron/releases/tag/v18.3.6)|July 28, 2022||no|103|16.13.2|100.0.4896.160|23034|
|[v18.3.5](https://github.com/electron/electron/releases/tag/v18.3.5)|June 22, 2022||no|103|16.13.2|100.0.4896.160|214098|
|[v18.3.4](https://github.com/electron/electron/releases/tag/v18.3.4)|June 15, 2022||no|103|16.13.2|100.0.4896.160|47056|
|[v18.3.3](https://github.com/electron/electron/releases/tag/v18.3.3)|June 8, 2022||no|103|16.13.2|100.0.4896.160|26146|
|[v18.3.2](https://github.com/electron/electron/releases/tag/v18.3.2)|June 1, 2022||no|103|16.13.2|100.0.4896.160|27529|
|[v18.3.1](https://github.com/electron/electron/releases/tag/v18.3.1)|2022-05-25||no|103|16.13.2|100.0.4896.160|38498|
|[v18.3.0](https://github.com/electron/electron/releases/tag/v18.3.0)|2022-05-23||no|103|16.13.2|100.0.4896.160|58431|
|[v18.2.4](https://github.com/electron/electron/releases/tag/v18.2.4)|2022-05-18||no|103|16.13.2|100.0.4896.160|96235|
|[v18.2.3](https://github.com/electron/electron/releases/tag/v18.2.3)|May 11, 2022||no|103|16.13.2|100.0.4896.143|143380|
|[v18.2.2](https://github.com/electron/electron/releases/tag/v18.2.2)|May 11, 2022||no|103|16.13.2|100.0.4896.143|58663|
|[v18.2.1](https://github.com/electron/electron/releases/tag/v18.2.1)|May 4, 2022||no|103|16.13.2|100.0.4896.143|5420|
|[v18.2.0](https://github.com/electron/electron/releases/tag/v18.2.0)|2022-04-29||no|103|16.13.2|100.0.4896.143|246965|
|[v18.1.0](https://github.com/electron/electron/releases/tag/v18.1.0)|2022-04-21||no|103|16.13.2|100.0.4896.127|288559|
|[v18.0.4](https://github.com/electron/electron/releases/tag/v18.0.4)|2022-04-14||no|103|16.13.2|100.0.4896.75|109106|
|[v18.0.3](https://github.com/electron/electron/releases/tag/v18.0.3)|2022-04-07||no|103|16.13.2|100.0.4896.75|218643|
|[v18.0.2](https://github.com/electron/electron/releases/tag/v18.0.2)|2022-04-05||no|103|16.13.2|100.0.4896.60|31998|
|[v18.0.1](https://github.com/electron/electron/releases/tag/v18.0.1)|2022-03-30||no|103|16.13.2|100.0.4896.60|139271|
|[v18.0.0](https://github.com/electron/electron/releases/tag/v18.0.0)|2022-03-29||no|103|16.13.2|100.0.4896.56|85648|
|[v18.0.0-nightly.20220201](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20220201)|February 1, 2022||yes|103|16.13.2|99.0.4767.0|193|
|[v18.0.0-nightly.20220131](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20220131)|January 31, 2022||yes|103|16.13.2|99.0.4767.0|244|
|[v18.0.0-nightly.20220128](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20220128)|January 28, 2022||yes|103|16.13.2|99.0.4767.0|394|
|[v18.0.0-nightly.20220127](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20220127)|January 27, 2022||yes|103|16.13.2|99.0.4767.0|206|
|[v18.0.0-nightly.20220125](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20220125)|January 25, 2022||yes|103|16.13.2|99.0.4767.0|372|
|[v18.0.0-nightly.20220124](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20220124)|2022-01-24||yes|103|16.13.2|99.0.4767.0|354|
|[v18.0.0-nightly.20220121](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20220121)|2022-01-21||yes|103|16.13.2|99.0.4767.0|383|
|[v18.0.0-nightly.20220119](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20220119)|2022-01-19||yes|103|16.13.2|99.0.4767.0|369|
|[v18.0.0-nightly.20220118](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20220118)|2022-01-18||yes|103|16.13.2|99.0.4767.0|339|
|[v18.0.0-nightly.20220117](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20220117)|2022-01-17||yes|103|16.13.2|99.0.4767.0|353|
|[v18.0.0-nightly.20220114](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20220114)|2022-01-14||yes|103|16.13.2|99.0.4767.0|407|
|[v18.0.0-nightly.20220113](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20220113)|2022-01-13||yes|103|16.13.2|99.0.4767.0|324|
|[v18.0.0-nightly.20220112](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20220112)|2022-01-12||yes|103|16.13.2|99.0.4767.0|343|
|[v18.0.0-nightly.20220111](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20220111)|January 11, 2022||yes|103|16.13.1|99.0.4767.0|339|
|[v18.0.0-nightly.20220111](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20220111)|January 11, 2022||yes|103|16.13.1|99.0.4767.0|339|
|[v18.0.0-nightly.20220110](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20220110)|January 10, 2022||yes|103|16.13.1|98.0.4706.0|327|
|[v18.0.0-nightly.20220110](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20220110)|January 10, 2022||yes|103|16.13.1|98.0.4706.0|327|
|[v18.0.0-nightly.20220107](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20220107)|January 7, 2022||yes|103|16.13.1|98.0.4706.0|387|
|[v18.0.0-nightly.20220107](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20220107)|January 7, 2022||yes|103|16.13.1|98.0.4706.0|387|
|[v18.0.0-nightly.20220106](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20220106)|January 6, 2022||yes|103|16.13.1|98.0.4706.0|331|
|[v18.0.0-nightly.20220106](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20220106)|January 6, 2022||yes|103|16.13.1|98.0.4706.0|331|
|[v18.0.0-nightly.20220105](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20220105)|January 5, 2022||yes|103|16.13.1|98.0.4706.0|328|
|[v18.0.0-nightly.20220105](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20220105)|January 5, 2022||yes|103|16.13.1|98.0.4706.0|328|
|[v18.0.0-nightly.20220104](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20220104)|January 4, 2022||yes|103|16.13.1|98.0.4706.0|315|
|[v18.0.0-nightly.20220103](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20220103)|January 3, 2022||yes|103|16.13.1|98.0.4706.0|322|
|[v18.0.0-nightly.20211231](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20211231)|December 31, 2021||yes|103|16.13.1|98.0.4706.0|503|
|[v18.0.0-nightly.20211229](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20211229)|2021-12-29||yes|103|16.13.1|98.0.4706.0|453|
|[v18.0.0-nightly.20211228](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20211228)|2021-12-28||yes|103|16.13.1|98.0.4706.0|471|
|[v18.0.0-nightly.20211223](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20211223)|December 24, 2021||yes|103|16.13.1|98.0.4706.0|506|
|[v18.0.0-nightly.20211222](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20211222)|2021-12-22||yes|103|16.13.1|98.0.4706.0|557|
|[v18.0.0-nightly.20211221](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20211221)|2021-12-21||yes|103|16.13.1|98.0.4706.0|450|
|[v18.0.0-nightly.20211220](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20211220)|2021-12-20||yes|103|16.13.1|98.0.4706.0|459|
|[v18.0.0-nightly.20211217](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20211217)|2021-12-17||yes|103|16.13.1|98.0.4706.0|488|
|[v18.0.0-nightly.20211216](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20211216)|2021-12-16||yes|103|16.13.0|98.0.4706.0|465|
|[v18.0.0-nightly.20211215](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20211215)|2021-12-15||yes|103|16.13.0|98.0.4706.0|543|
|[v18.0.0-nightly.20211214](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20211214)|2021-12-14||yes|103|16.13.0|98.0.4706.0|542|
|[v18.0.0-nightly.20211213](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20211213)|2021-12-13||yes|103|16.13.0|98.0.4706.0|530|
|[v18.0.0-nightly.20211210](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20211210)|December 10, 2021||yes|103|16.13.0|98.0.4706.0|606|
|[v18.0.0-nightly.20211209](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20211209)|2021-12-09||yes|103|16.13.0|98.0.4706.0|543|
|[v18.0.0-nightly.20211208](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20211208)|2021-12-08||yes|103|16.13.0|98.0.4706.0|542|
|[v18.0.0-nightly.20211207](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20211207)|2021-12-08||yes|103|16.13.0|98.0.4706.0|517|
|[v18.0.0-nightly.20211206](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20211206)|2021-12-06||yes|103|16.13.0|98.0.4706.0|531|
|[v18.0.0-nightly.20211203](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20211203)|2021-12-03||yes|103|16.13.0|98.0.4706.0|586|
|[v18.0.0-nightly.20211202](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20211202)|2021-12-02||yes|103|16.13.0|98.0.4706.0|546|
|[v18.0.0-nightly.20211201](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20211201)|December 1, 2021||yes|103|16.13.0|98.0.4706.0|610|
|[v18.0.0-nightly.20211130](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20211130)|2021-11-30||yes|103|16.13.0|98.0.4706.0|411|
|[v18.0.0-nightly.20211129](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20211129)|2021-11-29||yes|103|16.13.0|98.0.4706.0|410|
|[v18.0.0-nightly.20211126](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20211126)|2021-11-26||yes|103|16.13.0|98.0.4706.0|483|
|[v18.0.0-nightly.20211125](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20211125)|2021-11-25||yes|103|16.13.0|98.0.4706.0|406|
|[v18.0.0-nightly.20211124](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20211124)|2021-11-24||yes|103|16.13.0|98.0.4706.0|399|
|[v18.0.0-nightly.20211123](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20211123)|2021-11-23||yes|103|16.13.0|96.0.4664.4|406|
|[v18.0.0-nightly.20211122](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20211122)|2021-11-22||yes|103|16.13.0|96.0.4664.4|398|
|[v18.0.0-nightly.20211119](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20211119)|November 20, 2021||yes|103|16.13.0|96.0.4664.4|455|
|[v18.0.0-nightly.20211118](https://github.com/electron/electron/releases/tag/v18.0.0-nightly.20211118)|November 18, 2021||yes|103|16.13.0|96.0.4664.4|409|
|[v18.0.0-beta.6](https://github.com/electron/electron/releases/tag/v18.0.0-beta.6)|March 24, 2022|beta-18-x-y|yes|103|16.13.2|100.0.4894.0|3527|
|[v18.0.0-beta.5](https://github.com/electron/electron/releases/tag/v18.0.0-beta.5)|March 21, 2022||yes|103|16.13.2|100.0.4894.0|3720|
|[v18.0.0-beta.4](https://github.com/electron/electron/releases/tag/v18.0.0-beta.4)|March 17, 2022||yes|103|16.13.2|100.0.4894.0|2901|
|[v18.0.0-beta.3](https://github.com/electron/electron/releases/tag/v18.0.0-beta.3)|March 14, 2022||yes|103|16.13.2|100.0.4894.0|4713|
|[v18.0.0-beta.2](https://github.com/electron/electron/releases/tag/v18.0.0-beta.2)|March 10, 2022||yes|103|16.13.2|100.0.4894.0|2984|
|[v18.0.0-beta.1](https://github.com/electron/electron/releases/tag/v18.0.0-beta.1)|March 8, 2022||yes|103|16.13.2|100.0.4894.0|2162|
|[v18.0.0-alpha.5](https://github.com/electron/electron/releases/tag/v18.0.0-alpha.5)|February 28, 2022|alpha-18-x-y|yes|103|16.13.2|99.0.4767.0|2271|
|[v18.0.0-alpha.4](https://github.com/electron/electron/releases/tag/v18.0.0-alpha.4)|February 24, 2022||yes|103|16.13.2|99.0.4767.0|3425|
|[v18.0.0-alpha.3](https://github.com/electron/electron/releases/tag/v18.0.0-alpha.3)|February 14, 2022||yes|103|16.13.2|99.0.4767.0|2063|
|[v18.0.0-alpha.2](https://github.com/electron/electron/releases/tag/v18.0.0-alpha.2)|February 8, 2022||yes|103|16.13.2|99.0.4767.0|3286|
|[v18.0.0-alpha.1](https://github.com/electron/electron/releases/tag/v18.0.0-alpha.1)|February 2, 2022||yes|103|16.13.2|99.0.4767.0|2980|
|[v17.4.11](https://github.com/electron/electron/releases/tag/v17.4.11)|August 1, 2022|17-x-y|no|101|16.13.0|98.0.4758.141|134886|
|[v17.4.10](https://github.com/electron/electron/releases/tag/v17.4.10)|July 7, 2022||no|101|16.13.0|98.0.4758.141|46845|
|[v17.4.9](https://github.com/electron/electron/releases/tag/v17.4.9)|2022-06-30||no|101|16.13.0|98.0.4758.141|11952|
|[v17.4.8](https://github.com/electron/electron/releases/tag/v17.4.8)|2022-06-20||no|101|16.13.0|98.0.4758.141|19884|
|[v17.4.7](https://github.com/electron/electron/releases/tag/v17.4.7)|2022-06-01||no|101|16.13.0|98.0.4758.141|92999|
|[v17.4.6](https://github.com/electron/electron/releases/tag/v17.4.6)|2022-05-25||no|101|16.13.0|98.0.4758.141|22405|
|[v17.4.5](https://github.com/electron/electron/releases/tag/v17.4.5)|2022-05-18||no|101|16.13.0|98.0.4758.141|21073|
|[v17.4.4](https://github.com/electron/electron/releases/tag/v17.4.4)|2022-05-11||no|101|16.13.0|98.0.4758.141|55598|
|[v17.4.3](https://github.com/electron/electron/releases/tag/v17.4.3)|May 5, 2022||no|101|16.13.0|98.0.4758.141|30709|
|[v17.4.2](https://github.com/electron/electron/releases/tag/v17.4.2)|2022-04-29||no|101|16.13.0|98.0.4758.141|69760|
|[v17.4.1](https://github.com/electron/electron/releases/tag/v17.4.1)|2022-04-20||no|101|16.13.0|98.0.4758.141|56659|
|[v17.4.0](https://github.com/electron/electron/releases/tag/v17.4.0)|2022-04-05||no|101|16.13.0|98.0.4758.141|88289|
|[v17.3.1](https://github.com/electron/electron/releases/tag/v17.3.1)|2022-03-30||no|101|16.13.0|98.0.4758.141|57834|
|[v17.3.0](https://github.com/electron/electron/releases/tag/v17.3.0)|2022-03-29||no|101|16.13.0|98.0.4758.141|25967|
|[v17.2.0](https://github.com/electron/electron/releases/tag/v17.2.0)|2022-03-23||no|101|16.13.0|98.0.4758.109|229628|
|[v17.1.2](https://github.com/electron/electron/releases/tag/v17.1.2)|2022-03-09||no|101|16.13.0|98.0.4758.109|242995|
|[v17.1.1](https://github.com/electron/electron/releases/tag/v17.1.1)|2022-03-07||no|101|16.13.0|98.0.4758.109|117431|
|[v17.1.0](https://github.com/electron/electron/releases/tag/v17.1.0)|2022-02-23||no|101|16.13.0|98.0.4758.102|210548|
|[v17.0.1](https://github.com/electron/electron/releases/tag/v17.0.1)|2022-02-15||no|101|16.13.0|98.0.4758.82|168257|
|[v17.0.0](https://github.com/electron/electron/releases/tag/v17.0.0)|February 1, 2022||no|101|16.13.0|98.0.4758.74|368641|
|[v17.0.0-nightly.20211117](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20211117)|November 17, 2021||yes|101|16.13.0|96.0.4664.4|1460|
|[v17.0.0-nightly.20211116](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20211116)|2021-11-16||yes|101|16.13.0|96.0.4664.4|408|
|[v17.0.0-nightly.20211115](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20211115)|2021-11-15||yes|101|16.13.0|96.0.4664.4|419|
|[v17.0.0-nightly.20211112](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20211112)|2021-11-12||yes|101|16.13.0|96.0.4664.4|474|
|[v17.0.0-nightly.20211111](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20211111)|November 11, 2021||yes|101|16.13.0|96.0.4664.4|417|
|[v17.0.0-nightly.20211110](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20211110)|2021-11-10||yes|101|16.13.0|96.0.4664.4|393|
|[v17.0.0-nightly.20211109](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20211109)|2021-11-09||yes|101|16.13.0|96.0.4664.4|471|
|[v17.0.0-nightly.20211108](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20211108)|2021-11-08||yes|101|16.13.0|96.0.4664.4|418|
|[v17.0.0-nightly.20211105](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20211105)|2021-11-05||yes|101|16.13.0|96.0.4664.4|475|
|[v17.0.0-nightly.20211104](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20211104)|2021-11-04||yes|101|16.13.0|96.0.4664.4|407|
|[v17.0.0-nightly.20211103](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20211103)|2021-11-03||yes|101|16.13.0|96.0.4664.4|408|
|[v17.0.0-nightly.20211102](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20211102)|2021-11-02||yes|101|16.13.0|96.0.4664.4|407|
|[v17.0.0-nightly.20211101](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20211101)|November 1, 2021||yes|101|16.12.0|96.0.4664.4|479|
|[v17.0.0-nightly.20211029](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20211029)|2021-10-29||yes|101|16.12.0|96.0.4664.4|346|
|[v17.0.0-nightly.20211028](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20211028)|2021-10-28||yes|101|16.12.0|96.0.4664.4|264|
|[v17.0.0-nightly.20211027](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20211027)|2021-10-27||yes|101|16.12.0|96.0.4664.4|257|
|[v17.0.0-nightly.20211026](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20211026)|2021-10-26||yes|101|16.12.0|96.0.4664.4|250|
|[v17.0.0-nightly.20211025](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20211025)|2021-10-25||yes|101|16.11.1|96.0.4664.4|261|
|[v17.0.0-nightly.20211022](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20211022)|2021-10-23||yes|101|16.11.1|96.0.4664.4|454|
|[v17.0.0-nightly.20211021](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20211021)|2021-10-21||yes|101|16.11.1|96.0.4647.0|267|
|[v17.0.0-nightly.20211020](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20211020)|2021-10-20||yes|101|16.11.1|96.0.4647.0|274|
|[v17.0.0-nightly.20211019](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20211019)|2021-10-19||yes|101|16.11.1|96.0.4647.0|259|
|[v17.0.0-nightly.20211018](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20211018)|2021-10-18||yes|101|16.11.1|96.0.4647.0|396|
|[v17.0.0-nightly.20211015](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20211015)|2021-10-15||yes|101|16.11.1|96.0.4647.0|466|
|[v17.0.0-nightly.20211014](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20211014)|October 14, 2021||yes|101|16.11.1|96.0.4647.0|262|
|[v17.0.0-nightly.20211013](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20211013)|2021-10-14||yes|101|16.10.0|96.0.4647.0|398|
|[v17.0.0-nightly.20211012](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20211012)|2021-10-12||yes|101|16.10.0|96.0.4647.0|274|
|[v17.0.0-nightly.20211011](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20211011)|2021-10-11||yes|101|16.10.0|96.0.4647.0|258|
|[v17.0.0-nightly.20211008](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20211008)|2021-10-08||yes|101|16.10.0|96.0.4647.0|456|
|[v17.0.0-nightly.20211007](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20211007)|2021-10-07||yes|99|16.10.0|96.0.4647.0|258|
|[v17.0.0-nightly.20211006](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20211006)|2021-10-06||yes|99|16.10.0|96.0.4647.0|251|
|[v17.0.0-nightly.20211005](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20211005)|2021-10-05||yes|99|16.10.0|95.0.4629.0|408|
|[v17.0.0-nightly.20211004](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20211004)|2021-10-04||yes|99|16.10.0|95.0.4629.0|400|
|[v17.0.0-nightly.20211001](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20211001)|October 1, 2021||yes|99|16.10.0|95.0.4629.0|464|
|[v17.0.0-nightly.20210930](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20210930)|2021-09-30||yes|99|16.10.0|95.0.4629.0|417|
|[v17.0.0-nightly.20210929](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20210929)|2021-09-29||yes|99|16.10.0|95.0.4629.0|385|
|[v17.0.0-nightly.20210928](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20210928)|2021-09-28||yes|99|16.10.0|95.0.4629.0|396|
|[v17.0.0-nightly.20210927](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20210927)|2021-09-27||yes|99|16.9.1|95.0.4629.0|241|
|[v17.0.0-nightly.20210924](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20210924)|2021-09-24||yes|99|16.9.1|95.0.4629.0|458|
|[v17.0.0-nightly.20210923](https://github.com/electron/electron/releases/tag/v17.0.0-nightly.20210923)|September 23, 2021||yes|99|16.9.1|95.0.4629.0|412|
|[v17.0.0-beta.9](https://github.com/electron/electron/releases/tag/v17.0.0-beta.9)|January 31, 2022|beta-17-x-y|yes|101|16.13.0|98.0.4758.11|3455|
|[v17.0.0-beta.8](https://github.com/electron/electron/releases/tag/v17.0.0-beta.8)|2022-01-27||yes|101|16.13.0|98.0.4758.11|3918|
|[v17.0.0-beta.7](https://github.com/electron/electron/releases/tag/v17.0.0-beta.7)|2022-01-24||yes|101|16.13.0|98.0.4758.11|2313|
|[v17.0.0-beta.6](https://github.com/electron/electron/releases/tag/v17.0.0-beta.6)|2022-01-21||yes|101|16.13.0|98.0.4758.11|3648|
|[v17.0.0-beta.5](https://github.com/electron/electron/releases/tag/v17.0.0-beta.5)|January 17, 2022||yes|101|16.13.0|98.0.4758.11|4027|
|[v17.0.0-beta.4](https://github.com/electron/electron/releases/tag/v17.0.0-beta.4)|2022-01-13||yes|101|16.13.0|98.0.4758.11|11786|
|[v17.0.0-beta.3](https://github.com/electron/electron/releases/tag/v17.0.0-beta.3)|2022-01-11||yes|101|16.13.0|98.0.4758.9|2670|
|[v17.0.0-beta.2](https://github.com/electron/electron/releases/tag/v17.0.0-beta.2)|2022-01-10||yes|101|16.13.0|98.0.4706.0|3019|
|[v17.0.0-beta.1](https://github.com/electron/electron/releases/tag/v17.0.0-beta.1)|January 6, 2022||yes|101|16.13.0|98.0.4706.0|2911|
|[v17.0.0-alpha.6](https://github.com/electron/electron/releases/tag/v17.0.0-alpha.6)|January 3, 2022|alpha-17-x-y|yes|101|16.13.0|98.0.4706.0|1818|
|[v17.0.0-alpha.5](https://github.com/electron/electron/releases/tag/v17.0.0-alpha.5)|December 16, 2021||yes|101|16.13.0|98.0.4706.0|1994|
|[v17.0.0-alpha.4](https://github.com/electron/electron/releases/tag/v17.0.0-alpha.4)|2021-11-25||yes|101|16.13.0|98.0.4706.0|3403|
|[v17.0.0-alpha.3](https://github.com/electron/electron/releases/tag/v17.0.0-alpha.3)|2021-11-22||yes|101|16.13.0|96.0.4664.4|2381|
|[v17.0.0-alpha.2](https://github.com/electron/electron/releases/tag/v17.0.0-alpha.2)|2021-11-18||yes|101|16.13.0|96.0.4664.4|2434|
|[v17.0.0-alpha.1](https://github.com/electron/electron/releases/tag/v17.0.0-alpha.1)|2021-11-17||yes|101|16.13.0|96.0.4664.4|2202|
|[v16.2.8](https://github.com/electron/electron/releases/tag/v16.2.8)|2022-05-24|16-x-y|no|99|16.9.1|96.0.4664.174|174841|
|[v16.2.7](https://github.com/electron/electron/releases/tag/v16.2.7)|2022-05-18||no|99|16.9.1|96.0.4664.174|28527|
|[v16.2.6](https://github.com/electron/electron/releases/tag/v16.2.6)|2022-05-11||no|99|16.9.1|96.0.4664.174|30586|
|[v16.2.5](https://github.com/electron/electron/releases/tag/v16.2.5)|May 4, 2022||no|99|16.9.1|96.0.4664.174|30470|
|[v16.2.4](https://github.com/electron/electron/releases/tag/v16.2.4)|April 28, 2022||no|99|16.9.1|96.0.4664.174|10658|
|[v16.2.3](https://github.com/electron/electron/releases/tag/v16.2.3)|April 20, 2022||no|99|16.9.1|96.0.4664.174|20401|
|[v16.2.2](https://github.com/electron/electron/releases/tag/v16.2.2)|April 6, 2022||no|99|16.9.1|96.0.4664.174|45305|
|[v16.2.1](https://github.com/electron/electron/releases/tag/v16.2.1)|March 30, 2022||no|99|16.9.1|96.0.4664.174|21168|
|[v16.2.0](https://github.com/electron/electron/releases/tag/v16.2.0)|2022-03-28||no|99|16.9.1|96.0.4664.174|16288|
|[v16.1.1](https://github.com/electron/electron/releases/tag/v16.1.1)|2022-03-23||no|99|16.9.1|96.0.4664.174|23963|
|[v16.1.0](https://github.com/electron/electron/releases/tag/v16.1.0)|2022-03-09||no|99|16.9.1|96.0.4664.174|64613|
|[v16.0.10](https://github.com/electron/electron/releases/tag/v16.0.10)|February 23, 2022||no|99|16.9.1|96.0.4664.174|60336|
|[v16.0.9](https://github.com/electron/electron/releases/tag/v16.0.9)|2022-02-15||no|99|16.9.1|96.0.4664.174|127331|
|[v16.0.8](https://github.com/electron/electron/releases/tag/v16.0.8)|2022-01-27||no|99|16.9.1|96.0.4664.110|189744|
|[v16.0.7](https://github.com/electron/electron/releases/tag/v16.0.7)|2022-01-11||no|99|16.9.1|96.0.4664.110|262127|
|[v16.0.6](https://github.com/electron/electron/releases/tag/v16.0.6)|January 3, 2022||no|99|16.9.1|96.0.4664.110|288296|
|[v16.0.5](https://github.com/electron/electron/releases/tag/v16.0.5)|2021-12-17||no|99|16.9.1|96.0.4664.55|277691|
|[v16.0.4](https://github.com/electron/electron/releases/tag/v16.0.4)|2021-12-03||no|99|16.9.1|96.0.4664.55|228707|
|[v16.0.3](https://github.com/electron/electron/releases/tag/v16.0.3)|2021-11-30||no|99|16.9.1|96.0.4664.55|55321|
|[v16.0.2](https://github.com/electron/electron/releases/tag/v16.0.2)|2021-11-24||no|99|16.9.1|96.0.4664.55|157544|
|[v16.0.1](https://github.com/electron/electron/releases/tag/v16.0.1)|2021-11-18||no|99|16.9.1|96.0.4664.45|91021|
|[v16.0.0](https://github.com/electron/electron/releases/tag/v16.0.0)|2021-11-16||no|99|16.9.1|96.0.4664.45|105120|
|[v16.0.0-nightly.20210922](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210922)|2021-09-22||yes|99|16.9.1|95.0.4629.0|459|
|[v16.0.0-nightly.20210921](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210921)|2021-09-21||yes|99|16.9.1|95.0.4629.0|414|
|[v16.0.0-nightly.20210920](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210920)|2021-09-20||yes|99|16.9.1|95.0.4629.0|420|
|[v16.0.0-nightly.20210917](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210917)|2021-09-17||yes|99|16.9.1|95.0.4629.0|476|
|[v16.0.0-nightly.20210916](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210916)|2021-09-16||yes|99|16.9.1|95.0.4629.0|423|
|[v16.0.0-nightly.20210915](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210915)|2021-09-15||yes|89|16.9.0|95.0.4629.0|406|
|[v16.0.0-nightly.20210914](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210914)|2021-09-15||yes|89|16.9.0|95.0.4629.0|397|
|[v16.0.0-nightly.20210913](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210913)|2021-09-13||yes|89|16.9.0|95.0.4629.0|506|
|[v16.0.0-nightly.20210910](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210910)|2021-09-10||yes|89|16.9.0|95.0.4629.0|556|
|[v16.0.0-nightly.20210909](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210909)|2021-09-09||yes|89|16.9.0|95.0.4629.0|482|
|[v16.0.0-nightly.20210908](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210908)|2021-09-08||yes|89|16.8.0|95.0.4629.0|487|
|[v16.0.0-nightly.20210907](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210907)|September 7, 2021||yes|89|16.8.0|95.0.4629.0|509|
|[v16.0.0-nightly.20210906](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210906)|September 7, 2021||yes|89|16.8.0|95.0.4629.0|475|
|[v16.0.0-nightly.20210903](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210903)|September 3, 2021||yes|89|16.8.0|95.0.4629.0|667|
|[v16.0.0-nightly.20210902](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210902)|September 3, 2021||yes|89|16.8.0|95.0.4629.0|471|
|[v16.0.0-nightly.20210901](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210901)|September 1, 2021||yes|89|16.8.0|95.0.4612.5|522|
|[v16.0.0-nightly.20210831](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210831)|2021-08-31||yes|89|16.7.0|95.0.4612.5|519|
|[v16.0.0-nightly.20210830](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210830)|2021-08-30||yes|89|16.7.0|95.0.4612.5|503|
|[v16.0.0-nightly.20210827](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210827)|2021-08-27||yes|89|16.7.0|95.0.4612.5|415|
|[v16.0.0-nightly.20210826](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210826)|2021-08-26||yes|89|16.7.0|95.0.4612.5|333|
|[v16.0.0-nightly.20210825](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210825)|2021-08-25||yes|89|16.7.0|95.0.4612.5|496|
|[v16.0.0-nightly.20210824](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210824)|August 24, 2021||yes|89|16.7.0|95.0.4612.5|515|
|[v16.0.0-nightly.20210823](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210823)|2021-08-23||yes|89|16.7.0|94.0.4590.2|1001|
|[v16.0.0-nightly.20210820](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210820)|2021-08-20||yes|89|16.5.0|94.0.4590.2|570|
|[v16.0.0-nightly.20210819](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210819)|2021-08-19||yes|89|16.5.0|94.0.4590.2|501|
|[v16.0.0-nightly.20210818](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210818)|2021-08-18||yes|89|16.5.0|94.0.4590.2|521|
|[v16.0.0-nightly.20210817](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210817)|2021-08-17||yes|89|16.5.0|94.0.4590.2|492|
|[v16.0.0-nightly.20210816](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210816)|2021-08-16||yes|89|16.5.0|94.0.4590.2|499|
|[v16.0.0-nightly.20210813](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210813)|2021-08-13||yes|89|16.5.0|94.0.4590.2|545|
|[v16.0.0-nightly.20210812](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210812)|2021-08-12||yes|89|16.5.0|94.0.4590.2|493|
|[v16.0.0-nightly.20210811](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210811)|2021-08-11||yes|89|16.5.0|94.0.4584.0|505|
|[v16.0.0-nightly.20210810](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210810)|2021-08-10||yes|89|16.5.0|94.0.4584.0|506|
|[v16.0.0-nightly.20210809](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210809)|2021-08-09||yes|89|16.5.0|94.0.4584.0|499|
|[v16.0.0-nightly.20210806](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210806)|2021-08-06||yes|89|16.5.0|94.0.4584.0|588|
|[v16.0.0-nightly.20210805](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210805)|2021-08-05||yes|89|16.5.0|94.0.4584.0|516|
|[v16.0.0-nightly.20210804](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210804)|2021-08-04||yes|89|16.5.0|94.0.4584.0|511|
|[v16.0.0-nightly.20210803](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210803)|August 3, 2021||yes|89|16.5.0|94.0.4584.0|517|
|[v16.0.0-nightly.20210802](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210802)|2021-08-02||yes|89|16.5.0|94.0.4584.0|493|
|[v16.0.0-nightly.20210730](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210730)|2021-07-30||yes|89|16.5.0|94.0.4584.0|612|
|[v16.0.0-nightly.20210729](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210729)|2021-07-29||yes|89|16.5.0|94.0.4584.0|575|
|[v16.0.0-nightly.20210728](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210728)|2021-07-28||yes|89|16.5.0|94.0.4584.0|494|
|[v16.0.0-nightly.20210727](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210727)|2021-07-27||yes|89|16.5.0|94.0.4584.0|486|
|[v16.0.0-nightly.20210726](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210726)|2021-07-26||yes|89|16.5.0|93.0.4566.0|479|
|[v16.0.0-nightly.20210723](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210723)|2021-07-23||yes|89|16.5.0|93.0.4566.0|551|
|[v16.0.0-nightly.20210722](https://github.com/electron/electron/releases/tag/v16.0.0-nightly.20210722)|2021-07-22||yes|89|16.5.0|93.0.4566.0|495|
|[v16.0.0-beta.9](https://github.com/electron/electron/releases/tag/v16.0.0-beta.9)|November 11, 2021|beta-16-x-y|yes|99|16.9.1|96.0.4664.35|4052|
|[v16.0.0-beta.8](https://github.com/electron/electron/releases/tag/v16.0.0-beta.8)|November 8, 2021||yes|99|16.9.1|96.0.4664.35|3578|
|[v16.0.0-beta.7](https://github.com/electron/electron/releases/tag/v16.0.0-beta.7)|November 4, 2021||yes|99|16.9.1|96.0.4664.27|3160|
|[v16.0.0-beta.6](https://github.com/electron/electron/releases/tag/v16.0.0-beta.6)|November 1, 2021||yes|99|16.9.1|96.0.4664.27|3690|
|[v16.0.0-beta.5](https://github.com/electron/electron/releases/tag/v16.0.0-beta.5)|2021-10-28||yes|99|16.9.1|96.0.4664.18|2497|
|[v16.0.0-beta.4](https://github.com/electron/electron/releases/tag/v16.0.0-beta.4)|2021-10-27||yes|99|16.9.1|96.0.4664.18|2253|
|[v16.0.0-beta.3](https://github.com/electron/electron/releases/tag/v16.0.0-beta.3)|2021-10-25||yes|99|16.9.1|96.0.4647.0|3203|
|[v16.0.0-beta.2](https://github.com/electron/electron/releases/tag/v16.0.0-beta.2)|2021-10-21||yes|99|16.9.1|96.0.4647.0|3437|
|[v16.0.0-beta.1](https://github.com/electron/electron/releases/tag/v16.0.0-beta.1)|2021-10-20||yes|99|16.9.1|96.0.4647.0|1937|
|[v16.0.0-alpha.9](https://github.com/electron/electron/releases/tag/v16.0.0-alpha.9)|2021-10-18|alpha-16-x-y|yes|99|16.9.1|96.0.4647.0|2713|
|[v16.0.0-alpha.8](https://github.com/electron/electron/releases/tag/v16.0.0-alpha.8)|2021-10-14||yes|99|16.9.1|96.0.4647.0|2516|
|[v16.0.0-alpha.7](https://github.com/electron/electron/releases/tag/v16.0.0-alpha.7)|2021-10-11||yes|99|16.9.1|95.0.4629.0|2139|
|[v16.0.0-alpha.6](https://github.com/electron/electron/releases/tag/v16.0.0-alpha.6)|2021-10-07||yes|99|16.9.1|95.0.4629.0|2278|
|[v16.0.0-alpha.5](https://github.com/electron/electron/releases/tag/v16.0.0-alpha.5)|October 4, 2021||yes|99|16.9.1|95.0.4629.0|3188|
|[v16.0.0-alpha.4](https://github.com/electron/electron/releases/tag/v16.0.0-alpha.4)|October 4, 2021||yes|99|16.9.1|95.0.4629.0|2530|
|[v16.0.0-alpha.3](https://github.com/electron/electron/releases/tag/v16.0.0-alpha.3)|September 30, 2021||yes|99|16.9.1|95.0.4629.0|2586|
|[v16.0.0-alpha.2](https://github.com/electron/electron/releases/tag/v16.0.0-alpha.2)|September 30, 2021||yes|99|16.9.1|95.0.4629.0|2394|
|[v16.0.0-alpha.1](https://github.com/electron/electron/releases/tag/v16.0.0-alpha.1)|September 22, 2021||yes|99|16.9.1|95.0.4629.0|3524|
|[v15.5.7](https://github.com/electron/electron/releases/tag/v15.5.7)|May 24, 2022|15-x-y|no|98|16.5.0|94.0.4606.81|477228|
|[v15.5.6](https://github.com/electron/electron/releases/tag/v15.5.6)|May 23, 2022||no|98|16.5.0|94.0.4606.81|2945|
|[v15.5.5](https://github.com/electron/electron/releases/tag/v15.5.5)|May 11, 2022||no|98|16.5.0|94.0.4606.81|107161|
|[v15.5.4](https://github.com/electron/electron/releases/tag/v15.5.4)|May 4, 2022||no|98|16.5.0|94.0.4606.81|12403|
|[v15.5.3](https://github.com/electron/electron/releases/tag/v15.5.3)|April 30, 2022||no|98|16.5.0|94.0.4606.81|9930|
|[v15.5.2](https://github.com/electron/electron/releases/tag/v15.5.2)|April 6, 2022||no|98|16.5.0|94.0.4606.81|42043|
|[v15.5.1](https://github.com/electron/electron/releases/tag/v15.5.1)|2022-03-30||no|98|16.5.0|94.0.4606.81|36558|
|[v15.5.0](https://github.com/electron/electron/releases/tag/v15.5.0)|2022-03-29||no|98|16.5.0|94.0.4606.81|4047|
|[v15.4.2](https://github.com/electron/electron/releases/tag/v15.4.2)|2022-03-23||no|98|16.5.0|94.0.4606.81|28960|
|[v15.4.1](https://github.com/electron/electron/releases/tag/v15.4.1)|2022-03-09||no|98|16.5.0|94.0.4606.81|15167|
|[v15.4.0](https://github.com/electron/electron/releases/tag/v15.4.0)|March 1, 2022||no|98|16.5.0|94.0.4606.81|14630|
|[v15.3.7](https://github.com/electron/electron/releases/tag/v15.3.7)|February 14, 2022||no|98|16.5.0|94.0.4606.81|51951|
|[v15.3.6](https://github.com/electron/electron/releases/tag/v15.3.6)|January 27, 2022||no|98|16.5.0|94.0.4606.81|88398|
|[v15.3.5](https://github.com/electron/electron/releases/tag/v15.3.5)|2022-01-11||no|98|16.5.0|94.0.4606.81|81790|
|[v15.3.4](https://github.com/electron/electron/releases/tag/v15.3.4)|2021-12-16||no|98|16.5.0|94.0.4606.81|103891|
|[v15.3.3](https://github.com/electron/electron/releases/tag/v15.3.3)|2021-11-30||no|98|16.5.0|94.0.4606.81|52041|
|[v15.3.2](https://github.com/electron/electron/releases/tag/v15.3.2)|2021-11-16||no|98|16.5.0|94.0.4606.81|91736|
|[v15.3.1](https://github.com/electron/electron/releases/tag/v15.3.1)|2021-11-08||no|98|16.5.0|94.0.4606.81|127670|
|[v15.3.0](https://github.com/electron/electron/releases/tag/v15.3.0)|2021-10-20||no|98|16.5.0|94.0.4606.81|387212|
|[v15.2.0](https://github.com/electron/electron/releases/tag/v15.2.0)|2021-10-14||no|98|16.5.0|94.0.4606.81|123674|
|[v15.1.2](https://github.com/electron/electron/releases/tag/v15.1.2)|2021-10-08||no|98|16.5.0|94.0.4606.71|110841|
|[v15.1.1](https://github.com/electron/electron/releases/tag/v15.1.1)|2021-10-04||no|98|16.5.0|94.0.4606.61|79124|
|[v15.1.0](https://github.com/electron/electron/releases/tag/v15.1.0)|October 1, 2021||no|98|16.5.0|94.0.4606.61|57160|
|[v15.0.0](https://github.com/electron/electron/releases/tag/v15.0.0)|September 21, 2021||no|98|16.5.0|94.0.4606.51|167162|
|[v15.0.0-nightly.20210721](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210721)|2021-07-21||yes|89|16.5.0|93.0.4566.0|660|
|[v15.0.0-nightly.20210720](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210720)|2021-07-20||yes|89|16.5.0|93.0.4566.0|510|
|[v15.0.0-nightly.20210719](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210719)|2021-07-19||yes|89|16.5.0|93.0.4566.0|499|
|[v15.0.0-nightly.20210716](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210716)|2021-07-16||yes|89|16.5.0|93.0.4566.0|563|
|[v15.0.0-nightly.20210715](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210715)|2021-07-15||yes|89|16.4.1|93.0.4566.0|497|
|[v15.0.0-nightly.20210714](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210714)|2021-07-14||yes|89|16.4.1|93.0.4566.0|494|
|[v15.0.0-nightly.20210713](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210713)|2021-07-13||yes|89|16.4.1|93.0.4566.0|491|
|[v15.0.0-nightly.20210712](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210712)|2021-07-12||yes|89|16.4.1|93.0.4566.0|489|
|[v15.0.0-nightly.20210709](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210709)|2021-07-09||yes|89|16.4.1|93.0.4566.0|523|
|[v15.0.0-nightly.20210708](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210708)|2021-07-08||yes|89|16.4.1|93.0.4566.0|474|
|[v15.0.0-nightly.20210707](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210707)|2021-07-07||yes|89|16.4.1|93.0.4566.0|466|
|[v15.0.0-nightly.20210706](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210706)|2021-07-06||yes|89|16.4.1|93.0.4566.0|487|
|[v15.0.0-nightly.20210705](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210705)|2021-07-05||yes|89|16.4.0|93.0.4558.0|478|
|[v15.0.0-nightly.20210702](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210702)|2021-07-02||yes|89|16.4.0|93.0.4558.0|581|
|[v15.0.0-nightly.20210701](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210701)|July 1, 2021||yes|89|16.4.0|93.0.4558.0|556|
|[v15.0.0-nightly.20210630](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210630)|2021-06-30||yes|89|16.4.0|93.0.4558.0|486|
|[v15.0.0-nightly.20210629](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210629)|2021-06-29||yes|89|16.4.0|93.0.4552.0|485|
|[v15.0.0-nightly.20210628](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210628)|2021-06-28||yes|89|16.2.0|93.0.4552.0|483|
|[v15.0.0-nightly.20210625](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210625)|2021-06-25||yes|89|16.2.0|93.0.4552.0|546|
|[v15.0.0-nightly.20210624](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210624)|2021-06-24||yes|89|16.2.0|93.0.4550.0|497|
|[v15.0.0-nightly.20210623](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210623)|2021-06-23||yes|89|16.2.0|93.0.4550.0|489|
|[v15.0.0-nightly.20210622](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210622)|2021-06-22||yes|89|16.2.0|93.0.4539.0|460|
|[v15.0.0-nightly.20210621](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210621)|2021-06-21||yes|89|16.2.0|93.0.4539.0|513|
|[v15.0.0-nightly.20210618](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210618)|2021-06-18||yes|89|16.2.0|93.0.4539.0|590|
|[v15.0.0-nightly.20210617](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210617)|2021-06-17||yes|89|16.2.0|93.0.4539.0|471|
|[v15.0.0-nightly.20210616](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210616)|2021-06-16||yes|89|14.17.0|93.0.4536.0|496|
|[v15.0.0-nightly.20210615](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210615)|2021-06-15||yes|89|14.17.0|93.0.4536.0|406|
|[v15.0.0-nightly.20210614](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210614)|2021-06-14||yes|89|14.17.0|93.0.4536.0|474|
|[v15.0.0-nightly.20210611](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210611)|2021-06-11||yes|89|14.17.0|93.0.4536.0|548|
|[v15.0.0-nightly.20210610](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210610)|2021-06-10||yes|89|14.17.0|93.0.4536.0|476|
|[v15.0.0-nightly.20210609](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210609)|2021-06-09||yes|89|14.17.0|93.0.4536.0|488|
|[v15.0.0-nightly.20210608](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210608)|2021-06-08||yes|89|14.17.0|93.0.4535.0|452|
|[v15.0.0-nightly.20210604](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210604)|2021-06-04||yes|89|14.17.0|93.0.4530.0|572|
|[v15.0.0-nightly.20210603](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210603)|June 3, 2021||yes|89|14.17.0|93.0.4530.0|471|
|[v15.0.0-nightly.20210602](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210602)|June 2, 2021||yes|89|14.17.0|92.0.4511.0|501|
|[v15.0.0-nightly.20210601](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210601)|June 1, 2021||yes|89|14.17.0|92.0.4511.0|453|
|[v15.0.0-nightly.20210531](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210531)|May 31, 2021||yes|89|14.17.0|92.0.4511.0|506|
|[v15.0.0-nightly.20210528](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210528)|May 28, 2021||yes|89|14.17.0|92.0.4511.0|352|
|[v15.0.0-nightly.20210527](https://github.com/electron/electron/releases/tag/v15.0.0-nightly.20210527)|May 27, 2021||yes|89|14.17.0|92.0.4511.0|515|
|[v15.0.0-beta.7](https://github.com/electron/electron/releases/tag/v15.0.0-beta.7)|2021-09-16|beta-15-x-y|yes|98|16.5.0|94.0.4606.31|3386|
|[v15.0.0-beta.6](https://github.com/electron/electron/releases/tag/v15.0.0-beta.6)|2021-09-15||yes|89|16.5.0|94.0.4606.31|4003|
|[v15.0.0-beta.5](https://github.com/electron/electron/releases/tag/v15.0.0-beta.5)|2021-09-13||yes|89|16.5.0|94.0.4606.31|2210|
|[v15.0.0-beta.4](https://github.com/electron/electron/releases/tag/v15.0.0-beta.4)|2021-09-09||yes|89|16.5.0|94.0.4606.31|2941|
|[v15.0.0-beta.3](https://github.com/electron/electron/releases/tag/v15.0.0-beta.3)|2021-09-07||yes|89|16.5.0|94.0.4606.31|4038|
|[v15.0.0-beta.2](https://github.com/electron/electron/releases/tag/v15.0.0-beta.2)|September 2, 2021||yes|89|16.5.0|94.0.4606.20|4242|
|[v15.0.0-beta.1](https://github.com/electron/electron/releases/tag/v15.0.0-beta.1)|August 31, 2021||yes|89|16.5.0|94.0.4606.20|4004|
|[v15.0.0-alpha.10](https://github.com/electron/electron/releases/tag/v15.0.0-alpha.10)|2021-08-26|alpha-15-x-y|yes|89|16.5.0|94.0.4606.12|2295|
|[v15.0.0-alpha.9](https://github.com/electron/electron/releases/tag/v15.0.0-alpha.9)|2021-08-23||yes|89|16.5.0|94.0.4590.2|2428|
|[v15.0.0-alpha.8](https://github.com/electron/electron/releases/tag/v15.0.0-alpha.8)|2021-08-19||yes|89|16.5.0|94.0.4590.2|2807|
|[v15.0.0-alpha.7](https://github.com/electron/electron/releases/tag/v15.0.0-alpha.7)|2021-08-17||yes|89|16.5.0|94.0.4590.2|2114|
|[v15.0.0-alpha.6](https://github.com/electron/electron/releases/tag/v15.0.0-alpha.6)|2021-08-12||yes|89|16.5.0|94.0.4584.0|2949|
|[v15.0.0-alpha.5](https://github.com/electron/electron/releases/tag/v15.0.0-alpha.5)|2021-08-09||yes|89|16.5.0|94.0.4584.0|2171|
|[v15.0.0-alpha.4](https://github.com/electron/electron/releases/tag/v15.0.0-alpha.4)|2021-08-05||yes|89|16.5.0|94.0.4584.0|2854|
|[v15.0.0-alpha.3](https://github.com/electron/electron/releases/tag/v15.0.0-alpha.3)|August 2, 2021||yes|89|16.5.0|94.0.4584.0|2504|
|[v15.0.0-alpha.2](https://github.com/electron/electron/releases/tag/v15.0.0-alpha.2)|2021-07-26||yes|89|16.5.0|93.0.4566.0|6407|
|[v15.0.0-alpha.1](https://github.com/electron/electron/releases/tag/v15.0.0-alpha.1)|2021-07-21||yes|89|16.5.0|93.0.4566.0|2479|
|[v14.2.9](https://github.com/electron/electron/releases/tag/v14.2.9)|March 30, 2022|14-x-y|no|97|14.17.0|93.0.4577.82|147771|
|[v14.2.8](https://github.com/electron/electron/releases/tag/v14.2.8)|March 24, 2022||no|97|14.17.0|93.0.4577.82|7770|
|[v14.2.7](https://github.com/electron/electron/releases/tag/v14.2.7)|March 9, 2022||no|97|14.17.0|93.0.4577.82|18796|
|[v14.2.6](https://github.com/electron/electron/releases/tag/v14.2.6)|February 15, 2022||no|97|14.17.0|93.0.4577.82|32682|
|[v14.2.5](https://github.com/electron/electron/releases/tag/v14.2.5)|January 27, 2022||no|97|14.17.0|93.0.4577.82|17055|
|[v14.2.4](https://github.com/electron/electron/releases/tag/v14.2.4)|January 11, 2022||no|97|14.17.0|93.0.4577.82|31041|
|[v14.2.3](https://github.com/electron/electron/releases/tag/v14.2.3)|December 16, 2021||no|97|14.17.0|93.0.4577.82|42284|
|[v14.2.2](https://github.com/electron/electron/releases/tag/v14.2.2)|December 1, 2021||no|97|14.17.0|93.0.4577.82|21118|
|[v14.2.1](https://github.com/electron/electron/releases/tag/v14.2.1)|November 8, 2021||no|97|14.17.0|93.0.4577.82|72163|
|[v14.2.0](https://github.com/electron/electron/releases/tag/v14.2.0)|October 20, 2021||no|97|14.17.0|93.0.4577.82|75788|
|[v14.1.1](https://github.com/electron/electron/releases/tag/v14.1.1)|October 8, 2021||no|97|14.17.0|93.0.4577.82|45515|
|[v14.1.0](https://github.com/electron/electron/releases/tag/v14.1.0)|September 30, 2021||no|97|14.17.0|93.0.4577.82|77235|
|[v14.0.2](https://github.com/electron/electron/releases/tag/v14.0.2)|September 29, 2021||no|97|14.17.0|93.0.4577.82|28330|
|[v14.0.1](https://github.com/electron/electron/releases/tag/v14.0.1)|September 13, 2021||no|89|14.17.0|93.0.4577.63|113010|
|[v14.0.0](https://github.com/electron/electron/releases/tag/v14.0.0)|August 30, 2021||no|89|14.17.0|93.0.4577.58|288077|
|[v14.0.0-nightly.20210524](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210524)|May 24, 2021||yes|89|14.17.0|92.0.4511.0|711|
|[v14.0.0-nightly.20210523](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210523)|2021-05-24||yes|89|14.17.0|92.0.4511.0|506|
|[v14.0.0-nightly.20210520](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210520)|2021-05-20||yes|89|14.17.0|92.0.4511.0|561|
|[v14.0.0-nightly.20210519](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210519)|2021-05-19||yes|89|14.16.1|92.0.4505.0|324|
|[v14.0.0-nightly.20210518](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210518)|2021-05-18||yes|89|14.16.1|92.0.4505.0|588|
|[v14.0.0-nightly.20210517](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210517)|2021-05-17||yes|89|14.16.1|92.0.4505.0|468|
|[v14.0.0-nightly.20210514](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210514)|2021-05-14||yes|89|14.16.1|92.0.4505.0|658|
|[v14.0.0-nightly.20210513](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210513)|2021-05-13||yes|89|14.16.1|92.0.4499.0|465|
|[v14.0.0-nightly.20210512](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210512)|2021-05-12||yes|89|14.16.1|92.0.4499.0|477|
|[v14.0.0-nightly.20210511](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210511)|2021-05-11||yes|89|14.16.1|92.0.4499.0|479|
|[v14.0.0-nightly.20210510](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210510)|2021-05-10||yes|89|14.16.1|92.0.4499.0|469|
|[v14.0.0-nightly.20210507](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210507)|2021-05-07||yes|89|14.16.1|92.0.4499.0|536|
|[v14.0.0-nightly.20210506](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210506)|2021-05-06||yes|89|14.16.1|92.0.4498.0|484|
|[v14.0.0-nightly.20210505](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210505)|May 5, 2021||yes|89|14.16.1|92.0.4496.0|477|
|[v14.0.0-nightly.20210503](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210503)|2021-05-04||yes|89|14.16.1|92.0.4488.0|522|
|[v14.0.0-nightly.20210430](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210430)|2021-04-30||yes|89|14.16.1|92.0.4488.0|475|
|[v14.0.0-nightly.20210427](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210427)|2021-04-27||yes|89|14.16.1|92.0.4475.0|561|
|[v14.0.0-nightly.20210426](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210426)|2021-04-26||yes|89|14.16.1|92.0.4475.0|504|
|[v14.0.0-nightly.20210413](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210413)|2021-04-13||yes|89|14.16.1|91.0.4448.0|862|
|[v14.0.0-nightly.20210409](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210409)|2021-04-09||yes|89|14.16.1|91.0.4448.0|636|
|[v14.0.0-nightly.20210408](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210408)|2021-04-08||yes|89|14.16.1|91.0.4448.0|507|
|[v14.0.0-nightly.20210407](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210407)|2021-04-07||yes|89|14.16.0|91.0.4448.0|516|
|[v14.0.0-nightly.20210406](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210406)|2021-04-06||yes|89|14.16.0|91.0.4448.0|542|
|[v14.0.0-nightly.20210402](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210402)|2021-04-02||yes|89|14.16.0|91.0.4448.0|588|
|[v14.0.0-nightly.20210401](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210401)|April 1, 2021||yes|89|14.16.0|91.0.4448.0|594|
|[v14.0.0-nightly.20210331](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210331)|March 31, 2021||yes|89|14.16.0|91.0.4448.0|460|
|[v14.0.0-nightly.20210330](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210330)|2021-03-30||yes|89|14.16.0|90.0.4415.0|508|
|[v14.0.0-nightly.20210329](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210329)|2021-03-29||yes|89|14.16.0|90.0.4415.0|306|
|[v14.0.0-nightly.20210326](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210326)|2021-03-26||yes|89|14.16.0|90.0.4415.0|502|
|[v14.0.0-nightly.20210325](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210325)|2021-03-25||yes|89|14.16.0|90.0.4415.0|478|
|[v14.0.0-nightly.20210324](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210324)|2021-03-24||yes|89|14.16.0|90.0.4415.0|477|
|[v14.0.0-nightly.20210323](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210323)|2021-03-23||yes|89|14.16.0|90.0.4415.0|475|
|[v14.0.0-nightly.20210319](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210319)|2021-03-19||yes|89|14.16.0|90.0.4415.0|568|
|[v14.0.0-nightly.20210318](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210318)|2021-03-18||yes|89|14.16.0|90.0.4415.0|456|
|[v14.0.0-nightly.20210317](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210317)|2021-03-17||yes|89|14.16.0|90.0.4415.0|472|
|[v14.0.0-nightly.20210316](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210316)|2021-03-16||yes|89|14.16.0|90.0.4415.0|477|
|[v14.0.0-nightly.20210315](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210315)|2021-03-15||yes|89|14.16.0|90.0.4415.0|479|
|[v14.0.0-nightly.20210311](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210311)|2021-03-11||yes|89|14.16.0|90.0.4415.0|575|
|[v14.0.0-nightly.20210309](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210309)|2021-03-09||yes|89|14.16.0|90.0.4415.0|604|
|[v14.0.0-nightly.20210308](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210308)|2021-03-08||yes|89|14.16.0|90.0.4415.0|489|
|[v14.0.0-nightly.20210305](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210305)|2021-03-05||yes|89|14.16.0|90.0.4415.0|531|
|[v14.0.0-nightly.20210304](https://github.com/electron/electron/releases/tag/v14.0.0-nightly.20210304)|March 4, 2021||yes|89|14.16.0|90.0.4402.0|505|
|[v14.0.0-beta.25](https://github.com/electron/electron/releases/tag/v14.0.0-beta.25)|August 30, 2021|beta-14-x-y|yes|89|14.17.0|93.0.4577.51|4137|
|[v14.0.0-beta.24](https://github.com/electron/electron/releases/tag/v14.0.0-beta.24)|2021-08-26||yes|89|14.17.0|93.0.4577.51|2758|
|[v14.0.0-beta.23](https://github.com/electron/electron/releases/tag/v14.0.0-beta.23)|2021-08-19||yes|89|14.17.0|93.0.4577.25|3061|
|[v14.0.0-beta.22](https://github.com/electron/electron/releases/tag/v14.0.0-beta.22)|2021-08-17||yes|89|14.17.0|93.0.4577.25|2820|
|[v14.0.0-beta.21](https://github.com/electron/electron/releases/tag/v14.0.0-beta.21)|2021-08-12||yes|89|14.17.0|93.0.4577.15|3487|
|[v14.0.0-beta.20](https://github.com/electron/electron/releases/tag/v14.0.0-beta.20)|2021-08-09||yes|89|14.17.0|93.0.4577.15|4392|
|[v14.0.0-beta.19](https://github.com/electron/electron/releases/tag/v14.0.0-beta.19)|2021-08-05||yes|89|14.17.0|93.0.4577.15|3141|
|[v14.0.0-beta.18](https://github.com/electron/electron/releases/tag/v14.0.0-beta.18)|2021-08-02||yes|89|14.17.0|93.0.4577.15|2876|
|[v14.0.0-beta.17](https://github.com/electron/electron/releases/tag/v14.0.0-beta.17)|2021-07-26||yes|89|14.17.0|93.0.4566.0|4152|
|[v14.0.0-beta.16](https://github.com/electron/electron/releases/tag/v14.0.0-beta.16)|2021-07-22||yes|89|14.17.0|93.0.4566.0|4490|
|[v14.0.0-beta.15](https://github.com/electron/electron/releases/tag/v14.0.0-beta.15)|2021-07-20||yes|89|14.17.0|93.0.4566.0|2337|
|[v14.0.0-beta.14](https://github.com/electron/electron/releases/tag/v14.0.0-beta.14)|2021-07-15||yes|89|14.17.0|93.0.4566.0|3639|
|[v14.0.0-beta.13](https://github.com/electron/electron/releases/tag/v14.0.0-beta.13)|2021-07-12||yes|89|14.17.0|93.0.4566.0|2881|
|[v14.0.0-beta.12](https://github.com/electron/electron/releases/tag/v14.0.0-beta.12)|2021-07-05||yes|89|14.17.0|93.0.4557.4|3099|
|[v14.0.0-beta.11](https://github.com/electron/electron/releases/tag/v14.0.0-beta.11)|July 1, 2021||yes|89|14.17.0|93.0.4557.4|2793|
|[v14.0.0-beta.10](https://github.com/electron/electron/releases/tag/v14.0.0-beta.10)|2021-06-28||yes|89|14.17.0|93.0.4539.0|2554|
|[v14.0.0-beta.9](https://github.com/electron/electron/releases/tag/v14.0.0-beta.9)|2021-06-25||yes|89|14.17.0|93.0.4539.0|2527|
|[v14.0.0-beta.8](https://github.com/electron/electron/releases/tag/v14.0.0-beta.8)|2021-06-21||yes|89|14.17.0|93.0.4536.0|2393|
|[v14.0.0-beta.7](https://github.com/electron/electron/releases/tag/v14.0.0-beta.7)|2021-06-17||yes|89|14.17.0|93.0.4536.0|2413|
|[v14.0.0-beta.6](https://github.com/electron/electron/releases/tag/v14.0.0-beta.6)|2021-06-14||yes|89|14.17.0|93.0.4536.0|2317|
|[v14.0.0-beta.5](https://github.com/electron/electron/releases/tag/v14.0.0-beta.5)|2021-06-10||yes|89|14.17.0|93.0.4536.0|5893|
|[v14.0.0-beta.3](https://github.com/electron/electron/releases/tag/v14.0.0-beta.3)|June 3, 2021||yes|89|14.17.0|92.0.4511.0|5937|
|[v14.0.0-beta.2](https://github.com/electron/electron/releases/tag/v14.0.0-beta.2)|May 31, 2021||yes|89|14.17.0|92.0.4511.0|2609|
|[v14.0.0-beta.1](https://github.com/electron/electron/releases/tag/v14.0.0-beta.1)|May 26, 2021||yes|89|14.17.0|92.0.4511.0|17318|
|[v13.6.9](https://github.com/electron/electron/releases/tag/v13.6.9)|February 1, 2022|13-x-y|no|89|14.16.0|91.0.4472.164|484285|
|[v13.6.8](https://github.com/electron/electron/releases/tag/v13.6.8)|January 26, 2022||no|89|14.16.0|91.0.4472.164|32567|
|[v13.6.7](https://github.com/electron/electron/releases/tag/v13.6.7)|January 12, 2022||no|89|14.16.0|91.0.4472.164|124154|
|[v13.6.6](https://github.com/electron/electron/releases/tag/v13.6.6)|January 4, 2022||no|89|14.16.0|91.0.4472.164|152094|
|[v13.6.3](https://github.com/electron/electron/releases/tag/v13.6.3)|December 1, 2021||no|89|14.16.0|91.0.4472.164|152078|
|[v13.6.2](https://github.com/electron/electron/releases/tag/v13.6.2)|2021-11-16||no|89|14.16.0|91.0.4472.164|103474|
|[v13.6.1](https://github.com/electron/electron/releases/tag/v13.6.1)|2021-10-28||no|89|14.16.0|91.0.4472.164|156214|
|[v13.6.0](https://github.com/electron/electron/releases/tag/v13.6.0)|2021-10-21||no|89|14.16.0|91.0.4472.164|82291|
|[v13.5.2](https://github.com/electron/electron/releases/tag/v13.5.2)|2021-10-11||no|89|14.16.0|91.0.4472.164|183528|
|[v13.5.1](https://github.com/electron/electron/releases/tag/v13.5.1)|2021-09-30||no|89|14.16.0|91.0.4472.164|311984|
|[v13.5.0](https://github.com/electron/electron/releases/tag/v13.5.0)|2021-09-27||no|89|14.16.0|91.0.4472.164|71435|
|[v13.4.0](https://github.com/electron/electron/releases/tag/v13.4.0)|2021-09-13||no|89|14.16.0|91.0.4472.164|175973|
|[v13.3.0](https://github.com/electron/electron/releases/tag/v13.3.0)|August 31, 2021||no|89|14.16.0|91.0.4472.164|196830|
|[v13.2.3](https://github.com/electron/electron/releases/tag/v13.2.3)|August 27, 2021||no|89|14.16.0|91.0.4472.164|95623|
|[v13.2.2](https://github.com/electron/electron/releases/tag/v13.2.2)|August 23, 2021||no|89|14.16.0|91.0.4472.164|74854|
|[v13.2.1](https://github.com/electron/electron/releases/tag/v13.2.1)|August 17, 2021||no|89|14.16.0|91.0.4472.164|144042|
|[v13.2.0](https://github.com/electron/electron/releases/tag/v13.2.0)|August 17, 2021||no|89|14.16.0|91.0.4472.164|18943|
|[v13.1.9](https://github.com/electron/electron/releases/tag/v13.1.9)|August 10, 2021||no|89|14.16.0|91.0.4472.164|180020|
|[v13.1.8](https://github.com/electron/electron/releases/tag/v13.1.8)|August 3, 2021||no|89|14.16.0|91.0.4472.164|208531|
|[v13.1.7](https://github.com/electron/electron/releases/tag/v13.1.7)|2021-07-15||no|89|14.16.0|91.0.4472.124|351835|
|[v13.1.6](https://github.com/electron/electron/releases/tag/v13.1.6)|2021-07-05||no|89|14.16.0|91.0.4472.124|196879|
|[v13.1.5](https://github.com/electron/electron/releases/tag/v13.1.5)|July 1, 2021||no|89|14.16.0|91.0.4472.124|109619|
|[v13.1.4](https://github.com/electron/electron/releases/tag/v13.1.4)|2021-06-22||no|89|14.16.0|91.0.4472.106|234132|
|[v13.1.3](https://github.com/electron/electron/releases/tag/v13.1.3)|2021-06-21||no|89|14.16.0|91.0.4472.106|24252|
|[v13.1.2](https://github.com/electron/electron/releases/tag/v13.1.2)|2021-06-09||no|89|14.16.0|91.0.4472.77|225179|
|[v13.1.1](https://github.com/electron/electron/releases/tag/v13.1.1)|June 4, 2021||no|89|14.16.0|91.0.4472.77|65587|
|[v13.1.0](https://github.com/electron/electron/releases/tag/v13.1.0)|June 3, 2021||no|89|14.16.0|91.0.4472.77|42796|
|[v13.0.1](https://github.com/electron/electron/releases/tag/v13.0.1)|May 25, 2021||no|89|14.16.0|91.0.4472.69|133537|
|[v13.0.0](https://github.com/electron/electron/releases/tag/v13.0.0)|May 25, 2021||no|89|14.16.0|91.0.4472.69|568380|
|[v13.0.0-nightly.20210303](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20210303)|March 3, 2021||yes|89|14.16.0|90.0.4402.0|598|
|[v13.0.0-nightly.20210302](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20210302)|March 2, 2021||yes|89|14.16.0|90.0.4402.0|465|
|[v13.0.0-nightly.20210301](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20210301)|March 1, 2021||yes|89|14.16.0|90.0.4402.0|472|
|[v13.0.0-nightly.20210226](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20210226)|2021-02-26||yes|89|14.16.0|90.0.4402.0|552|
|[v13.0.0-nightly.20210225](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20210225)|2021-02-25||yes|89|14.15.4|90.0.4402.0|446|
|[v13.0.0-nightly.20210222](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20210222)|February 22, 2021||yes|89|14.15.4|90.0.4402.0|511|
|[v13.0.0-nightly.20210219](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20210219)|2021-02-19||yes|89|14.15.4|90.0.4402.0|507|
|[v13.0.0-nightly.20210218](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20210218)|2021-02-18||yes|89|14.15.4|90.0.4402.0|422|
|[v13.0.0-nightly.20210217](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20210217)|2021-02-17||yes|89|14.15.4|90.0.4402.0|420|
|[v13.0.0-nightly.20210216](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20210216)|February 16, 2021||yes|89|14.15.4|90.0.4402.0|421|
|[v13.0.0-nightly.20210212](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20210212)|2021-02-12||yes|89|14.15.4|90.0.4402.0|443|
|[v13.0.0-nightly.20210211](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20210211)|February 11, 2021||yes|89|14.15.4|90.0.4402.0|583|
|[v13.0.0-nightly.20210210](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20210210)|2021-02-10||yes|89|14.15.4|90.0.4402.0|505|
|[v13.0.0-nightly.20210209](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20210209)|2021-02-09||yes|89|14.15.4|89.0.4389.0|480|
|[v13.0.0-nightly.20210208](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20210208)|2021-02-08||yes|89|14.15.4|89.0.4389.0|452|
|[v13.0.0-nightly.20210205](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20210205)|2021-02-05||yes|89|14.15.4|89.0.4389.0|595|
|[v13.0.0-nightly.20210203](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20210203)|2021-02-03||yes|89|14.15.4|89.0.4389.0|517|
|[v13.0.0-nightly.20210202](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20210202)|2021-02-02||yes|89|14.15.4|89.0.4389.0|479|
|[v13.0.0-nightly.20210201](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20210201)|February 1, 2021||yes|89|14.15.4|89.0.4389.0|479|
|[v13.0.0-nightly.20210129](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20210129)|2021-01-29||yes|89|14.15.4|89.0.4389.0|570|
|[v13.0.0-nightly.20210128](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20210128)|2021-01-28||yes|89|14.15.4|89.0.4389.0|480|
|[v13.0.0-nightly.20210127](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20210127)|2021-01-27||yes|89|14.15.4|89.0.4389.0|467|
|[v13.0.0-nightly.20210125](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20210125)|2021-01-25||yes|89|14.15.4|89.0.4386.0|524|
|[v13.0.0-nightly.20210122](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20210122)|2021-01-22||yes|89|14.15.4|89.0.4386.0|537|
|[v13.0.0-nightly.20210118](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20210118)|2021-01-18||yes|89|14.15.4|89.0.4386.0|581|
|[v13.0.0-nightly.20210114](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20210114)|2021-01-14||yes|89|14.15.4|89.0.4386.0|798|
|[v13.0.0-nightly.20210113](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20210113)|2021-01-13||yes|89|14.15.4|89.0.4386.0|485|
|[v13.0.0-nightly.20210111](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20210111)|2021-01-11||yes|89|14.15.4|89.0.4359.0|518|
|[v13.0.0-nightly.20210108](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20210108)|January 8, 2021||yes|89|14.15.4|89.0.4359.0|549|
|[v13.0.0-nightly.20210104](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20210104)|January 4, 2021||yes|89|14.15.2|89.0.4359.0|563|
|[v13.0.0-nightly.20201223](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20201223)|2020-12-23||yes|89|14.15.2|89.0.4359.0|935|
|[v13.0.0-nightly.20201222](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20201222)|2020-12-22||yes|89|14.15.2|89.0.4349.0|582|
|[v13.0.0-nightly.20201221](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20201221)|2020-12-21||yes|89|14.15.2|89.0.4349.0|574|
|[v13.0.0-nightly.20201216](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20201216)|2020-12-16||yes|89|14.15.1|89.0.4349.0|678|
|[v13.0.0-nightly.20201215](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20201215)|2020-12-15||yes|89|14.15.1|89.0.4349.0|543|
|[v13.0.0-nightly.20201214](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20201214)|2020-12-14||yes|89|14.15.1|89.0.4328.0|546|
|[v13.0.0-nightly.20201211](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20201211)|2020-12-11||yes|89|14.15.1|89.0.4328.0|619|
|[v13.0.0-nightly.20201210](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20201210)|2020-12-10||yes|89|14.15.1|89.0.4328.0|555|
|[v13.0.0-nightly.20201209](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20201209)|2020-12-09||yes|89|14.15.1|89.0.4328.0|557|
|[v13.0.0-nightly.20201208](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20201208)|2020-12-08||yes|89|14.15.1|89.0.4328.0|551|
|[v13.0.0-nightly.20201207](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20201207)|2020-12-07||yes|89|14.15.1|89.0.4328.0|461|
|[v13.0.0-nightly.20201204](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20201204)|2020-12-04||yes|89|14.15.1|89.0.4328.0|499|
|[v13.0.0-nightly.20201203](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20201203)|2020-12-03||yes|89|14.15.1|89.0.4328.0|536|
|[v13.0.0-nightly.20201202](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20201202)|2020-12-02||yes|89|14.15.1|89.0.4328.0|537|
|[v13.0.0-nightly.20201201](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20201201)|December 1, 2020||yes|89|14.15.1|89.0.4328.0|549|
|[v13.0.0-nightly.20201130](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20201130)|November 30, 2020||yes|89|14.15.1|89.0.4328.0|671|
|[v13.0.0-nightly.20201127](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20201127)|November 27, 2020||yes|89|14.15.1|89.0.4328.0|737|
|[v13.0.0-nightly.20201126](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20201126)|November 26, 2020||yes|89|14.15.1|89.0.4328.0|678|
|[v13.0.0-nightly.20201124](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20201124)|November 24, 2020||yes|89|14.15.1|89.0.4328.0|699|
|[v13.0.0-nightly.20201123](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20201123)|November 23, 2020||yes|87|14.15.1|89.0.4328.0|683|
|[v13.0.0-nightly.20201119](https://github.com/electron/electron/releases/tag/v13.0.0-nightly.20201119)|November 19, 2020||yes|87|14.15.1|89.0.4328.0|753|
|[v13.0.0-beta.28](https://github.com/electron/electron/releases/tag/v13.0.0-beta.28)|2021-05-20|beta-13-x-y|yes|89|14.16.0|91.0.4472.38|2381|
|[v13.0.0-beta.27](https://github.com/electron/electron/releases/tag/v13.0.0-beta.27)|2021-05-17||yes|89|14.16.0|91.0.4472.38|6395|
|[v13.0.0-beta.26](https://github.com/electron/electron/releases/tag/v13.0.0-beta.26)|2021-05-13||yes|89|14.16.0|91.0.4472.38|2491|
|[v13.0.0-beta.24](https://github.com/electron/electron/releases/tag/v13.0.0-beta.24)|2021-05-11||yes|89|14.16.0|91.0.4472.38|3149|
|[v13.0.0-beta.23](https://github.com/electron/electron/releases/tag/v13.0.0-beta.23)|2021-05-07||yes|89|14.16.0|91.0.4472.33|2181|
|[v13.0.0-beta.22](https://github.com/electron/electron/releases/tag/v13.0.0-beta.22)|2021-05-06||yes|89|14.16.0|91.0.4472.33|1697|
|[v13.0.0-beta.21](https://github.com/electron/electron/releases/tag/v13.0.0-beta.21)|May 5, 2021||yes|89|14.16.0|91.0.4472.33|3236|
|[v13.0.0-beta.20](https://github.com/electron/electron/releases/tag/v13.0.0-beta.20)|2021-05-04||yes|89|14.16.0|91.0.4448.0|2051|
|[v13.0.0-beta.18](https://github.com/electron/electron/releases/tag/v13.0.0-beta.18)|2021-04-26||yes|89|14.16.0|91.0.4448.0|3298|
|[v13.0.0-beta.17](https://github.com/electron/electron/releases/tag/v13.0.0-beta.17)|2021-04-22||yes|89|14.16.0|91.0.4448.0|2011|
|[v13.0.0-beta.16](https://github.com/electron/electron/releases/tag/v13.0.0-beta.16)|2021-04-20||yes|89|14.16.0|91.0.4448.0|1841|
|[v13.0.0-beta.14](https://github.com/electron/electron/releases/tag/v13.0.0-beta.14)|2021-04-14||yes|89|14.16.0|91.0.4448.0|2496|
|[v13.0.0-beta.13](https://github.com/electron/electron/releases/tag/v13.0.0-beta.13)|2021-04-12||yes|89|14.16.0|90.0.4415.0|2222|
|[v13.0.0-beta.12](https://github.com/electron/electron/releases/tag/v13.0.0-beta.12)|2021-04-08||yes|89|14.16.0|90.0.4415.0|10560|
|[v13.0.0-beta.11](https://github.com/electron/electron/releases/tag/v13.0.0-beta.11)|2021-04-05||yes|89|14.16.0|90.0.4415.0|2023|
|[v13.0.0-beta.9](https://github.com/electron/electron/releases/tag/v13.0.0-beta.9)|2021-03-29||yes|89|14.16.0|90.0.4415.0|2396|
|[v13.0.0-beta.8](https://github.com/electron/electron/releases/tag/v13.0.0-beta.8)|2021-03-25||yes|89|14.16.0|90.0.4415.0|3266|
|[v13.0.0-beta.7](https://github.com/electron/electron/releases/tag/v13.0.0-beta.7)|2021-03-22||yes|89|14.16.0|90.0.4415.0|1946|
|[v13.0.0-beta.6](https://github.com/electron/electron/releases/tag/v13.0.0-beta.6)|2021-03-18||yes|89|14.16.0|90.0.4415.0|1975|
|[v13.0.0-beta.5](https://github.com/electron/electron/releases/tag/v13.0.0-beta.5)|2021-03-15||yes|89|14.16.0|90.0.4415.0|2161|
|[v13.0.0-beta.4](https://github.com/electron/electron/releases/tag/v13.0.0-beta.4)|2021-03-11||yes|89|14.16.0|90.0.4415.0|3574|
|[v13.0.0-beta.3](https://github.com/electron/electron/releases/tag/v13.0.0-beta.3)|2021-03-08||yes|89|14.16.0|90.0.4402.0|2029|
|[v13.0.0-beta.2](https://github.com/electron/electron/releases/tag/v13.0.0-beta.2)|March 5, 2021||yes|89|14.16.0|90.0.4402.0|1840|
|[v12.2.3](https://github.com/electron/electron/releases/tag/v12.2.3)|November 15, 2021|12-x-y|no|87|14.16.0|89.0.4389.128|951992|
|[v12.2.2](https://github.com/electron/electron/releases/tag/v12.2.2)|October 11, 2021||no|87|14.16.0|89.0.4389.128|151131|
|[v12.2.1](https://github.com/electron/electron/releases/tag/v12.2.1)|September 30, 2021||no|87|14.16.0|89.0.4389.128|152742|
|[v12.2.0](https://github.com/electron/electron/releases/tag/v12.2.0)|September 28, 2021||no|87|14.16.0|89.0.4389.128|24734|
|[v12.1.2](https://github.com/electron/electron/releases/tag/v12.1.2)|September 20, 2021||no|87|14.16.0|89.0.4389.128|35529|
|[v12.1.1](https://github.com/electron/electron/releases/tag/v12.1.1)|September 13, 2021||no|87|14.16.0|89.0.4389.128|36655|
|[v12.1.0](https://github.com/electron/electron/releases/tag/v12.1.0)|August 31, 2021||no|87|14.16.0|89.0.4389.128|147444|
|[v12.0.18](https://github.com/electron/electron/releases/tag/v12.0.18)|2021-08-27||no|87|14.16.0|89.0.4389.128|21067|
|[v12.0.17](https://github.com/electron/electron/releases/tag/v12.0.17)|2021-08-18||no|87|14.16.0|89.0.4389.128|51102|
|[v12.0.16](https://github.com/electron/electron/releases/tag/v12.0.16)|August 3, 2021||no|87|14.16.0|89.0.4389.128|89341|
|[v12.0.15](https://github.com/electron/electron/releases/tag/v12.0.15)|2021-07-15||no|87|14.16.0|89.0.4389.128|71808|
|[v12.0.14](https://github.com/electron/electron/releases/tag/v12.0.14)|2021-07-06||no|87|14.16.0|89.0.4389.128|50402|
|[v12.0.13](https://github.com/electron/electron/releases/tag/v12.0.13)|2021-06-29||no|87|14.16.0|89.0.4389.128|115088|
|[v12.0.12](https://github.com/electron/electron/releases/tag/v12.0.12)|2021-06-21||no|87|14.16.0|89.0.4389.128|64049|
|[v12.0.11](https://github.com/electron/electron/releases/tag/v12.0.11)|2021-06-09||no|87|14.16.0|89.0.4389.128|84889|
|[v12.0.10](https://github.com/electron/electron/releases/tag/v12.0.10)|2021-06-03||no|87|14.16.0|89.0.4389.128|42448|
|[v12.0.9](https://github.com/electron/electron/releases/tag/v12.0.9)|May 19, 2021||no|87|14.16.0|89.0.4389.128|220787|
|[v12.0.8](https://github.com/electron/electron/releases/tag/v12.0.8)|May 17, 2021||no|87|14.16.0|89.0.4389.128|84767|
|[v12.0.7](https://github.com/electron/electron/releases/tag/v12.0.7)|May 7, 2021||no|87|14.16.0|89.0.4389.128|218702|
|[v12.0.6](https://github.com/electron/electron/releases/tag/v12.0.6)|April 30, 2021||no|87|14.16.0|89.0.4389.128|183825|
|[v12.0.5](https://github.com/electron/electron/releases/tag/v12.0.5)|April 21, 2021||no|87|14.16.0|89.0.4389.128|248933|
|[v12.0.4](https://github.com/electron/electron/releases/tag/v12.0.4)|April 13, 2021||no|87|14.16.0|89.0.4389.114|222573|
|[v12.0.3](https://github.com/electron/electron/releases/tag/v12.0.3)|April 13, 2021||no|87|14.16.0|89.0.4389.114|81422|
|[v12.0.2](https://github.com/electron/electron/releases/tag/v12.0.2)|March 24, 2021||no|87|14.16.0|89.0.4389.90|367074|
|[v12.0.1](https://github.com/electron/electron/releases/tag/v12.0.1)|March 10, 2021||no|87|14.16.0|89.0.4389.82|253290|
|[v12.0.0](https://github.com/electron/electron/releases/tag/v12.0.0)|March 2, 2021||no|87|14.16.0|89.0.4389.69|671233|
|[v12.0.0-nightly.20201116](https://github.com/electron/electron/releases/tag/v12.0.0-nightly.20201116)|2020-11-17||yes|87|14.15.0|88.0.4324.0|1138|
|[v12.0.0-nightly.20201112](https://github.com/electron/electron/releases/tag/v12.0.0-nightly.20201112)|2020-11-12||yes|87|14.15.0|88.0.4306.0|854|
|[v12.0.0-nightly.20201111](https://github.com/electron/electron/releases/tag/v12.0.0-nightly.20201111)|November 11, 2020||yes|87|14.15.0|88.0.4306.0|688|
|[v12.0.0-nightly.20201106](https://github.com/electron/electron/releases/tag/v12.0.0-nightly.20201106)|2020-11-06||yes|87|14.15.0|88.0.4306.0|815|
|[v12.0.0-nightly.20201105](https://github.com/electron/electron/releases/tag/v12.0.0-nightly.20201105)|2020-11-05||yes|87|14.15.0|88.0.4306.0|680|
|[v12.0.0-nightly.20201104](https://github.com/electron/electron/releases/tag/v12.0.0-nightly.20201104)|2020-11-04||yes|87|14.15.0|88.0.4306.0|713|
|[v12.0.0-nightly.20201103](https://github.com/electron/electron/releases/tag/v12.0.0-nightly.20201103)|2020-11-03||yes|87|14.15.0|88.0.4306.0|674|
|[v12.0.0-nightly.20201102](https://github.com/electron/electron/releases/tag/v12.0.0-nightly.20201102)|2020-11-02||yes|87|14.15.0|88.0.4306.0|695|
|[v12.0.0-nightly.20201030](https://github.com/electron/electron/releases/tag/v12.0.0-nightly.20201030)|2020-10-30||yes|87|14.15.0|88.0.4306.0|651|
|[v12.0.0-nightly.20201026](https://github.com/electron/electron/releases/tag/v12.0.0-nightly.20201026)|2020-10-26||yes|87|14.14.0|88.0.4292.0|868|
|[v12.0.0-nightly.20201023](https://github.com/electron/electron/releases/tag/v12.0.0-nightly.20201023)|2020-10-23||yes|87|14.14.0|88.0.4292.0|739|
|[v12.0.0-nightly.20201015](https://github.com/electron/electron/releases/tag/v12.0.0-nightly.20201015)|2020-10-15||yes|87|14.13.1|87.0.4268.0|879|
|[v12.0.0-nightly.20201014](https://github.com/electron/electron/releases/tag/v12.0.0-nightly.20201014)|2020-10-14||yes|87|14.13.1|87.0.4268.0|689|
|[v12.0.0-nightly.20201013](https://github.com/electron/electron/releases/tag/v12.0.0-nightly.20201013)|2020-10-13||yes|87|14.13.1|87.0.4268.0|692|
|[v12.0.0-nightly.20200914](https://github.com/electron/electron/releases/tag/v12.0.0-nightly.20200914)|2020-09-14||yes|82|12.18.3|86.0.4234.0|1532|
|[v12.0.0-nightly.20200911](https://github.com/electron/electron/releases/tag/v12.0.0-nightly.20200911)|September 11, 2020||yes|82|12.18.3|86.0.4234.0|655|
|[v12.0.0-nightly.20200910](https://github.com/electron/electron/releases/tag/v12.0.0-nightly.20200910)|2020-09-10||yes|82|12.18.3|86.0.4234.0|773|
|[v12.0.0-nightly.20200907](https://github.com/electron/electron/releases/tag/v12.0.0-nightly.20200907)|2020-09-07||yes|82|12.18.3|86.0.4234.0|660|
|[v12.0.0-nightly.20200903](https://github.com/electron/electron/releases/tag/v12.0.0-nightly.20200903)|2020-09-03||yes|82|12.18.3|86.0.4234.0|952|
|[v12.0.0-nightly.20200902](https://github.com/electron/electron/releases/tag/v12.0.0-nightly.20200902)|2020-09-02||yes|82|12.18.3|86.0.4234.0|677|
|[v12.0.0-nightly.20200831](https://github.com/electron/electron/releases/tag/v12.0.0-nightly.20200831)|August 31, 2020||yes|82|12.18.3|86.0.4234.0|714|
|[v12.0.0-nightly.20200827](https://github.com/electron/electron/releases/tag/v12.0.0-nightly.20200827)|August 27, 2020||yes|82|12.18.3|86.0.4234.0|754|
|[v12.0.0-beta.31](https://github.com/electron/electron/releases/tag/v12.0.0-beta.31)|March 1, 2021|beta-12-x-y|yes|87|14.16.0|89.0.4389.58|2453|
|[v12.0.0-beta.30](https://github.com/electron/electron/releases/tag/v12.0.0-beta.30)|2021-02-25||yes|87|14.15.1|89.0.4389.58|3434|
|[v12.0.0-beta.29](https://github.com/electron/electron/releases/tag/v12.0.0-beta.29)|2021-02-23||yes|87|14.15.1|89.0.4389.23|2207|
|[v12.0.0-beta.28](https://github.com/electron/electron/releases/tag/v12.0.0-beta.28)|2021-02-22||yes|87|14.15.1|89.0.4389.23|3529|
|[v12.0.0-beta.27](https://github.com/electron/electron/releases/tag/v12.0.0-beta.27)|2021-02-19||yes|87|14.15.1|89.0.4389.23|4462|
|[v12.0.0-beta.26](https://github.com/electron/electron/releases/tag/v12.0.0-beta.26)|2021-02-15||yes|87|14.15.1|89.0.4388.2|6695|
|[v12.0.0-beta.25](https://github.com/electron/electron/releases/tag/v12.0.0-beta.25)|2021-02-11||yes|87|14.15.1|89.0.4388.2|4623|
|[v12.0.0-beta.24](https://github.com/electron/electron/releases/tag/v12.0.0-beta.24)|February 9, 2021||yes|87|14.15.1|89.0.4388.2|5980|
|[v12.0.0-beta.23](https://github.com/electron/electron/releases/tag/v12.0.0-beta.23)|February 9, 2021||yes|87|14.15.1|89.0.4388.2|1921|
|[v12.0.0-beta.22](https://github.com/electron/electron/releases/tag/v12.0.0-beta.22)|2021-02-04||yes|87|14.15.1|89.0.4388.2|3887|
|[v12.0.0-beta.21](https://github.com/electron/electron/releases/tag/v12.0.0-beta.21)|2021-02-03||yes|87|14.15.1|89.0.4388.2|4711|
|[v12.0.0-beta.20](https://github.com/electron/electron/releases/tag/v12.0.0-beta.20)|February 1, 2021||yes|87|14.15.1|89.0.4348.1|3106|
|[v12.0.0-beta.19](https://github.com/electron/electron/releases/tag/v12.0.0-beta.19)|January 28, 2021||yes|87|14.15.1|89.0.4348.1|4439|
|[v12.0.0-beta.18](https://github.com/electron/electron/releases/tag/v12.0.0-beta.18)|January 25, 2021||yes|87|14.15.1|89.0.4348.1|4589|
|[v12.0.0-beta.16](https://github.com/electron/electron/releases/tag/v12.0.0-beta.16)|January 18, 2021||yes|87|14.15.1|89.0.4348.1|5450|
|[v12.0.0-beta.14](https://github.com/electron/electron/releases/tag/v12.0.0-beta.14)|January 11, 2021||yes|87|14.15.1|89.0.4328.0|15297|
|[v12.0.0-beta.12](https://github.com/electron/electron/releases/tag/v12.0.0-beta.12)|2020-12-21||yes|87|14.15.1|89.0.4328.0|4601|
|[v12.0.0-beta.11](https://github.com/electron/electron/releases/tag/v12.0.0-beta.11)|2020-12-17||yes|87|14.15.1|89.0.4328.0|4533|
|[v12.0.0-beta.10](https://github.com/electron/electron/releases/tag/v12.0.0-beta.10)|2020-12-14||yes|87|14.15.1|89.0.4328.0|2860|
|[v12.0.0-beta.9](https://github.com/electron/electron/releases/tag/v12.0.0-beta.9)|2020-12-11||yes|87|14.15.1|89.0.4328.0|4653|
|[v12.0.0-beta.8](https://github.com/electron/electron/releases/tag/v12.0.0-beta.8)|2020-12-10||yes|87|14.15.1|89.0.4328.0|1882|
|[v12.0.0-beta.7](https://github.com/electron/electron/releases/tag/v12.0.0-beta.7)|2020-12-07||yes|87|14.15.1|89.0.4328.0|4877|
|[v12.0.0-beta.6](https://github.com/electron/electron/releases/tag/v12.0.0-beta.6)|December 3, 2020||yes|87|14.15.1|89.0.4328.0|4887|
|[v12.0.0-beta.5](https://github.com/electron/electron/releases/tag/v12.0.0-beta.5)|2020-11-30||yes|87|14.15.1|89.0.4328.0|2515|
|[v12.0.0-beta.4](https://github.com/electron/electron/releases/tag/v12.0.0-beta.4)|2020-11-26||yes|87|14.15.1|89.0.4328.0|3599|
|[v12.0.0-beta.3](https://github.com/electron/electron/releases/tag/v12.0.0-beta.3)|2020-11-23||yes|87|14.15.1|89.0.4328.0|2229|
|[v12.0.0-beta.1](https://github.com/electron/electron/releases/tag/v12.0.0-beta.1)|2020-11-19||yes|87|14.15.1|89.0.4328.0|2554|
|[v11.5.0](https://github.com/electron/electron/releases/tag/v11.5.0)|August 31, 2021|11-x-y|no|85|12.18.3|87.0.4280.141|2155636|
|[v11.4.12](https://github.com/electron/electron/releases/tag/v11.4.12)|August 18, 2021||no|85|12.18.3|87.0.4280.141|131479|
|[v11.4.11](https://github.com/electron/electron/releases/tag/v11.4.11)|August 3, 2021||no|85|12.18.3|87.0.4280.141|99954|
|[v11.4.10](https://github.com/electron/electron/releases/tag/v11.4.10)|July 6, 2021||no|85|12.18.3|87.0.4280.141|286959|
|[v11.4.9](https://github.com/electron/electron/releases/tag/v11.4.9)|2021-06-21||no|85|12.18.3|87.0.4280.141|212751|
|[v11.4.8](https://github.com/electron/electron/releases/tag/v11.4.8)|2021-06-03||no|85|12.18.3|87.0.4280.141|200408|
|[v11.4.7](https://github.com/electron/electron/releases/tag/v11.4.7)|2021-05-17||no|85|12.18.3|87.0.4280.141|176937|
|[v11.4.6](https://github.com/electron/electron/releases/tag/v11.4.6)|2021-05-08||no|85|12.18.3|87.0.4280.141|201175|
|[v11.4.5](https://github.com/electron/electron/releases/tag/v11.4.5)|May 5, 2021||no|85|12.18.3|87.0.4280.141|46073|
|[v11.4.4](https://github.com/electron/electron/releases/tag/v11.4.4)|2021-04-27||no|85|12.18.3|87.0.4280.141|95618|
|[v11.4.3](https://github.com/electron/electron/releases/tag/v11.4.3)|2021-04-14||no|85|12.18.3|87.0.4280.141|256717|
|[v11.4.2](https://github.com/electron/electron/releases/tag/v11.4.2)|April 2, 2021||no|85|12.18.3|87.0.4280.141|125749|
|[v11.4.1](https://github.com/electron/electron/releases/tag/v11.4.1)|2021-03-23||no|85|12.18.3|87.0.4280.141|98160|
|[v11.4.0](https://github.com/electron/electron/releases/tag/v11.4.0)|2021-03-23|origin/11-x-y|no|85|12.18.3|87.0.4280.141|10563|
|[v11.3.0](https://github.com/electron/electron/releases/tag/v11.3.0)|2021-02-19||no|85|12.18.3|87.0.4280.141|615640|
|[v11.2.3](https://github.com/electron/electron/releases/tag/v11.2.3)|2021-02-06||no|85|12.18.3|87.0.4280.141|422252|
|[v11.2.2](https://github.com/electron/electron/releases/tag/v11.2.2)|February 2, 2021||no|85|12.18.3|87.0.4280.141|125015|
|[v11.2.1](https://github.com/electron/electron/releases/tag/v11.2.1)|January 23, 2021||no|85|12.18.3|87.0.4280.141|278254|
|[v11.2.0](https://github.com/electron/electron/releases/tag/v11.2.0)|January 13, 2021||no|85|12.18.3|87.0.4280.141|744234|
|[v11.1.1](https://github.com/electron/electron/releases/tag/v11.1.1)|December 21, 2020||no|85|12.18.3|87.0.4280.88|540086|
|[v11.1.0](https://github.com/electron/electron/releases/tag/v11.1.0)|December 12, 2020||no|85|12.18.3|87.0.4280.88|387813|
|[v11.0.5](https://github.com/electron/electron/releases/tag/v11.0.5)|2020-12-11||no|85|12.18.3|87.0.4280.88|74384|
|[v11.0.4](https://github.com/electron/electron/releases/tag/v11.0.4)|2020-12-07||no|85|12.18.3|87.0.4280.67|113905|
|[v11.0.3](https://github.com/electron/electron/releases/tag/v11.0.3)|2020-11-24||no|85|12.18.3|87.0.4280.67|271714|
|[v11.0.2](https://github.com/electron/electron/releases/tag/v11.0.2)|2020-11-19||no|85|12.18.3|87.0.4280.67|78430|
|[v11.0.1](https://github.com/electron/electron/releases/tag/v11.0.1)|2020-11-17||no|85|12.18.3|87.0.4280.60|136629|
|[v11.0.0](https://github.com/electron/electron/releases/tag/v11.0.0)|2020-11-16||no|85|12.18.3|87.0.4280.60|730343|
|[v11.0.0-nightly.20200826](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200826)|2020-08-26||yes|82|12.18.3|86.0.4234.0|836|
|[v11.0.0-nightly.20200825](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200825)|2020-08-25||yes|82|12.18.3|86.0.4234.0|809|
|[v11.0.0-nightly.20200824](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200824)|2020-08-24||yes|82|12.18.3|86.0.4234.0|1008|
|[v11.0.0-nightly.20200822](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200822)|2020-08-23||yes|82|12.18.3|86.0.4234.0|531|
|[v11.0.0-nightly.20200812](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200812)|2020-08-12||yes|82|12.18.3|86.0.4209.0|5166|
|[v11.0.0-nightly.20200811](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200811)|2020-08-11||yes|82|12.18.3|86.0.4209.0|762|
|[v11.0.0-nightly.20200805](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200805)|2020-08-05||yes|82|12.18.3|86.0.4209.0|934|
|[v11.0.0-nightly.20200804](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200804)|2020-08-04||yes|82|12.18.3|86.0.4209.0|691|
|[v11.0.0-nightly.20200803](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200803)|2020-08-03||yes|82|12.18.3|86.0.4209.0|2548|
|[v11.0.0-nightly.20200731](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200731)|2020-07-31||yes|82|12.18.3|86.0.4209.0|760|
|[v11.0.0-nightly.20200730](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200730)|2020-07-30||yes|82|12.18.3|86.0.4209.0|695|
|[v11.0.0-nightly.20200729](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200729)|2020-07-29||yes|82|12.18.3|86.0.4209.0|740|
|[v11.0.0-nightly.20200724](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200724)|2020-07-24||yes|82|12.18.2|86.0.4209.0|806|
|[v11.0.0-nightly.20200723](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200723)|2020-07-23||yes|82|12.18.2|86.0.4209.0|695|
|[v11.0.0-nightly.20200721](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200721)|2020-07-22||yes|82|12.18.2|86.0.4203.0|1139|
|[v11.0.0-nightly.20200720](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200720)|2020-07-20||yes|82|12.18.2|86.0.4203.0|618|
|[v11.0.0-nightly.20200717](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200717)|2020-07-17||yes|82|12.18.2|86.0.4203.0|480|
|[v11.0.0-nightly.20200716](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200716)|2020-07-16||yes|82|12.18.2|86.0.4203.0|591|
|[v11.0.0-nightly.20200709](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200709)|2020-07-09||yes|82|12.18.2|85.0.4179.0|607|
|[v11.0.0-nightly.20200708](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200708)|2020-07-08||yes|82|12.18.2|85.0.4179.0|790|
|[v11.0.0-nightly.20200707](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200707)|2020-07-07||yes|82|12.18.2|85.0.4179.0|575|
|[v11.0.0-nightly.20200706](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200706)|2020-07-06||yes|82|12.18.2|85.0.4179.0|575|
|[v11.0.0-nightly.20200703](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200703)|2020-07-03||yes|82|12.18.2|85.0.4179.0|642|
|[v11.0.0-nightly.20200702](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200702)|2020-07-02||yes|82|12.18.2|85.0.4179.0|585|
|[v11.0.0-nightly.20200701](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200701)|July 1, 2020||yes|82|12.18.1|85.0.4179.0|536|
|[v11.0.0-nightly.20200619](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200619)|2020-06-19||yes|82|12.18.1|85.0.4162.0|796|
|[v11.0.0-nightly.20200618](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200618)|2020-06-18||yes|82|12.18.0|85.0.4162.0|524|
|[v11.0.0-nightly.20200617](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200617)|2020-06-17||yes|82|12.16.3|85.0.4162.0|522|
|[v11.0.0-nightly.20200616](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200616)|2020-06-16||yes|82|12.16.3|85.0.4162.0|524|
|[v11.0.0-nightly.20200615](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200615)|2020-06-15||yes|82|12.16.3|85.0.4162.0|341|
|[v11.0.0-nightly.20200611](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200611)|2020-06-11||yes|82|12.16.3|85.0.4162.0|618|
|[v11.0.0-nightly.20200610](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200610)|2020-06-10||yes|82|12.16.3|85.0.4162.0|343|
|[v11.0.0-nightly.20200609](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200609)|2020-06-09||yes|82|12.16.3|85.0.4162.0|516|
|[v11.0.0-nightly.20200604](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200604)|2020-06-04||yes|82|12.16.3|85.0.4162.0|329|
|[v11.0.0-nightly.20200603](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200603)|2020-06-03||yes|82|12.16.3|85.0.4162.0|677|
|[v11.0.0-nightly.20200602](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200602)|2020-06-02||yes|82|12.16.3|85.0.4162.0|517|
|[v11.0.0-nightly.20200529](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200529)|2020-05-29||yes|82|12.16.3|85.0.4156.0|541|
|[v11.0.0-nightly.20200526](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200526)|2020-05-26||yes|82|12.16.3|84.0.4129.0|478|
|[v11.0.0-nightly.20200525](https://github.com/electron/electron/releases/tag/v11.0.0-nightly.20200525)|2020-05-25||yes|82|12.16.3|84.0.4129.0|377|
|[v11.0.0-beta.23](https://github.com/electron/electron/releases/tag/v11.0.0-beta.23)|November 14, 2020|beta-11-x-y|yes|85|12.18.3|87.0.4280.47|3908|
|[v11.0.0-beta.22](https://github.com/electron/electron/releases/tag/v11.0.0-beta.22)|November 12, 2020||yes|85|12.18.3|87.0.4280.47|4424|
|[v11.0.0-beta.20](https://github.com/electron/electron/releases/tag/v11.0.0-beta.20)|November 6, 2020||yes|85|12.18.3|87.0.4280.40|11532|
|[v11.0.0-beta.19](https://github.com/electron/electron/releases/tag/v11.0.0-beta.19)|November 2, 2020||yes|85|12.18.3|87.0.4280.27|4890|
|[v11.0.0-beta.18](https://github.com/electron/electron/releases/tag/v11.0.0-beta.18)|2020-10-29||yes|85|12.18.3|87.0.4280.27|4985|
|[v11.0.0-beta.17](https://github.com/electron/electron/releases/tag/v11.0.0-beta.17)|2020-10-26||yes|85|12.18.3|87.0.4280.27|6085|
|[v11.0.0-beta.16](https://github.com/electron/electron/releases/tag/v11.0.0-beta.16)|October 24, 2020||yes|85|12.18.3|87.0.4280.27|5145|
|[v11.0.0-beta.13](https://github.com/electron/electron/releases/tag/v11.0.0-beta.13)|2020-10-15||yes|85|12.18.3|87.0.4280.11|4108|
|[v11.0.0-beta.12](https://github.com/electron/electron/releases/tag/v11.0.0-beta.12)|2020-10-14||yes|85|12.18.3|87.0.4280.11|5025|
|[v11.0.0-beta.11](https://github.com/electron/electron/releases/tag/v11.0.0-beta.11)|October 5, 2020||yes|85|12.18.3|87.0.4251.1|3087|
|[v11.0.0-beta.9](https://github.com/electron/electron/releases/tag/v11.0.0-beta.9)|September 28, 2020||yes|82|12.18.3|87.0.4251.1|5285|
|[v11.0.0-beta.8](https://github.com/electron/electron/releases/tag/v11.0.0-beta.8)|2020-09-25||yes|82|12.18.3|87.0.4251.1|2477|
|[v11.0.0-beta.7](https://github.com/electron/electron/releases/tag/v11.0.0-beta.7)|September 14, 2020||yes|82|12.18.3|86.0.4234.0|3764|
|[v11.0.0-beta.6](https://github.com/electron/electron/releases/tag/v11.0.0-beta.6)|2020-09-10||yes|82|12.18.3|86.0.4234.0|3321|
|[v11.0.0-beta.5](https://github.com/electron/electron/releases/tag/v11.0.0-beta.5)|2020-09-07||yes|82|12.18.3|86.0.4234.0|2496|
|[v11.0.0-beta.4](https://github.com/electron/electron/releases/tag/v11.0.0-beta.4)|September 3, 2020||yes|82|12.18.3|86.0.4234.0|5638|
|[v11.0.0-beta.3](https://github.com/electron/electron/releases/tag/v11.0.0-beta.3)|August 31, 2020||yes|82|12.18.3|86.0.4234.0|2557|
|[v11.0.0-beta.1](https://github.com/electron/electron/releases/tag/v11.0.0-beta.1)|August 26, 2020||yes|82|12.18.3|86.0.4234.0|3118|
|[v10.4.7](https://github.com/electron/electron/releases/tag/v10.4.7)|May 24, 2021|10-x-y|no|82|12.16.3|85.0.4183.121|264595|
|[v10.4.6](https://github.com/electron/electron/releases/tag/v10.4.6)|May 19, 2021||no|82|12.16.3|85.0.4183.121|8956|
|[v10.4.5](https://github.com/electron/electron/releases/tag/v10.4.5)|May 5, 2021||no|82|12.16.3|85.0.4183.121|51763|
|[v10.4.4](https://github.com/electron/electron/releases/tag/v10.4.4)|April 27, 2021||no|82|12.16.3|85.0.4183.121|23290|
|[v10.4.3](https://github.com/electron/electron/releases/tag/v10.4.3)|April 14, 2021||no|82|12.16.3|85.0.4183.121|78617|
|[v10.4.2](https://github.com/electron/electron/releases/tag/v10.4.2)|March 23, 2021||no|82|12.16.3|85.0.4183.121|53762|
|[v10.4.1](https://github.com/electron/electron/releases/tag/v10.4.1)|March 15, 2021||no|82|12.16.3|85.0.4183.121|16516|
|[v10.4.0](https://github.com/electron/electron/releases/tag/v10.4.0)|February 20, 2021||no|82|12.16.3|85.0.4183.121|45689|
|[v10.3.2](https://github.com/electron/electron/releases/tag/v10.3.2)|February 5, 2021||no|82|12.16.3|85.0.4183.121|52740|
|[v10.3.1](https://github.com/electron/electron/releases/tag/v10.3.1)|January 27, 2021||no|82|12.16.3|85.0.4183.121|42872|
|[v10.3.0](https://github.com/electron/electron/releases/tag/v10.3.0)|January 15, 2021||no|82|12.16.3|85.0.4183.121|44826|
|[v10.2.0](https://github.com/electron/electron/releases/tag/v10.2.0)|December 12, 2020||no|82|12.16.3|85.0.4183.121|177918|
|[v10.1.7](https://github.com/electron/electron/releases/tag/v10.1.7)|December 8, 2020||no|82|12.16.3|85.0.4183.121|26520|
|[v10.1.6](https://github.com/electron/electron/releases/tag/v10.1.6)|November 18, 2020||no|82|12.16.3|85.0.4183.121|118093|
|[v10.1.5](https://github.com/electron/electron/releases/tag/v10.1.5)|October 23, 2020||no|82|12.16.3|85.0.4183.121|441616|
|[v10.1.4](https://github.com/electron/electron/releases/tag/v10.1.4)|October 20, 2020||no|82|12.16.3|85.0.4183.121|189094|
|[v10.1.3](https://github.com/electron/electron/releases/tag/v10.1.3)|September 29, 2020||no|82|12.16.3|85.0.4183.121|340102|
|[v10.1.2](https://github.com/electron/electron/releases/tag/v10.1.2)|September 14, 2020||no|82|12.16.3|85.0.4183.98|233599|
|[v10.1.1](https://github.com/electron/electron/releases/tag/v10.1.1)|September 1, 2020||no|82|12.16.3|85.0.4183.93|242164|
|[v10.1.0](https://github.com/electron/electron/releases/tag/v10.1.0)|August 28, 2020||no|82|12.16.3|85.0.4183.87|73501|
|[v10.0.1](https://github.com/electron/electron/releases/tag/v10.0.1)|August 27, 2020||no|82|12.16.3|85.0.4183.86|5161|
|[v10.0.0](https://github.com/electron/electron/releases/tag/v10.0.0)|August 24, 2020||no|82|12.16.3|85.0.4183.84|311329|
|[v10.0.0-nightly.20200521](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200521)|May 21, 2020||yes|82|12.16.3|84.0.4129.0|573|
|[v10.0.0-nightly.20200520](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200520)|2020-05-20||yes|82|12.16.3|84.0.4129.0|385|
|[v10.0.0-nightly.20200519](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200519)|2020-05-19||yes|82|12.16.3|84.0.4129.0|376|
|[v10.0.0-nightly.20200518](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200518)|2020-05-18||yes|82|12.16.3|84.0.4129.0|407|
|[v10.0.0-nightly.20200515](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200515)|2020-05-15||yes|82|12.16.3|84.0.4129.0|347|
|[v10.0.0-nightly.20200514](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200514)|2020-05-14||yes|82|12.16.3|84.0.4129.0|485|
|[v10.0.0-nightly.20200513](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200513)|2020-05-13||yes|82|12.16.3|84.0.4129.0|368|
|[v10.0.0-nightly.20200512](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200512)|2020-05-12||yes|82|12.16.3|84.0.4129.0|369|
|[v10.0.0-nightly.20200511](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200511)|2020-05-11||yes|82|12.16.3|84.0.4129.0|392|
|[v10.0.0-nightly.20200508](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200508)|2020-05-08||yes|82|12.16.3|84.0.4129.0|613|
|[v10.0.0-nightly.20200507](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200507)|2020-05-07||yes|82|12.16.3|84.0.4129.0|407|
|[v10.0.0-nightly.20200506](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200506)|2020-05-06||yes|82|12.16.3|84.0.4129.0|358|
|[v10.0.0-nightly.20200505](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200505)|2020-05-05||yes|82|12.16.3|84.0.4129.0|367|
|[v10.0.0-nightly.20200504](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200504)|2020-05-04||yes|82|12.16.3|84.0.4129.0|316|
|[v10.0.0-nightly.20200501](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200501)|May 1, 2020||yes|82|12.16.3|84.0.4129.0|467|
|[v10.0.0-nightly.20200430](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200430)|2020-04-30||yes|82|12.16.3|84.0.4125.0|352|
|[v10.0.0-nightly.20200429](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200429)|2020-04-29||yes|82|12.16.2|84.0.4125.0|340|
|[v10.0.0-nightly.20200428](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200428)|2020-04-28||yes|82|12.16.2|84.0.4125.0|374|
|[v10.0.0-nightly.20200427](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200427)|2020-04-27||yes|82|12.16.2|84.0.4125.0|350|
|[v10.0.0-nightly.20200423](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200423)|2020-04-24||yes|82|12.16.2|84.0.4121.0|396|
|[v10.0.0-nightly.20200422](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200422)|2020-04-22||yes|82|12.16.2|84.0.4121.0|484|
|[v10.0.0-nightly.20200417](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200417)|2020-04-17||yes|82|12.16.2|84.0.4115.0|513|
|[v10.0.0-nightly.20200416](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200416)|2020-04-16||yes|82|12.16.2|84.0.4115.0|1092|
|[v10.0.0-nightly.20200415](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200415)|2020-04-15||yes|82|12.16.2|84.0.4115.0|366|
|[v10.0.0-nightly.20200414](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200414)|2020-04-14||yes|82|12.16.1|84.0.4114.0|357|
|[v10.0.0-nightly.20200413](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200413)|2020-04-13||yes|82|12.16.1|83.0.4095.0|361|
|[v10.0.0-nightly.20200410](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200410)|2020-04-10||yes|82|12.16.1|83.0.4095.0|331|
|[v10.0.0-nightly.20200408](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200408)|2020-04-08||yes|82|12.16.1|83.0.4095.0|473|
|[v10.0.0-nightly.20200406](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200406)|2020-04-06||yes|82|12.16.1|83.0.4087.0|431|
|[v10.0.0-nightly.20200403](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200403)|2020-04-03||yes|82|12.16.1|83.0.4087.0|249|
|[v10.0.0-nightly.20200402](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200402)|2020-04-02||yes|82|12.16.1|83.0.4087.0|441|
|[v10.0.0-nightly.20200401](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200401)|April 1, 2020||yes|82|12.16.1|83.0.4087.0|364|
|[v10.0.0-nightly.20200331](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200331)|2020-03-31||yes|82|12.16.1|83.0.4087.0|388|
|[v10.0.0-nightly.20200330](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200330)|2020-03-30||yes|82|12.16.1|83.0.4087.0|348|
|[v10.0.0-nightly.20200327](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200327)|2020-03-27||yes|82|12.16.1|83.0.4087.0|415|
|[v10.0.0-nightly.20200326](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200326)|2020-03-26||yes|82|12.16.1|83.0.4087.0|348|
|[v10.0.0-nightly.20200325](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200325)|2020-03-25||yes|82|12.16.1|83.0.4087.0|344|
|[v10.0.0-nightly.20200324](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200324)|2020-03-24||yes|82|12.16.1|83.0.4087.0|372|
|[v10.0.0-nightly.20200323](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200323)|2020-03-23||yes|82|12.16.1|83.0.4087.0|367|
|[v10.0.0-nightly.20200320](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200320)|2020-03-20||yes|82|12.16.1|83.0.4087.0|410|
|[v10.0.0-nightly.20200318](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200318)|2020-03-18||yes|82|12.16.1|83.0.4087.0|350|
|[v10.0.0-nightly.20200317](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200317)|2020-03-17||yes|82|12.16.1|83.0.4087.0|434|
|[v10.0.0-nightly.20200316](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200316)|2020-03-16||yes|82|12.16.1|83.0.4086.0|318|
|[v10.0.0-nightly.20200311](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200311)|2020-03-11||yes|82|12.16.1|82.0.4083.0|313|
|[v10.0.0-nightly.20200310](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200310)|2020-03-10||yes|82|12.16.1|82.0.4076.0|547|
|[v10.0.0-nightly.20200309](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200309)|2020-03-09||yes|82|12.16.1|82.0.4076.0|356|
|[v10.0.0-nightly.20200306](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200306)|2020-03-06||yes|82|12.16.1|82.0.4076.0|419|
|[v10.0.0-nightly.20200305](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200305)|2020-03-05||yes|82|12.16.1|82.0.4076.0|347|
|[v10.0.0-nightly.20200304](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200304)|2020-03-04||yes|82|12.16.1|82.0.4076.0|350|
|[v10.0.0-nightly.20200303](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200303)|March 3, 2020||yes|82|12.16.1|82.0.4050.0|354|
|[v10.0.0-nightly.20200226](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200226)|February 26, 2020||yes|82|12.16.1|82.0.4050.0|563|
|[v10.0.0-nightly.20200223](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200223)|February 23, 2020||yes|82|12.15.0|82.0.4050.0|445|
|[v10.0.0-nightly.20200222](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200222)|February 22, 2020||yes|82|12.15.0|82.0.4050.0|368|
|[v10.0.0-nightly.20200221](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200221)|February 21, 2020||yes|82|12.15.0|82.0.4050.0|569|
|[v10.0.0-nightly.20200218](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200218)|February 18, 2020||yes|82|12.15.0|82.0.4050.0|442|
|[v10.0.0-nightly.20200217](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200217)|February 17, 2020||yes|82|12.15.0|82.0.4050.0|371|
|[v10.0.0-nightly.20200216](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200216)|February 16, 2020||yes|82|12.15.0|82.0.4050.0|441|
|[v10.0.0-nightly.20200211](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200211)|February 11, 2020||yes|76|12.15.0|82.0.4050.0|488|
|[v10.0.0-nightly.20200210](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200210)|February 10, 2020||yes|76|12.14.1|82.0.4050.0|874|
|[v10.0.0-nightly.20200209](https://github.com/electron/electron/releases/tag/v10.0.0-nightly.20200209)|February 9, 2020||yes|76|12.14.1|82.0.4050.0|403|
|[v10.0.0-beta.25](https://github.com/electron/electron/releases/tag/v10.0.0-beta.25)|August 22, 2020|beta-10-x-y|yes|82|12.16.3|85.0.4183.80|21102|
|[v10.0.0-beta.24](https://github.com/electron/electron/releases/tag/v10.0.0-beta.24)|August 20, 2020||yes|82|12.16.3|85.0.4183.78|2041|
|[v10.0.0-beta.23](https://github.com/electron/electron/releases/tag/v10.0.0-beta.23)|August 17, 2020||yes|82|12.16.3|85.0.4183.70|2821|
|[v10.0.0-beta.21](https://github.com/electron/electron/releases/tag/v10.0.0-beta.21)|August 11, 2020||yes|82|12.16.3|85.0.4183.39|7268|
|[v10.0.0-beta.20](https://github.com/electron/electron/releases/tag/v10.0.0-beta.20)|August 10, 2020||yes|82|12.16.3|85.0.4183.39|1906|
|[v10.0.0-beta.19](https://github.com/electron/electron/releases/tag/v10.0.0-beta.19)|August 6, 2020||yes|82|12.16.3|85.0.4183.39|2374|
|[v10.0.0-beta.17](https://github.com/electron/electron/releases/tag/v10.0.0-beta.17)|August 3, 2020||yes|82|12.16.3|85.0.4183.39|2061|
|[v10.0.0-beta.15](https://github.com/electron/electron/releases/tag/v10.0.0-beta.15)|July 29, 2020||yes|82|12.16.3|85.0.4183.39|3095|
|[v10.0.0-beta.14](https://github.com/electron/electron/releases/tag/v10.0.0-beta.14)|July 27, 2020||yes|82|12.16.3|85.0.4183.39|2097|
|[v10.0.0-beta.13](https://github.com/electron/electron/releases/tag/v10.0.0-beta.13)|July 23, 2020||yes|82|12.16.3|85.0.4183.39|1787|
|[v10.0.0-beta.12](https://github.com/electron/electron/releases/tag/v10.0.0-beta.12)|July 16, 2020||yes|82|12.16.3|85.0.4183.26|3620|
|[v10.0.0-beta.11](https://github.com/electron/electron/releases/tag/v10.0.0-beta.11)|July 13, 2020||yes|82|12.16.3|85.0.4183.20|2290|
|[v10.0.0-beta.10](https://github.com/electron/electron/releases/tag/v10.0.0-beta.10)|July 9, 2020||yes|82|12.16.3|85.0.4183.19|2449|
|[v10.0.0-beta.9](https://github.com/electron/electron/releases/tag/v10.0.0-beta.9)|July 6, 2020||yes|82|12.16.3|85.0.4181.1|2277|
|[v10.0.0-beta.8](https://github.com/electron/electron/releases/tag/v10.0.0-beta.8)|July 2, 2020||yes|82|12.16.3|85.0.4181.1|2068|
|[v10.0.0-beta.4](https://github.com/electron/electron/releases/tag/v10.0.0-beta.4)|June 18, 2020||yes|82|12.16.3|85.0.4161.2|2848|
|[v10.0.0-beta.3](https://github.com/electron/electron/releases/tag/v10.0.0-beta.3)|June 15, 2020||yes|82|12.16.3|85.0.4161.2|1817|
|[v10.0.0-beta.2](https://github.com/electron/electron/releases/tag/v10.0.0-beta.2)|June 1, 2020||yes|82|12.16.3|84.0.4129.0|3087|
|[v10.0.0-beta.1](https://github.com/electron/electron/releases/tag/v10.0.0-beta.1)|May 22, 2020||yes|82|12.16.3|84.0.4129.0|9119|
|[v9.4.4](https://github.com/electron/electron/releases/tag/v9.4.4)|March 3, 2021|9-x-y|no|80|12.14.1|83.0.4103.122|932460|
|[v9.4.3](https://github.com/electron/electron/releases/tag/v9.4.3)|February 5, 2021||no|80|12.14.1|83.0.4103.122|179024|
|[v9.4.2](https://github.com/electron/electron/releases/tag/v9.4.2)|January 27, 2021||no|80|12.14.1|83.0.4103.122|143792|
|[v9.4.1](https://github.com/electron/electron/releases/tag/v9.4.1)|January 13, 2021||no|80|12.14.1|83.0.4103.122|213204|
|[v9.4.0](https://github.com/electron/electron/releases/tag/v9.4.0)|December 12, 2020||no|80|12.14.1|83.0.4103.122|420821|
|[v9.3.5](https://github.com/electron/electron/releases/tag/v9.3.5)|November 24, 2020||no|80|12.14.1|83.0.4103.122|185695|
|[v9.3.4](https://github.com/electron/electron/releases/tag/v9.3.4)|November 10, 2020||no|80|12.14.1|83.0.4103.122|107262|
|[v9.3.3](https://github.com/electron/electron/releases/tag/v9.3.3)|October 26, 2020||no|80|12.14.1|83.0.4103.122|140963|
|[v9.3.2](https://github.com/electron/electron/releases/tag/v9.3.2)|October 5, 2020||no|80|12.14.1|83.0.4103.122|330058|
|[v9.3.1](https://github.com/electron/electron/releases/tag/v9.3.1)|September 15, 2020||no|80|12.14.1|83.0.4103.122|315628|
|[v9.3.0](https://github.com/electron/electron/releases/tag/v9.3.0)|September 3, 2020||no|80|12.14.1|83.0.4103.122|165973|
|[v9.2.1](https://github.com/electron/electron/releases/tag/v9.2.1)|August 18, 2020||no|80|12.14.1|83.0.4103.122|290803|
|[v9.2.0](https://github.com/electron/electron/releases/tag/v9.2.0)|August 7, 2020||no|80|12.14.1|83.0.4103.122|390053|
|[v9.1.2](https://github.com/electron/electron/releases/tag/v9.1.2)|July 28, 2020||no|80|12.14.1|83.0.4103.122|237509|
|[v9.1.1](https://github.com/electron/electron/releases/tag/v9.1.1)|July 20, 2020||no|80|12.14.1|83.0.4103.122|182182|
|[v9.1.0](https://github.com/electron/electron/releases/tag/v9.1.0)|July 6, 2020||no|80|12.14.1|83.0.4103.122|499431|
|[v9.0.5](https://github.com/electron/electron/releases/tag/v9.0.5)|June 22, 2020||no|80|12.14.1|83.0.4103.119|351526|
|[v9.0.4](https://github.com/electron/electron/releases/tag/v9.0.4)|June 12, 2020||no|80|12.14.1|83.0.4103.104|199901|
|[v9.0.3](https://github.com/electron/electron/releases/tag/v9.0.3)|June 8, 2020||no|80|12.14.1|83.0.4103.100|95629|
|[v9.0.2](https://github.com/electron/electron/releases/tag/v9.0.2)|June 2, 2020||no|80|12.14.1|83.0.4103.94|180988|
|[v9.0.1](https://github.com/electron/electron/releases/tag/v9.0.1)|June 1, 2020||no|80|12.14.1|83.0.4103.94|63694|
|[v9.0.0](https://github.com/electron/electron/releases/tag/v9.0.0)|May 19, 2020||no|80|12.14.1|83.0.4103.64|929365|
|[v9.0.0-nightly.20200121](https://github.com/electron/electron/releases/tag/v9.0.0-nightly.20200121)|January 21, 2020||yes|76|12.14.1|81.0.4030.0|1006|
|[v9.0.0-nightly.20200119](https://github.com/electron/electron/releases/tag/v9.0.0-nightly.20200119)|January 19, 2020||yes|76|12.14.1|81.0.4030.0|406|
|[v9.0.0-nightly.20200117](https://github.com/electron/electron/releases/tag/v9.0.0-nightly.20200117)|January 17, 2020||yes|76|12.14.1|81.0.3994.0|539|
|[v9.0.0-nightly.20200116](https://github.com/electron/electron/releases/tag/v9.0.0-nightly.20200116)|January 16, 2020||yes|76|12.14.1|81.0.3994.0|481|
|[v9.0.0-nightly.20200115](https://github.com/electron/electron/releases/tag/v9.0.0-nightly.20200115)|January 15, 2020||yes|76|12.14.1|81.0.3994.0|440|
|[v9.0.0-nightly.20200113](https://github.com/electron/electron/releases/tag/v9.0.0-nightly.20200113)|January 13, 2020||yes|76|12.14.1|81.0.3994.0|440|
|[v9.0.0-nightly.20200111](https://github.com/electron/electron/releases/tag/v9.0.0-nightly.20200111)|January 11, 2020||yes|76|12.14.1|81.0.3994.0|369|
|[v9.0.0-nightly.20200110](https://github.com/electron/electron/releases/tag/v9.0.0-nightly.20200110)|January 10, 2020||yes|76|12.14.1|81.0.3994.0|448|
|[v9.0.0-nightly.20200109](https://github.com/electron/electron/releases/tag/v9.0.0-nightly.20200109)|January 9, 2020||yes|76|12.14.0|81.0.3994.0|401|
|[v9.0.0-nightly.20200108](https://github.com/electron/electron/releases/tag/v9.0.0-nightly.20200108)|January 8, 2020||yes|76|12.14.0|81.0.3994.0|414|
|[v9.0.0-nightly.20200106](https://github.com/electron/electron/releases/tag/v9.0.0-nightly.20200106)|January 6, 2020||yes|76|12.14.0|81.0.3994.0|382|
|[v9.0.0-nightly.20200105](https://github.com/electron/electron/releases/tag/v9.0.0-nightly.20200105)|January 5, 2020||yes|76|12.14.0|81.0.3994.0|367|
|[v9.0.0-nightly.20200104](https://github.com/electron/electron/releases/tag/v9.0.0-nightly.20200104)|January 4, 2020||yes|76|12.14.0|81.0.3994.0|486|
|[v9.0.0-nightly.20200103](https://github.com/electron/electron/releases/tag/v9.0.0-nightly.20200103)|January 3, 2020||yes|76|12.14.0|81.0.3994.0|379|
|[v9.0.0-nightly.20200101](https://github.com/electron/electron/releases/tag/v9.0.0-nightly.20200101)|January 1, 2020||yes|76|12.14.0|81.0.3994.0|482|
|[v9.0.0-nightly.20191231](https://github.com/electron/electron/releases/tag/v9.0.0-nightly.20191231)|December 31, 2019||yes|76|12.14.0|81.0.3994.0|388|
|[v9.0.0-nightly.20191230](https://github.com/electron/electron/releases/tag/v9.0.0-nightly.20191230)|December 30, 2019||yes|76|12.14.0|81.0.3994.0|396|
|[v9.0.0-nightly.20191229](https://github.com/electron/electron/releases/tag/v9.0.0-nightly.20191229)|December 29, 2019||yes|76|12.14.0|81.0.3994.0|396|
|[v9.0.0-nightly.20191228](https://github.com/electron/electron/releases/tag/v9.0.0-nightly.20191228)|December 28, 2019||yes|76|12.14.0|81.0.3994.0|384|
|[v9.0.0-nightly.20191226](https://github.com/electron/electron/releases/tag/v9.0.0-nightly.20191226)|December 26, 2019||yes|76|12.14.0|81.0.3994.0|372|
|[v9.0.0-nightly.20191225](https://github.com/electron/electron/releases/tag/v9.0.0-nightly.20191225)|December 25, 2019||yes|76|12.14.0|81.0.3994.0|511|
|[v9.0.0-nightly.20191224](https://github.com/electron/electron/releases/tag/v9.0.0-nightly.20191224)|December 24, 2019||yes|76|12.14.0|81.0.3994.0|389|
|[v9.0.0-nightly.20191223](https://github.com/electron/electron/releases/tag/v9.0.0-nightly.20191223)|December 23, 2019||yes|76|12.14.0|81.0.3994.0|418|
|[v9.0.0-nightly.20191222](https://github.com/electron/electron/releases/tag/v9.0.0-nightly.20191222)|December 22, 2019||yes|76|12.14.0|81.0.3994.0|393|
|[v9.0.0-nightly.20191221](https://github.com/electron/electron/releases/tag/v9.0.0-nightly.20191221)|December 21, 2019||yes|76|12.14.0|81.0.3994.0|410|
|[v9.0.0-nightly.20191220](https://github.com/electron/electron/releases/tag/v9.0.0-nightly.20191220)|December 20, 2019||yes|76|12.14.0|81.0.3994.0|392|
|[v9.0.0-nightly.20191210](https://github.com/electron/electron/releases/tag/v9.0.0-nightly.20191210)|December 10, 2019||yes|76|12.13.0|80.0.3954.0|374|
|[v9.0.0-nightly.20191204](https://github.com/electron/electron/releases/tag/v9.0.0-nightly.20191204)|December 4, 2019||yes|76|12.13.0|80.0.3954.0|761|
|[v9.0.0-nightly.20191203](https://github.com/electron/electron/releases/tag/v9.0.0-nightly.20191203)|December 3, 2019||yes|76|12.13.0|80.0.3954.0|402|
|[v9.0.0-nightly.20191202](https://github.com/electron/electron/releases/tag/v9.0.0-nightly.20191202)|December 2, 2019||yes|76|12.13.0|80.0.3954.0|455|
|[v9.0.0-nightly.20191201](https://github.com/electron/electron/releases/tag/v9.0.0-nightly.20191201)|December 1, 2019||yes|76|12.13.0|80.0.3954.0|402|
|[v9.0.0-nightly.20191130](https://github.com/electron/electron/releases/tag/v9.0.0-nightly.20191130)|November 30, 2019||yes|76|12.13.0|80.0.3954.0|405|
|[v9.0.0-nightly.20191129](https://github.com/electron/electron/releases/tag/v9.0.0-nightly.20191129)|November 29, 2019||yes|76|12.13.0|80.0.3954.0|417|
|[v9.0.0-nightly.20191124](https://github.com/electron/electron/releases/tag/v9.0.0-nightly.20191124)|November 24, 2019||yes|76|12.13.0|80.0.3954.0|484|
|[v9.0.0-nightly.20191123](https://github.com/electron/electron/releases/tag/v9.0.0-nightly.20191123)|November 23, 2019||yes|76|12.13.0|80.0.3954.0|399|
|[v9.0.0-nightly.20191122](https://github.com/electron/electron/releases/tag/v9.0.0-nightly.20191122)|November 22, 2019||yes|76|12.13.0|80.0.3954.0|409|
|[v9.0.0-nightly.20191121](https://github.com/electron/electron/releases/tag/v9.0.0-nightly.20191121)|November 21, 2019||yes|76|12.13.0|80.0.3954.0|415|
|[v9.0.0-beta.24](https://github.com/electron/electron/releases/tag/v9.0.0-beta.24)|May 11, 2020|beta-9-x-y|yes|80|12.14.1|83.0.4103.45|13924|
|[v9.0.0-beta.23](https://github.com/electron/electron/releases/tag/v9.0.0-beta.23)|May 7, 2020||yes|80|12.14.1|83.0.4103.44|1624|
|[v9.0.0-beta.22](https://github.com/electron/electron/releases/tag/v9.0.0-beta.22)|April 30, 2020||yes|80|12.14.1|83.0.4103.34|6005|
|[v9.0.0-beta.21](https://github.com/electron/electron/releases/tag/v9.0.0-beta.21)|April 28, 2020||yes|80|12.14.1|83.0.4103.26|1819|
|[v9.0.0-beta.20](https://github.com/electron/electron/releases/tag/v9.0.0-beta.20)|April 27, 2020||yes|80|12.14.1|83.0.4103.26|1501|
|[v9.0.0-beta.19](https://github.com/electron/electron/releases/tag/v9.0.0-beta.19)|April 24, 2020||yes|80|12.14.1|83.0.4103.24|2431|
|[v9.0.0-beta.18](https://github.com/electron/electron/releases/tag/v9.0.0-beta.18)|April 20, 2020||yes|80|12.14.1|83.0.4103.16|2354|
|[v9.0.0-beta.17](https://github.com/electron/electron/releases/tag/v9.0.0-beta.17)|April 17, 2020||yes|80|12.14.1|83.0.4103.14|1926|
|[v9.0.0-beta.16](https://github.com/electron/electron/releases/tag/v9.0.0-beta.16)|April 13, 2020||yes|80|12.14.1|83.0.4102.3|2127|
|[v9.0.0-beta.15](https://github.com/electron/electron/releases/tag/v9.0.0-beta.15)|April 9, 2020||yes|80|12.14.1|83.0.4102.3|2763|
|[v9.0.0-beta.14](https://github.com/electron/electron/releases/tag/v9.0.0-beta.14)|April 6, 2020||yes|80|12.14.1|82.0.4085.27|2473|
|[v9.0.0-beta.13](https://github.com/electron/electron/releases/tag/v9.0.0-beta.13)|April 2, 2020||yes|80|12.14.1|82.0.4085.14|5099|
|[v9.0.0-beta.12](https://github.com/electron/electron/releases/tag/v9.0.0-beta.12)|March 30, 2020||yes|80|12.14.1|82.0.4085.14|2126|
|[v9.0.0-beta.10](https://github.com/electron/electron/releases/tag/v9.0.0-beta.10)|March 23, 2020||yes|80|12.14.1|82.0.4085.10|2560|
|[v9.0.0-beta.9](https://github.com/electron/electron/releases/tag/v9.0.0-beta.9)|March 16, 2020||yes|80|12.14.1|82.0.4058.2|2963|
|[v9.0.0-beta.7](https://github.com/electron/electron/releases/tag/v9.0.0-beta.7)|March 9, 2020||yes|80|12.14.1|82.0.4058.2|2546|
|[v9.0.0-beta.6](https://github.com/electron/electron/releases/tag/v9.0.0-beta.6)|March 6, 2020||yes|80|12.14.1|82.0.4058.2|3041|
|[v9.0.0-beta.5](https://github.com/electron/electron/releases/tag/v9.0.0-beta.5)|March 2, 2020||yes|80|12.14.1|82.0.4048.0|4312|
|[v9.0.0-beta.4](https://github.com/electron/electron/releases/tag/v9.0.0-beta.4)|February 28, 2020||yes|80|12.14.1|82.0.4048.0|2146|
|[v9.0.0-beta.3](https://github.com/electron/electron/releases/tag/v9.0.0-beta.3)|February 26, 2020||yes|80|12.14.1|82.0.4048.0|1965|
|[v9.0.0-beta.2](https://github.com/electron/electron/releases/tag/v9.0.0-beta.2)|February 16, 2020||yes|80|12.14.1|82.0.4048.0|2475|
|[v9.0.0-beta.1](https://github.com/electron/electron/releases/tag/v9.0.0-beta.1)|February 10, 2020||yes|76|12.14.1|82.0.4048.0|2233|
|[v8.5.5](https://github.com/electron/electron/releases/tag/v8.5.5)|November 18, 2020|8-x-y|no|76|12.13.0|80.0.3987.163|668689|
|[v8.5.4](https://github.com/electron/electron/releases/tag/v8.5.4)|November 17, 2020||no|76|12.13.0|80.0.3987.163|17526|
|[v8.5.3](https://github.com/electron/electron/releases/tag/v8.5.3)|October 30, 2020||no|76|12.13.0|80.0.3987.163|89162|
|[v8.5.2](https://github.com/electron/electron/releases/tag/v8.5.2)|September 22, 2020||no|76|12.13.0|80.0.3987.165|350550|
|[v8.5.1](https://github.com/electron/electron/releases/tag/v8.5.1)|September 3, 2020||no|76|12.13.0|80.0.3987.165|78966|
|[v8.5.0](https://github.com/electron/electron/releases/tag/v8.5.0)|August 7, 2020||no|76|12.13.0|80.0.3987.165|122121|
|[v8.4.1](https://github.com/electron/electron/releases/tag/v8.4.1)|July 23, 2020||no|76|12.13.0|80.0.3987.165|145330|
|[v8.4.0](https://github.com/electron/electron/releases/tag/v8.4.0)|July 7, 2020||no|76|12.13.0|80.0.3987.165|79535|
|[v8.3.4](https://github.com/electron/electron/releases/tag/v8.3.4)|June 25, 2020||no|76|12.13.0|80.0.3987.165|88826|
|[v8.3.3](https://github.com/electron/electron/releases/tag/v8.3.3)|June 18, 2020||no|76|12.13.0|80.0.3987.165|130939|
|[v8.3.2](https://github.com/electron/electron/releases/tag/v8.3.2)|June 15, 2020||no|76|12.13.0|80.0.3987.165|28799|
|[v8.3.1](https://github.com/electron/electron/releases/tag/v8.3.1)|June 1, 2020||no|76|12.13.0|80.0.3987.165|86551|
|[v8.3.0](https://github.com/electron/electron/releases/tag/v8.3.0)|May 15, 2020||no|76|12.13.0|80.0.3987.165|218654|
|[v8.2.5](https://github.com/electron/electron/releases/tag/v8.2.5)|April 30, 2020||no|76|12.13.0|80.0.3987.165|479425|
|[v8.2.4](https://github.com/electron/electron/releases/tag/v8.2.4)|April 28, 2020||no|76|12.13.0|80.0.3987.165|156006|
|[v8.2.3](https://github.com/electron/electron/releases/tag/v8.2.3)|April 16, 2020||no|76|12.13.0|80.0.3987.163|311143|
|[v8.2.2](https://github.com/electron/electron/releases/tag/v8.2.2)|April 13, 2020||no|76|12.13.0|80.0.3987.163|96955|
|[v8.2.1](https://github.com/electron/electron/releases/tag/v8.2.1)|April 6, 2020||no|76|12.13.0|80.0.3987.163|140886|
|[v8.2.0](https://github.com/electron/electron/releases/tag/v8.2.0)|March 24, 2020||no|76|12.13.0|80.0.3987.158|472013|
|[v8.1.1](https://github.com/electron/electron/releases/tag/v8.1.1)|March 10, 2020||no|76|12.13.0|80.0.3987.141|260439|
|[v8.1.0](https://github.com/electron/electron/releases/tag/v8.1.0)|March 6, 2020||no|76|12.13.0|80.0.3987.137|52491|
|[v8.0.3](https://github.com/electron/electron/releases/tag/v8.0.3)|March 3, 2020||no|76|12.13.0|80.0.3987.134|127926|
|[v8.0.2](https://github.com/electron/electron/releases/tag/v8.0.2)|February 26, 2020||no|76|12.13.0|80.0.3987.86|255552|
|[v8.0.1](https://github.com/electron/electron/releases/tag/v8.0.1)|February 14, 2020||no|76|12.13.0|80.0.3987.86|211316|
|[v8.0.0](https://github.com/electron/electron/releases/tag/v8.0.0)|February 3, 2020||no|76|12.13.0|80.0.3987.86|760925|
|[v8.0.0-nightly.20191105](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20191105)|November 5, 2019||yes|76|12.13.0|80.0.3952.0|633|
|[v8.0.0-nightly.20191101](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20191101)|November 1, 2019||yes|76|12.13.0|80.0.3952.0|451|
|[v8.0.0-nightly.20191023](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20191023)|October 23, 2019||yes|76|12.13.0|79.0.3931.0|599|
|[v8.0.0-nightly.20191021](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20191021)|October 21, 2019||yes|76|12.12.0|79.0.3931.0|439|
|[v8.0.0-nightly.20191020](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20191020)|October 20, 2019||yes|76|12.12.0|79.0.3931.0|446|
|[v8.0.0-nightly.20191019](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20191019)|October 19, 2019||yes|76|12.12.0|79.0.3931.0|423|
|[v8.0.0-nightly.20191017](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20191017)|October 17, 2019||yes|76|12.10.0|79.0.3919.0|374|
|[v8.0.0-nightly.20191012](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20191012)|October 12, 2019||yes|76|12.9.1|79.0.3919.0|441|
|[v8.0.0-nightly.20191011](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20191011)|October 11, 2019||yes|76|12.9.1|79.0.3919.0|372|
|[v8.0.0-nightly.20191009](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20191009)|October 9, 2019||yes|76|12.9.1|79.0.3919.0|392|
|[v8.0.0-nightly.20191006](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20191006)|October 6, 2019||yes|76|12.9.1|79.0.3919.0|386|
|[v8.0.0-nightly.20191005](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20191005)|October 5, 2019||yes|76|12.9.1|79.0.3919.0|368|
|[v8.0.0-nightly.20191004](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20191004)|October 4, 2019||yes|76|12.9.1|79.0.3919.0|354|
|[v8.0.0-nightly.20191001](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20191001)|October 1, 2019||yes|76|12.9.1|79.0.3919.0|409|
|[v8.0.0-nightly.20190930](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190930)|September 30, 2019||yes|76|12.9.1|79.0.3919.0|372|
|[v8.0.0-nightly.20190929](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190929)|September 29, 2019||yes|76|12.9.1|79.0.3919.0|377|
|[v8.0.0-nightly.20190926](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190926)|September 26, 2019||yes|76|12.9.1|79.0.3919.0|408|
|[v8.0.0-nightly.20190924](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190924)|September 24, 2019||yes|76|12.9.1|79.0.3919.0|365|
|[v8.0.0-nightly.20190923](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190923)|September 23, 2019||yes|76|12.9.1|79.0.3919.0|369|
|[v8.0.0-nightly.20190920](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190920)|September 20, 2019||yes|76|12.9.1|79.0.3915.0|425|
|[v8.0.0-nightly.20190919](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190919)|September 19, 2019||yes|76|12.9.1|79.0.3915.0|389|
|[v8.0.0-nightly.20190917](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190917)|September 17, 2019||yes|76|12.9.1|78.0.3892.0|382|
|[v8.0.0-nightly.20190915](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190915)|September 15, 2019||yes|76|12.9.1|78.0.3892.0|351|
|[v8.0.0-nightly.20190914](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190914)|September 14, 2019||yes|76|12.9.1|78.0.3892.0|376|
|[v8.0.0-nightly.20190913](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190913)|September 13, 2019||yes|76|12.9.1|78.0.3892.0|360|
|[v8.0.0-nightly.20190911](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190911)|September 11, 2019||yes|76|12.9.1|78.0.3892.0|361|
|[v8.0.0-nightly.20190910](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190910)|September 10, 2019||yes|76|12.9.1|78.0.3892.0|367|
|[v8.0.0-nightly.20190909](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190909)|September 9, 2019||yes|76|12.9.1|78.0.3892.0|369|
|[v8.0.0-nightly.20190907](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190907)|September 8, 2019||yes|76|12.9.1|78.0.3892.0|349|
|[v8.0.0-nightly.20190902](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190902)|September 2, 2019||yes|76|12.9.1|78.0.3892.0|310|
|[v8.0.0-nightly.20190901](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190901)|September 1, 2019||yes|76|12.9.1|78.0.3892.0|437|
|[v8.0.0-nightly.20190830](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190830)|August 30, 2019||yes|76|12.9.1|78.0.3892.0|337|
|[v8.0.0-nightly.20190828](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190828)|August 28, 2019||yes|76|12.9.1|78.0.3892.0|236|
|[v8.0.0-nightly.20190827](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190827)|August 28, 2019||yes|76|12.9.1|78.0.3892.0|210|
|[v8.0.0-nightly.20190825](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190825)|August 25, 2019||yes|76|12.9.0|78.0.3892.0|360|
|[v8.0.0-nightly.20190824](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190824)|August 24, 2019||yes|76|12.9.0|78.0.3892.0|312|
|[v8.0.0-nightly.20190820](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190820)|August 20, 2019||yes|76|12.8.1|78.0.3881.0|307|
|[v8.0.0-nightly.20190819](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190819)|August 20, 2019||yes|76|12.8.0|78.0.3881.0|366|
|[v8.0.0-nightly.20190818](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190818)|August 18, 2019||yes|76|12.8.0|78.0.3881.0|332|
|[v8.0.0-nightly.20190817](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190817)|August 17, 2019||yes|76|12.8.0|78.0.3881.0|319|
|[v8.0.0-nightly.20190816](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190816)|August 16, 2019||yes|76|12.8.0|78.0.3881.0|322|
|[v8.0.0-nightly.20190815](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190815)|August 15, 2019||yes|76|12.8.0|78.0.3871.0|321|
|[v8.0.0-nightly.20190814](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190814)|August 14, 2019||yes|76|12.8.0|78.0.3871.0|311|
|[v8.0.0-nightly.20190813](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190813)|August 13, 2019||yes|76|12.8.0|78.0.3871.0|336|
|[v8.0.0-nightly.20190812](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190812)|August 12, 2019||yes|76|12.6.0|78.0.3871.0|331|
|[v8.0.0-nightly.20190811](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190811)|August 12, 2019||yes|76|12.6.0|78.0.3871.0|329|
|[v8.0.0-nightly.20190810](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190810)|August 11, 2019||yes|76|12.6.0|78.0.3871.0|311|
|[v8.0.0-nightly.20190809](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190809)|August 9, 2019||yes|76|12.6.0|78.0.3871.0|318|
|[v8.0.0-nightly.20190808](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190808)|August 8, 2019||yes|76|12.6.0|78.0.3871.0|309|
|[v8.0.0-nightly.20190807](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190807)|August 7, 2019||yes|76|12.6.0|78.0.3871.0|331|
|[v8.0.0-nightly.20190806](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190806)|August 6, 2019||yes|76|12.6.0|78.0.3871.0|335|
|[v8.0.0-nightly.20190803](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190803)|August 4, 2019||yes|76|12.6.0|78.0.3871.0|383|
|[v8.0.0-nightly.20190802](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190802)|August 2, 2019||yes|76|12.6.0|78.0.3866.0|327|
|[v8.0.0-nightly.20190801](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190801)|August 1, 2019||yes|76|12.6.0|78.0.3866.0|334|
|[v8.0.0-beta.9](https://github.com/electron/electron/releases/tag/v8.0.0-beta.9)|January 30, 2020|beta-8-x-y|yes|76|12.13.0|80.0.3987.75|4844|
|[v8.0.0-beta.8](https://github.com/electron/electron/releases/tag/v8.0.0-beta.8)|January 29, 2020||yes|76|12.13.0|80.0.3987.75|1593|
|[v8.0.0-beta.7](https://github.com/electron/electron/releases/tag/v8.0.0-beta.7)|January 16, 2020||yes|76|12.13.0|80.0.3987.59|62207|
|[v8.0.0-beta.6](https://github.com/electron/electron/releases/tag/v8.0.0-beta.6)|January 14, 2020||yes|76|12.13.0|80.0.3987.51|2371|
|[v8.0.0-beta.5](https://github.com/electron/electron/releases/tag/v8.0.0-beta.5)|December 18, 2019||yes|76|12.13.0|80.0.3987.14|40282|
|[v8.0.0-beta.4](https://github.com/electron/electron/releases/tag/v8.0.0-beta.4)|December 4, 2019||yes|76|12.13.0|80.0.3955.0|30118|
|[v8.0.0-beta.3](https://github.com/electron/electron/releases/tag/v8.0.0-beta.3)|November 20, 2019||yes|76|12.13.0|80.0.3955.0|7528|
|[v8.0.0-beta.2](https://github.com/electron/electron/releases/tag/v8.0.0-beta.2)|November 1, 2019||yes|76|12.13.0|79.0.3931.0|6187|
|[v8.0.0-beta.1](https://github.com/electron/electron/releases/tag/v8.0.0-beta.1)|October 24, 2019||yes|76|12.13.0|79.0.3931.0|2734|
|[v7.3.3](https://github.com/electron/electron/releases/tag/v7.3.3)|2020-08-25|7-3-x|no|75|12.8.1|78.0.3904.130|861584|
|[v7.3.2](https://github.com/electron/electron/releases/tag/v7.3.2)|2020-06-24||no|75|12.8.1|78.0.3904.130|317817|
|[v7.3.1](https://github.com/electron/electron/releases/tag/v7.3.1)|2020-06-01||no|75|12.8.1|78.0.3904.130|85175|
|[v7.3.0](https://github.com/electron/electron/releases/tag/v7.3.0)|2020-05-15||no|75|12.8.1|78.0.3904.130|65869|
|[v7.2.4](https://github.com/electron/electron/releases/tag/v7.2.4)|2020-04-29|7-2-x|no|75|12.8.1|78.0.3904.130|193290|
|[v7.2.3](https://github.com/electron/electron/releases/tag/v7.2.3)|2020-04-17||no|75|12.8.1|78.0.3904.130|48598|
|[v7.2.2](https://github.com/electron/electron/releases/tag/v7.2.2)|2020-04-14||no|75|12.8.1|78.0.3904.130|25158|
|[v7.2.1](https://github.com/electron/electron/releases/tag/v7.2.1)|2020-03-24||no|75|12.8.1|78.0.3904.130|222418|
|[v7.2.0](https://github.com/electron/electron/releases/tag/v7.2.0)|2020-03-23||no|75|12.8.1|78.0.3904.130|4277|
|[v7.1.14](https://github.com/electron/electron/releases/tag/v7.1.14)|February 28, 2020|7-1-x|no|75|12.8.1|78.0.3904.130|303050|
|[v7.1.13](https://github.com/electron/electron/releases/tag/v7.1.13)|February 20, 2020||no|75|12.8.1|78.0.3904.130|118744|
|[v7.1.12](https://github.com/electron/electron/releases/tag/v7.1.12)|February 10, 2020||no|75|12.8.1|78.0.3904.130|100594|
|[v7.1.11](https://github.com/electron/electron/releases/tag/v7.1.11)|January 30, 2020||no|75|12.8.1|78.0.3904.130|381551|
|[v7.1.10](https://github.com/electron/electron/releases/tag/v7.1.10)|January 22, 2020||no|75|12.8.1|78.0.3904.130|223050|
|[v7.1.9](https://github.com/electron/electron/releases/tag/v7.1.9)|January 13, 2020||no|75|12.8.1|78.0.3904.130|228940|
|[v7.1.8](https://github.com/electron/electron/releases/tag/v7.1.8)|January 8, 2020||no|75|12.8.1|78.0.3904.130|117203|
|[v7.1.7](https://github.com/electron/electron/releases/tag/v7.1.7)|December 19, 2019||no|75|12.8.1|78.0.3904.130|457990|
|[v7.1.6](https://github.com/electron/electron/releases/tag/v7.1.6)|December 18, 2019||no|75|12.8.1|78.0.3904.130|73061|
|[v7.1.5](https://github.com/electron/electron/releases/tag/v7.1.5)|December 13, 2019||no|75|12.8.1|78.0.3904.130|104015|
|[v7.1.4](https://github.com/electron/electron/releases/tag/v7.1.4)|December 10, 2019||no|75|12.8.1|78.0.3904.130|149155|
|[v7.1.3](https://github.com/electron/electron/releases/tag/v7.1.3)|December 3, 2019||no|75|12.8.1|78.0.3904.126|180190|
|[v7.1.2](https://github.com/electron/electron/releases/tag/v7.1.2)|November 20, 2019||no|75|12.8.1|78.0.3904.113|399265|
|[v7.1.1](https://github.com/electron/electron/releases/tag/v7.1.1)|November 7, 2019||no|75|12.8.1|78.0.3904.99|262982|
|[v7.1.0](https://github.com/electron/electron/releases/tag/v7.1.0)|November 5, 2019||no|75|12.8.1|78.0.3904.94|103181|
|[v7.0.1](https://github.com/electron/electron/releases/tag/v7.0.1)|November 1, 2019|7-0-x|no|75|12.8.1|78.0.3904.92|121318|
|[v7.0.0](https://github.com/electron/electron/releases/tag/v7.0.0)|October 21, 2019||no|75|12.8.1|78.0.3905.1|952483|
|[v7.0.0-nightly.20190731](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190731)|July 31, 2019||yes|75|12.6.0|78.0.3866.0|365|
|[v7.0.0-nightly.20190730](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190730)|July 30, 2019||yes|75|12.6.0|78.0.3866.0|358|
|[v7.0.0-nightly.20190729](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190729)|July 29, 2019||yes|75|12.6.0|78.0.3866.0|312|
|[v7.0.0-nightly.20190728](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190728)|July 28, 2019||yes|75|12.6.0|78.0.3866.0|328|
|[v7.0.0-nightly.20190727](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190727)|July 27, 2019||yes|75|12.6.0|78.0.3866.0|332|
|[v7.0.0-nightly.20190726](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190726)|July 26, 2019||yes|75|12.6.0|77.0.3864.0|328|
|[v7.0.0-nightly.20190721](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190721)|July 21, 2019||yes|73|12.6.0|77.0.3848.0|597|
|[v7.0.0-nightly.20190720](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190720)|July 20, 2019||yes|73|12.6.0|77.0.3848.0|344|
|[v7.0.0-nightly.20190719](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190719)|July 19, 2019||yes|73|12.6.0|77.0.3848.0|322|
|[v7.0.0-nightly.20190705](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190705)|July 5, 2019||yes|73|12.0.0|77.0.3843.0|326|
|[v7.0.0-nightly.20190704](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190704)|July 4, 2019||yes|73|12.0.0|77.0.3843.0|547|
|[v7.0.0-nightly.20190702](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190702)|July 2, 2019||yes|73|12.0.0|77.0.3815.0|350|
|[v7.0.0-nightly.20190701](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190701)|July 1, 2019||yes|73|12.0.0|77.0.3815.0|317|
|[v7.0.0-nightly.20190630](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190630)|July 1, 2019||yes|73|12.0.0|77.0.3815.0|319|
|[v7.0.0-nightly.20190629](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190629)|June 29, 2019||yes|73|12.0.0|77.0.3815.0|332|
|[v7.0.0-nightly.20190627](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190627)|June 27, 2019||yes|73|12.0.0|77.0.3815.0|345|
|[v7.0.0-nightly.20190624](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190624)|June 24, 2019||yes|73|12.0.0|77.0.3815.0|360|
|[v7.0.0-nightly.20190623](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190623)|June 23, 2019||yes|73|12.0.0|77.0.3815.0|314|
|[v7.0.0-nightly.20190622](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190622)|June 22, 2019||yes|73|12.0.0|77.0.3815.0|321|
|[v7.0.0-nightly.20190619](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190619)|June 19, 2019||yes|73|12.0.0|77.0.3815.0|358|
|[v7.0.0-nightly.20190618](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190618)|June 18, 2019||yes|73|12.0.0|77.0.3815.0|319|
|[v7.0.0-nightly.20190616](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190616)|June 16, 2019||yes|73|12.0.0|77.0.3815.0|341|
|[v7.0.0-nightly.20190615](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190615)|June 15, 2019||yes|73|12.0.0|77.0.3815.0|325|
|[v7.0.0-nightly.20190613](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190613)|June 13, 2019||yes|73|12.0.0|77.0.3815.0|348|
|[v7.0.0-nightly.20190612](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190612)|June 12, 2019||yes|73|12.0.0|77.0.3815.0|333|
|[v7.0.0-nightly.20190611](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190611)|June 11, 2019||yes|73|12.0.0|77.0.3815.0|313|
|[v7.0.0-nightly.20190609](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190609)|June 9, 2019||yes|73|12.0.0|77.0.3815.0|308|
|[v7.0.0-nightly.20190608](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190608)|June 8, 2019||yes|73|12.0.0|77.0.3815.0|329|
|[v7.0.0-nightly.20190607](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190607)|June 7, 2019||yes|73|12.0.0|77.0.3815.0|320|
|[v7.0.0-nightly.20190606](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190606)|June 6, 2019||yes|73|12.0.0|77.0.3815.0|325|
|[v7.0.0-nightly.20190605](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190605)|June 5, 2019||yes|73|12.0.0|77.0.3815.0|324|
|[v7.0.0-nightly.20190604](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190604)|June 4, 2019||yes|73|12.0.0|77.0.3814.0|313|
|[v7.0.0-nightly.20190603](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190603)|June 3, 2019||yes|73|12.0.0|76.0.3806.0|315|
|[v7.0.0-nightly.20190602](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190602)|June 2, 2019||yes|73|12.0.0|76.0.3806.0|314|
|[v7.0.0-nightly.20190531](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190531)|May 31, 2019||yes|73|12.0.0|76.0.3806.0|318|
|[v7.0.0-nightly.20190530](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190530)|May 30, 2019||yes|73|12.0.0|76.0.3806.0|321|
|[v7.0.0-nightly.20190529](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190529)|May 29, 2019||yes|73|12.0.0|76.0.3806.0|322|
|[v7.0.0-nightly.20190521](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190521)|May 21, 2019||yes|73|12.0.0|76.0.3784.0|704|
|[v7.0.0-beta.7](https://github.com/electron/electron/releases/tag/v7.0.0-beta.7)|October 16, 2019|beta-7-0-x|yes|75|12.8.1|78.0.3905.1|3020|
|[v7.0.0-beta.6](https://github.com/electron/electron/releases/tag/v7.0.0-beta.6)|October 9, 2019||yes|75|12.8.1|78.0.3905.1|3116|
|[v7.0.0-beta.5](https://github.com/electron/electron/releases/tag/v7.0.0-beta.5)|September 24, 2019||yes|75|12.8.1|78.0.3905.1|4523|
|[v7.0.0-beta.4](https://github.com/electron/electron/releases/tag/v7.0.0-beta.4)|September 3, 2019||yes|75|12.8.1|78.0.3896.6|3812|
|[v7.0.0-beta.3](https://github.com/electron/electron/releases/tag/v7.0.0-beta.3)|August 15, 2019||yes|75|12.8.0|78.0.3866.0|4190|
|[v7.0.0-beta.2](https://github.com/electron/electron/releases/tag/v7.0.0-beta.2)|August 7, 2019||yes|75|12.6.0|78.0.3866.0|2987|
|[v7.0.0-beta.1](https://github.com/electron/electron/releases/tag/v7.0.0-beta.1)|August 1, 2019||yes|75|12.6.0|78.0.3866.0|2377|
|[v6.1.12](https://github.com/electron/electron/releases/tag/v6.1.12)|May 18, 2020|6-1-x|no|73|12.4.0|76.0.3809.146|580733|
|[v6.1.11](https://github.com/electron/electron/releases/tag/v6.1.11)|May 5, 2020||no|73|12.4.0|76.0.3809.146|47134|
|[v6.1.10](https://github.com/electron/electron/releases/tag/v6.1.10)|April 14, 2020||no|73|12.4.0|76.0.3809.146|78566|
|[v6.1.9](https://github.com/electron/electron/releases/tag/v6.1.9)|February 28, 2020||no|73|12.4.0|76.0.3809.146|91348|
|[v6.1.8](https://github.com/electron/electron/releases/tag/v6.1.8)|February 21, 2020||no|73|12.4.0|76.0.3809.146|14020|
|[v6.1.7](https://github.com/electron/electron/releases/tag/v6.1.7)|December 17, 2019||no|73|12.4.0|76.0.3809.146|353179|
|[v6.1.6](https://github.com/electron/electron/releases/tag/v6.1.6)|December 11, 2019||no|73|12.4.0|76.0.3809.146|136480|
|[v6.1.5](https://github.com/electron/electron/releases/tag/v6.1.5)|November 21, 2019||no|73|12.4.0|76.0.3809.146|155914|
|[v6.1.4](https://github.com/electron/electron/releases/tag/v6.1.4)|November 5, 2019||no|73|12.4.0|76.0.3809.146|324519|
|[v6.1.3](https://github.com/electron/electron/releases/tag/v6.1.3)|November 1, 2019||no|73|12.4.0|76.0.3809.146|18127|
|[v6.1.2](https://github.com/electron/electron/releases/tag/v6.1.2)|October 24, 2019||no|73|12.4.0|76.0.3809.146|78577|
|[v6.1.1](https://github.com/electron/electron/releases/tag/v6.1.1)|October 23, 2019||no|73|12.4.0|76.0.3809.146|23849|
|[v6.1.0](https://github.com/electron/electron/releases/tag/v6.1.0)|October 22, 2019||no|73|12.4.0|76.0.3809.146|16593|
|[v6.0.12](https://github.com/electron/electron/releases/tag/v6.0.12)|October 8, 2019|6-0-x|no|73|12.4.0|76.0.3809.146|293471|
|[v6.0.11](https://github.com/electron/electron/releases/tag/v6.0.11)|October 2, 2019||no|73|12.4.0|76.0.3809.146|148859|
|[v6.0.10](https://github.com/electron/electron/releases/tag/v6.0.10)|September 19, 2019||no|73|12.4.0|76.0.3809.146|383566|
|[v6.0.9](https://github.com/electron/electron/releases/tag/v6.0.9)|September 12, 2019||no|73|12.4.0|76.0.3809.146|121469|
|[v6.0.8](https://github.com/electron/electron/releases/tag/v6.0.8)|September 9, 2019||no|73|12.4.0|76.0.3809.146|83046|
|[v6.0.7](https://github.com/electron/electron/releases/tag/v6.0.7)|August 31, 2019||no|73|12.4.0|76.0.3809.139|233596|
|[v6.0.6](https://github.com/electron/electron/releases/tag/v6.0.6)|August 30, 2019||no|73|12.4.0|76.0.3809.138|16057|
|[v6.0.5](https://github.com/electron/electron/releases/tag/v6.0.5)|August 27, 2019||no|73|12.4.0|76.0.3809.136|99438|
|[v6.0.4](https://github.com/electron/electron/releases/tag/v6.0.4)|August 24, 2019||no|73|12.4.0|76.0.3809.131|42964|
|[v6.0.3](https://github.com/electron/electron/releases/tag/v6.0.3)|August 20, 2019||no|73|12.4.0|76.0.3809.126|66716|
|[v6.0.2](https://github.com/electron/electron/releases/tag/v6.0.2)|August 12, 2019||no|73|12.4.0|76.0.3809.110|89030|
|[v6.0.1](https://github.com/electron/electron/releases/tag/v6.0.1)|August 7, 2019||no|73|12.4.0|76.0.3809.102|89844|
|[v6.0.0](https://github.com/electron/electron/releases/tag/v6.0.0)|July 29, 2019||no|73|12.4.0|76.0.3809.88|545601|
|[v6.0.0-nightly.20190311](https://github.com/electron/electron/releases/tag/v6.0.0-nightly.20190311)|March 11, 2019||yes|68|12.0.0|74.0.3724.8|3373|
|[v6.0.0-nightly.20190213](https://github.com/electron/electron/releases/tag/v6.0.0-nightly.20190213)|February 14, 2019||yes|68|12.0.0|72.0.3626.110|1461|
|[v6.0.0-nightly.20190212](https://github.com/electron/electron/releases/tag/v6.0.0-nightly.20190212)|February 12, 2019||yes|68|12.0.0|72.0.3626.107|348|
|[v6.0.0-beta.15](https://github.com/electron/electron/releases/tag/v6.0.0-beta.15)|July 20, 2019|beta-6-0-x|yes|73|12.4.0|76.0.3809.74|5105|
|[v6.0.0-beta.14](https://github.com/electron/electron/releases/tag/v6.0.0-beta.14)|July 17, 2019||yes|73|12.4.0|76.0.3809.68|2521|
|[v6.0.0-beta.13](https://github.com/electron/electron/releases/tag/v6.0.0-beta.13)|July 10, 2019||yes|73|12.0.0|76.0.3809.60|3334|
|[v6.0.0-beta.12](https://github.com/electron/electron/releases/tag/v6.0.0-beta.12)|July 4, 2019||yes|73|12.0.0|76.0.3809.54|3165|
|[v6.0.0-beta.11](https://github.com/electron/electron/releases/tag/v6.0.0-beta.11)|June 26, 2019||yes|73|12.0.0|76.0.3809.42|2546|
|[v6.0.0-beta.10](https://github.com/electron/electron/releases/tag/v6.0.0-beta.10)|June 22, 2019||yes|73|12.0.0|76.0.3809.37|2512|
|[v6.0.0-beta.9](https://github.com/electron/electron/releases/tag/v6.0.0-beta.9)|June 18, 2019||yes|73|12.0.0|76.0.3809.26|2167|
|[v6.0.0-beta.8](https://github.com/electron/electron/releases/tag/v6.0.0-beta.8)|June 14, 2019||yes|73|12.0.0|76.0.3809.26|1916|
|[v6.0.0-beta.7](https://github.com/electron/electron/releases/tag/v6.0.0-beta.7)|June 11, 2019||yes|73|12.0.0|76.0.3809.22|1918|
|[v6.0.0-beta.6](https://github.com/electron/electron/releases/tag/v6.0.0-beta.6)|June 5, 2019||yes|73|12.0.0|76.0.3809.3|2215|
|[v6.0.0-beta.5](https://github.com/electron/electron/releases/tag/v6.0.0-beta.5)|2019-05-29||yes|73|12.0.0|76.0.3805.4|1840|
|[v6.0.0-beta.4](https://github.com/electron/electron/releases/tag/v6.0.0-beta.4)|2019-05-21||yes|73|12.0.0|76.0.3783.1|2264|
|[v6.0.0-beta.3](https://github.com/electron/electron/releases/tag/v6.0.0-beta.3)|May 14, 2019||yes|73|12.0.0|76.0.3783.1|15077|
|[v6.0.0-beta.2](https://github.com/electron/electron/releases/tag/v6.0.0-beta.2)|May 8, 2019||yes|73|12.0.0|76.0.3783.1|2540|
|[v6.0.0-beta.1](https://github.com/electron/electron/releases/tag/v6.0.0-beta.1)|May 1, 2019||yes|73|12.0.0|76.0.3774.1|2393|
|[v5.0.13](https://github.com/electron/electron/releases/tag/v5.0.13)|December 17, 2019|5-0-x|no|70|12.0.0|73.0.3683.121|1011294|
|[v5.0.12](https://github.com/electron/electron/releases/tag/v5.0.12)|November 2, 2019||no|70|12.0.0|73.0.3683.121|182352|
|[v5.0.11](https://github.com/electron/electron/releases/tag/v5.0.11)|August 24, 2019||no|70|12.0.0|73.0.3683.121|132943|
|[v5.0.10](https://github.com/electron/electron/releases/tag/v5.0.10)|August 20, 2019||no|70|12.0.0|73.0.3683.121|221680|
|[v5.0.9](https://github.com/electron/electron/releases/tag/v5.0.9)|August 6, 2019||no|70|12.0.0|73.0.3683.121|233496|
|[v5.0.8](https://github.com/electron/electron/releases/tag/v5.0.8)|July 23, 2019||no|70|12.0.0|73.0.3683.121|201079|
|[v5.0.7](https://github.com/electron/electron/releases/tag/v5.0.7)|July 16, 2019||no|70|12.0.0|73.0.3683.121|159885|
|[v5.0.6](https://github.com/electron/electron/releases/tag/v5.0.6)|June 26, 2019||no|70|12.0.0|73.0.3683.121|339558|
|[v5.0.5](https://github.com/electron/electron/releases/tag/v5.0.5)|June 21, 2019||no|70|12.0.0|73.0.3683.121|132152|
|[v5.0.4](https://github.com/electron/electron/releases/tag/v5.0.4)|June 15, 2019||no|70|12.0.0|73.0.3683.121|149153|
|[v5.0.3](https://github.com/electron/electron/releases/tag/v5.0.3)|June 7, 2019||no|70|12.0.0|73.0.3683.121|97694|
|[v5.0.2](https://github.com/electron/electron/releases/tag/v5.0.2)|May 23, 2019||no|70|12.0.0|73.0.3683.121|221520|
|[v5.0.1](https://github.com/electron/electron/releases/tag/v5.0.1)|May 4, 2019||no|70|12.0.0|73.0.3683.121|917890|
|[v5.0.0](https://github.com/electron/electron/releases/tag/v5.0.0)|April 24, 2019||no|70|12.0.0|73.0.3683.119|219964|
|[v5.0.0-nightly.20190122](https://github.com/electron/electron/releases/tag/v5.0.0-nightly.20190122)|January 22, 2019||yes|68|12.0.0|71.0.3578.98|225|
|[v5.0.0-nightly.20190121](https://github.com/electron/electron/releases/tag/v5.0.0-nightly.20190121)|January 22, 2019||yes|68|12.0.0|71.0.3578.98|406|
|[v5.0.0-nightly.20190107](https://github.com/electron/electron/releases/tag/v5.0.0-nightly.20190107)|January 8, 2019||yes|67|11.0.0|70.0.3538.110|818|
|[v5.0.0-beta.9](https://github.com/electron/electron/releases/tag/v5.0.0-beta.9)|April 20, 2019|beta-5-0-x|yes|70|12.0.0|73.0.3683.117|3999|
|[v5.0.0-beta.8](https://github.com/electron/electron/releases/tag/v5.0.0-beta.8)|April 4, 2019||yes|68|12.0.0|73.0.3683.104|8549|
|[v5.0.0-beta.7](https://github.com/electron/electron/releases/tag/v5.0.0-beta.7)|March 28, 2019||yes|68|12.0.0|73.0.3683.94|21239|
|[v5.0.0-beta.6](https://github.com/electron/electron/releases/tag/v5.0.0-beta.6)|March 20, 2019||yes|68|12.0.0|73.0.3683.84|49807|
|[v5.0.0-beta.5](https://github.com/electron/electron/releases/tag/v5.0.0-beta.5)|March 5, 2019||yes|68|12.0.0|73.0.3683.61|7075|
|[v5.0.0-beta.4](https://github.com/electron/electron/releases/tag/v5.0.0-beta.4)|February 27, 2019||yes|68|12.0.0|73.0.3683.54|3056|
|[v5.0.0-beta.3](https://github.com/electron/electron/releases/tag/v5.0.0-beta.3)|February 15, 2019||yes|68|12.0.0|73.0.3683.27|5817|
|[v5.0.0-beta.2](https://github.com/electron/electron/releases/tag/v5.0.0-beta.2)|February 4, 2019||yes|68|12.0.0|72.0.3626.52|5275|
|[v5.0.0-beta.1](https://github.com/electron/electron/releases/tag/v5.0.0-beta.1)|January 23, 2019||yes|68|12.0.0|72.0.3626.52|8677|
|[v4.2.12](https://github.com/electron/electron/releases/tag/v4.2.12)|October 16, 2019|4-2-x|no|69|10.11.0|69.0.3497.128|848191|
|[v4.2.11](https://github.com/electron/electron/releases/tag/v4.2.11)|September 24, 2019||no|69|10.11.0|69.0.3497.128|82213|
|[v4.2.10](https://github.com/electron/electron/releases/tag/v4.2.10)|August 29, 2019||no|69|10.11.0|69.0.3497.128|99310|
|[v4.2.9](https://github.com/electron/electron/releases/tag/v4.2.9)|August 6, 2019||no|69|10.11.0|69.0.3497.128|102385|
|[v4.2.8](https://github.com/electron/electron/releases/tag/v4.2.8)|July 20, 2019||no|69|10.11.0|69.0.3497.128|72294|
|[v4.2.7](https://github.com/electron/electron/releases/tag/v4.2.7)|July 16, 2019||no|69|10.11.0|69.0.3497.128|37619|
|[v4.2.6](https://github.com/electron/electron/releases/tag/v4.2.6)|July 2, 2019||no|69|10.11.0|69.0.3497.128|90712|
|[v4.2.5](https://github.com/electron/electron/releases/tag/v4.2.5)|June 21, 2019||no|69|10.11.0|69.0.3497.128|79645|
|[v4.2.4](https://github.com/electron/electron/releases/tag/v4.2.4)|June 5, 2019||no|69|10.11.0|69.0.3497.128|118649|
|[v4.2.3](https://github.com/electron/electron/releases/tag/v4.2.3)|May 31, 2019||no|69|10.11.0|69.0.3497.128|64006|
|[v4.2.2](https://github.com/electron/electron/releases/tag/v4.2.2)|May 17, 2019||no|69|10.11.0|69.0.3497.128|92409|
|[v4.2.1](https://github.com/electron/electron/releases/tag/v4.2.1)|May 14, 2019||no|69|10.11.0|69.0.3497.128|32786|
|[v4.2.0](https://github.com/electron/electron/releases/tag/v4.2.0)|May 3, 2019||no|69|10.11.0|69.0.3497.128|250913|
|[v4.1.5](https://github.com/electron/electron/releases/tag/v4.1.5)|April 24, 2019|4-1-x|no|69|10.11.0|69.0.3497.128|76689|
|[v4.1.4](https://github.com/electron/electron/releases/tag/v4.1.4)|April 4, 2019||no|69|10.11.0|69.0.3497.128|446251|
|[v4.1.3](https://github.com/electron/electron/releases/tag/v4.1.3)|March 29, 2019||no|69|10.11.0|69.0.3497.128|132092|
|[v4.1.2](https://github.com/electron/electron/releases/tag/v4.1.2)|March 28, 2018||no|69|10.11.0|69.0.3497.128|18369|
|[v4.1.1](https://github.com/electron/electron/releases/tag/v4.1.1)|March 20, 2018||no|69|10.11.0|69.0.3497.128|142553|
|[v4.1.0](https://github.com/electron/electron/releases/tag/v4.1.0)|March 14, 2019||no|69|10.11.0|69.0.3497.128|157650|
|[v4.0.8](https://github.com/electron/electron/releases/tag/v4.0.8)|March 8, 2019|4-0-x|no|69|10.11.0|69.0.3497.128|104689|
|[v4.0.7](https://github.com/electron/electron/releases/tag/v4.0.7)|March 5, 2019||no|69|10.11.0|69.0.3497.128|87955|
|[v4.0.6](https://github.com/electron/electron/releases/tag/v4.0.6)|February 27, 2019||no|69|10.11.0|69.0.3497.106|113703|
|[v4.0.5](https://github.com/electron/electron/releases/tag/v4.0.5)|February 15, 2019||no|69|10.11.0|69.0.3497.106|166317|
|[v4.0.4](https://github.com/electron/electron/releases/tag/v4.0.4)|February 2, 2019||no|69|10.11.0|69.0.3497.106|501095|
|[v4.0.3](https://github.com/electron/electron/releases/tag/v4.0.3)|January 29, 2019||no|64|10.11.0|69.0.3497.106|85055|
|[v4.0.2](https://github.com/electron/electron/releases/tag/v4.0.2)|January 22, 2019||no|64|10.11.0|69.0.3497.106|119852|
|[v4.0.1](https://github.com/electron/electron/releases/tag/v4.0.1)|January 4, 2019||no|64|10.11.0|69.0.3497.106|361864|
|[v4.0.0](https://github.com/electron/electron/releases/tag/v4.0.0)|December 20, 2018||no|64|10.11.0|69.0.3497.106|621216|
|[v4.0.0-nightly.20181010](https://github.com/electron/electron/releases/tag/v4.0.0-nightly.20181010)|October 10, 2018||yes|64|10.11.0|69.0.3497.106|8808|
|[v4.0.0-nightly.20181006](https://github.com/electron/electron/releases/tag/v4.0.0-nightly.20181006)|October 6, 2018||yes|64|10.11.0|68.0.3440.128|691|
|[v4.0.0-nightly.20180929](https://github.com/electron/electron/releases/tag/v4.0.0-nightly.20180929)|September 29, 2018||yes|64|10.6.0|67.0.3396.99|819|
|[v4.0.0-nightly.20180821](https://github.com/electron/electron/releases/tag/v4.0.0-nightly.20180821)|August 21, 2018||yes|64|10.2.0|66.0.3359.181|588|
|[v4.0.0-nightly.20180819](https://github.com/electron/electron/releases/tag/v4.0.0-nightly.20180819)|August 19, 2018||yes|64|10.2.0|66.0.3359.181|385|
|[v4.0.0-nightly.20180817](https://github.com/electron/electron/releases/tag/v4.0.0-nightly.20180817)|August 18, 2018||yes|64|10.2.0|66.0.3359.181|336|
|[v4.0.0-beta.11](https://github.com/electron/electron/releases/tag/v4.0.0-beta.11)|December 19, 2018|beta-4-0-x|yes|64|10.11.0|69.0.3497.106|6175|
|[v4.0.0-beta.10](https://github.com/electron/electron/releases/tag/v4.0.0-beta.10)|December 17, 2018||yes|64|10.11.0|69.0.3497.106|6034|
|[v4.0.0-beta.9](https://github.com/electron/electron/releases/tag/v4.0.0-beta.9)|December 11, 2018||yes|64|10.11.0|69.0.3497.106|4669|
|[v4.0.0-beta.8](https://github.com/electron/electron/releases/tag/v4.0.0-beta.8)|November 30, 2018||yes|64|10.11.0|69.0.3497.106|4480|
|[v4.0.0-beta.7](https://github.com/electron/electron/releases/tag/v4.0.0-beta.7)|November 6, 2018||yes|64|10.11.0|69.0.3497.106|9944|
|[v4.0.0-beta.6](https://github.com/electron/electron/releases/tag/v4.0.0-beta.6)|November 1, 2018||yes|64|10.11.0|69.0.3497.106|7297|
|[v4.0.0-beta.5](https://github.com/electron/electron/releases/tag/v4.0.0-beta.5)|October 23, 2018||yes|64|10.11.0|69.0.3497.106|7376|
|[v4.0.0-beta.4](https://github.com/electron/electron/releases/tag/v4.0.0-beta.4)|October 19, 2018||yes|64|10.11.0|69.0.3497.106|5508|
|[v4.0.0-beta.3](https://github.com/electron/electron/releases/tag/v4.0.0-beta.3)|October 12, 2018||yes|64|10.11.0|69.0.3497.106|5383|
|[v4.0.0-beta.2](https://github.com/electron/electron/releases/tag/v4.0.0-beta.2)|October 12, 2018||yes|64|10.11.0|69.0.3497.106|4051|
|[v4.0.0-beta.1](https://github.com/electron/electron/releases/tag/v4.0.0-beta.1)|October 11, 2018||yes|64|10.11.0|69.0.3497.106|26697|
|[v3.1.13](https://github.com/electron/electron/releases/tag/v3.1.13)|July 31, 2019||no|64|10.2.0|66.0.3359.181|548809|
|[v3.1.12](https://github.com/electron/electron/releases/tag/v3.1.12)|July 11, 2019|3-1-x|no|64|10.2.0|66.0.3359.181|48576|
|[v3.1.11](https://github.com/electron/electron/releases/tag/v3.1.11)|June 6, 2019||no|64|10.2.0|66.0.3359.181|64780|
|[v3.1.10](https://github.com/electron/electron/releases/tag/v3.1.10)|May 29, 2019||no|64|10.2.0|66.0.3359.181|48307|
|[v3.1.9](https://github.com/electron/electron/releases/tag/v3.1.9)|March 1, 2019||no|64|10.2.0|66.0.3359.181|162855|
|[v3.1.8](https://github.com/electron/electron/releases/tag/v3.1.8)|March 28, 2019||no|64|10.2.0|66.0.3359.181|159301|
|[v3.1.7](https://github.com/electron/electron/releases/tag/v3.1.7)|March 21, 2019||no|64|10.2.0|66.0.3359.181|85643|
|[v3.1.6](https://github.com/electron/electron/releases/tag/v3.1.6)|March 8, 2019||no|64|10.2.0|66.0.3359.181|120068|
|[v3.1.5](https://github.com/electron/electron/releases/tag/v3.1.5)|March 4, 2019||no|64|10.2.0|66.0.3359.181|12269|
|[v3.1.4](https://github.com/electron/electron/releases/tag/v3.1.4)|February 15, 2019||no|64|10.2.0|66.0.3359.181|43095|
|[v3.1.3](https://github.com/electron/electron/releases/tag/v3.1.3)|January 31, 2019||no|64|10.2.0|66.0.3359.181|220517|
|[v3.1.2](https://github.com/electron/electron/releases/tag/v3.1.2)|January 24, 2019||no|64|10.2.0|66.0.3359.181|34282|
|[v3.1.1](https://github.com/electron/electron/releases/tag/v3.1.1)|January 14, 2019||no|64|10.2.0|66.0.3359.181|66451|
|[v3.1.0](https://github.com/electron/electron/releases/tag/v3.1.0)|January 7, 2019||no|64|10.2.0|66.0.3359.181|54311|
|[v3.1.0-beta.5](https://github.com/electron/electron/releases/tag/v3.1.0-beta.5)|January 4, 2019|beta-3-1-x|yes|64|10.2.0|66.0.3359.181|7280|
|[v3.1.0-beta.4](https://github.com/electron/electron/releases/tag/v3.1.0-beta.4)|December 17, 2018||yes|64|10.2.0|66.0.3359.181|10248|
|[v3.1.0-beta.3](https://github.com/electron/electron/releases/tag/v3.1.0-beta.3)|December 14, 2018||yes|64|10.2.0|66.0.3359.181|3022|
|[v3.1.0-beta.2](https://github.com/electron/electron/releases/tag/v3.1.0-beta.2)|December 4, 2018||yes|64|10.2.0|66.0.3359.181|3701|
|[v3.1.0-beta.1](https://github.com/electron/electron/releases/tag/v3.1.0-beta.1)|December 2, 2018||yes|64|10.2.0|66.0.3359.181|2183|
|[v3.0.16](https://github.com/electron/electron/releases/tag/v3.0.16)|March 8, 2019|3-0-x|no|64|10.2.0|66.0.3359.181|35050|
|[v3.0.15](https://github.com/electron/electron/releases/tag/v3.0.15)|January 31, 2019||no|64|10.2.0|66.0.3359.181|10519|
|[v3.0.14](https://github.com/electron/electron/releases/tag/v3.0.14)|January 4, 2019||no|64|10.2.0|66.0.3359.181|37992|
|[v3.0.13](https://github.com/electron/electron/releases/tag/v3.0.13)|December 17, 2018||no|64|10.2.0|66.0.3359.181|230809|
|[v3.0.12](https://github.com/electron/electron/releases/tag/v3.0.12)|December 14, 2018||no|64|10.2.0|66.0.3359.181|32222|
|[v3.0.11](https://github.com/electron/electron/releases/tag/v3.0.11)|December 11, 2018||no|64|10.2.0|66.0.3359.181|105650|
|[v3.0.10](https://github.com/electron/electron/releases/tag/v3.0.10)|November 19, 2018||no|64|10.2.0|66.0.3359.181|372342|
|[v3.0.9](https://github.com/electron/electron/releases/tag/v3.0.9)|November 13, 2018||no|64|10.2.0|66.0.3359.181|181527|
|[v3.0.8](https://github.com/electron/electron/releases/tag/v3.0.8)|November 5, 2018||no|64|10.2.0|66.0.3359.181|130838|
|[v3.0.7](https://github.com/electron/electron/releases/tag/v3.0.7)|November 1, 2018||no|64|10.2.0|66.0.3359.181|132102|
|[v3.0.6](https://github.com/electron/electron/releases/tag/v3.0.6)|October 24, 2018||no|64|10.2.0|66.0.3359.181|110847|
|[v3.0.5](https://github.com/electron/electron/releases/tag/v3.0.5)|October 19, 2018||no|64|10.2.0|66.0.3359.181|96728|
|[v3.0.4](https://github.com/electron/electron/releases/tag/v3.0.4)|October 11, 2018||no|64|10.2.0|66.0.3359.181|125307|
|[v3.0.3](https://github.com/electron/electron/releases/tag/v3.0.3)|October 7, 2018||no|64|10.2.0|66.0.3359.181|75973|
|[v3.0.2](https://github.com/electron/electron/releases/tag/v3.0.2)|September 27, 2018||no|64|10.2.0|66.0.3359.181|130153|
|[v3.0.1](https://github.com/electron/electron/releases/tag/v3.0.1)|September 27, 2018||no|64|10.2.0|66.0.3359.181|16562|
|[v3.0.0](https://github.com/electron/electron/releases/tag/v3.0.0)|September 18, 2018||no|64|10.2.0|66.0.3359.181|1529536|
|[v3.0.0-nightly.20180904](https://github.com/electron/electron/releases/tag/v3.0.0-nightly.20180904)|September 5, 2018||yes|64|10.2.0|66.0.3359.181|1227|
|[v3.0.0-nightly.20180823](https://github.com/electron/electron/releases/tag/v3.0.0-nightly.20180823)|August 24, 2018||yes|64|10.2.0|66.0.3359.181|408|
|[v3.0.0-nightly.20180821](https://github.com/electron/electron/releases/tag/v3.0.0-nightly.20180821)|August 21, 2018||yes|64|10.2.0|66.0.3359.181|1157|
|[v3.0.0-nightly.20180818](https://github.com/electron/electron/releases/tag/v3.0.0-nightly.20180818)|August 18, 2018||yes|64|10.2.0|66.0.3359.181|529|
|[v3.0.0-beta.13](https://github.com/electron/electron/releases/tag/v3.0.0-beta.13)|September 17, 2018||yes|64|10.2.0|66.0.3359.181|3556|
|[v3.0.0-beta.12](https://github.com/electron/electron/releases/tag/v3.0.0-beta.12)|September 12, 2018||yes|64|10.2.0|66.0.3359.181|8052|
|[v3.0.0-beta.11](https://github.com/electron/electron/releases/tag/v3.0.0-beta.11)|September 12, 2018||yes|64|10.2.0|66.0.3359.181|3257|
|[v3.0.0-beta.10](https://github.com/electron/electron/releases/tag/v3.0.0-beta.10)|September 8, 2018||yes|64|10.2.0|66.0.3359.181|4509|
|[v3.0.0-beta.9](https://github.com/electron/electron/releases/tag/v3.0.0-beta.9)|September 6, 2018||yes|64|10.2.0|66.0.3359.181|3903|
|[v3.0.0-beta.8](https://github.com/electron/electron/releases/tag/v3.0.0-beta.8)|August 29, 2018||yes|64|10.2.0|66.0.3359.181|7066|
|[v3.0.0-beta.7](https://github.com/electron/electron/releases/tag/v3.0.0-beta.7)|August 22, 2018||yes|64|10.2.0|66.0.3359.181|5429|
|[v3.0.0-beta.6](https://github.com/electron/electron/releases/tag/v3.0.0-beta.6)|August 20, 2018||yes|64|10.2.0|66.0.3359.181|5255|
|[v3.0.0-beta.5](https://github.com/electron/electron/releases/tag/v3.0.0-beta.5)|August 13, 2018||yes|64|10.2.0|66.0.3359.181|28662|
|[v3.0.0-beta.4](https://github.com/electron/electron/releases/tag/v3.0.0-beta.4)|August 1, 2018||yes|64|10.2.0|66.0.3359.181|16729|
|[v3.0.0-beta.3](https://github.com/electron/electron/releases/tag/v3.0.0-beta.3)|July 17, 2018||yes|64|10.2.0|66.0.3359.181|8099|
|[v3.0.0-beta.2](https://github.com/electron/electron/releases/tag/v3.0.0-beta.2)|July 10, 2018||yes|64|10.2.0|66.0.3359.181|6201|
|[v3.0.0-beta.1](https://github.com/electron/electron/releases/tag/v3.0.0-beta.1)|June 21, 2018||yes|64|10.2.0|66.0.3359.181|35521|
|[v2.1.0-unsupported.20180809](https://github.com/electron/electron/releases/tag/v2.1.0-unsupported.20180809)|August 9, 2018|unsupported|no|57|8.9.3|61.0.3163.100|8862|
|[v2.0.18](https://github.com/electron/electron/releases/tag/v2.0.18)|March 8, 2019|2-0-x|no|57|8.9.3|61.0.3163.100|2328508|
|[v2.0.17](https://github.com/electron/electron/releases/tag/v2.0.17)|January 31, 2019||no|57|8.9.3|61.0.3163.100|111319|
|[v2.0.16](https://github.com/electron/electron/releases/tag/v2.0.16)|December 18, 2018||no|57|8.9.3|61.0.3163.100|203802|
|[v2.0.15](https://github.com/electron/electron/releases/tag/v2.0.15)|December 13, 2018||no|57|8.9.3|61.0.3163.100|18145|
|[v2.0.14](https://github.com/electron/electron/releases/tag/v2.0.14)|November 19, 2018||no|57|8.9.3|61.0.3163.100|123853|
|[v2.0.13](https://github.com/electron/electron/releases/tag/v2.0.13)|November 1, 2018||no|57|8.9.3|61.0.3163.100|119294|
|[v2.0.12](https://github.com/electron/electron/releases/tag/v2.0.12)|October 19, 2018||no|57|8.9.3|61.0.3163.100|155450|
|[v2.0.11](https://github.com/electron/electron/releases/tag/v2.0.11)|October 1, 2018||no|57|8.9.3|61.0.3163.100|107747|
|[v2.0.10](https://github.com/electron/electron/releases/tag/v2.0.10)|September 19, 2018||no|57|8.9.3|61.0.3163.100|103247|
|[v2.0.9](https://github.com/electron/electron/releases/tag/v2.0.9)|September 10, 2018||no|57|8.9.3|61.0.3163.100|304509|
|[v2.0.8](https://github.com/electron/electron/releases/tag/v2.0.8)|August 22, 2018||no|57|8.9.3|61.0.3163.100|939222|
|[v2.0.8-nightly.20180820](https://github.com/electron/electron/releases/tag/v2.0.8-nightly.20180820)|August 21, 2018||yes|57|8.9.3|61.0.3163.100|405|
|[v2.0.8-nightly.20180819](https://github.com/electron/electron/releases/tag/v2.0.8-nightly.20180819)|August 20, 2018||yes|57|8.9.3|61.0.3163.100|390|
|[v2.0.7](https://github.com/electron/electron/releases/tag/v2.0.7)|August 8, 2018||no|57|8.9.3|61.0.3163.100|232124|
|[v2.0.6](https://github.com/electron/electron/releases/tag/v2.0.6)|August 1, 2018||no|57|8.9.3|61.0.3163.100|196232|
|[v2.0.5](https://github.com/electron/electron/releases/tag/v2.0.5)|July 13, 2018||no|57|8.9.3|61.0.3163.100|283000|
|[v2.0.4](https://github.com/electron/electron/releases/tag/v2.0.4)|July 3, 2018||no|57|8.9.3|61.0.3163.100|178699|
|[v2.0.3](https://github.com/electron/electron/releases/tag/v2.0.3)|June 21, 2018||no|57|8.9.3|61.0.3163.100|147046|
|[v2.0.2](https://github.com/electron/electron/releases/tag/v2.0.2)|May 22, 2018||no|57|8.9.3|61.0.3163.100|491163|
|[v2.0.1](https://github.com/electron/electron/releases/tag/v2.0.1)|May 16, 2018||no|57|8.9.3|61.0.3163.100|128762|
|[v2.0.0](https://github.com/electron/electron/releases/tag/v2.0.0)|May 1, 2018||no|57|8.9.3|61.0.3163.100|747295|
|[v2.0.0-beta.8](https://github.com/electron/electron/releases/tag/v2.0.0-beta.8)|April 26, 2018||yes|57|8.9.3|61.0.3163.100|19657|
|[v2.0.0-beta.7](https://github.com/electron/electron/releases/tag/v2.0.0-beta.7)|April 3, 2018||yes|57|8.9.3|61.0.3163.100|44554|
|[v2.0.0-beta.6](https://github.com/electron/electron/releases/tag/v2.0.0-beta.6)|March 27, 2018||yes|57|8.9.3|61.0.3163.100|15544|
|[v2.0.0-beta.5](https://github.com/electron/electron/releases/tag/v2.0.0-beta.5)|March 20, 2018||yes|57|8.9.3|61.0.3163.100|14354|
|[v2.0.0-beta.4](https://github.com/electron/electron/releases/tag/v2.0.0-beta.4)|March 15, 2018||yes|57|8.9.3|61.0.3163.100|13109|
|[v2.0.0-beta.3](https://github.com/electron/electron/releases/tag/v2.0.0-beta.3)|March 9, 2018||yes|57|8.9.3|61.0.3163.100|11493|
|[v2.0.0-beta.2](https://github.com/electron/electron/releases/tag/v2.0.0-beta.2)|March 5, 2018||yes|57|8.9.3|61.0.3163.100|20773|
|[v2.0.0-beta.1](https://github.com/electron/electron/releases/tag/v2.0.0-beta.1)|February 21, 2018||yes|57|8.9.3|61.0.3163.100|16023|
|[v1.8.8](https://github.com/electron/electron/releases/tag/v1.8.8)|August 22, 2018|1-8-x|no|57|8.2.1|59.0.3071.115|5510094|
|[v1.8.7](https://github.com/electron/electron/releases/tag/v1.8.7)|May 16, 2018||no|57|8.2.1|59.0.3071.115|1123213|
|[v1.8.6](https://github.com/electron/electron/releases/tag/v1.8.6)|April 27, 2018||no|57|8.2.1|59.0.3071.115|285522|
|[v1.8.5](https://github.com/electron/electron/releases/tag/v1.8.5)|April 26, 2018||no|57|8.2.1|59.0.3071.115|22313|
|[v1.8.4](https://github.com/electron/electron/releases/tag/v1.8.4)|March 16, 2018||no|57|8.2.1|59.0.3071.115|957019|
|[v1.8.3](https://github.com/electron/electron/releases/tag/v1.8.3)|March 6, 2018||no|57|8.2.1|59.0.3071.115|416689|
|[v1.8.2](https://github.com/electron/electron/releases/tag/v1.8.2)|February 7, 2018||no|57|8.2.1|59.0.3071.115|622899|
|[v1.8.2-beta.5](https://github.com/electron/electron/releases/tag/v1.8.2-beta.5)|January 31, 2018||yes|57|8.2.1|59.0.3071.115|154271|
|[v1.8.2-beta.4](https://github.com/electron/electron/releases/tag/v1.8.2-beta.4)|January 23, 2018||yes|57|8.2.1|59.0.3071.115|23123|
|[v1.8.2-beta.3](https://github.com/electron/electron/releases/tag/v1.8.2-beta.3)|December 4, 2017||yes|57|8.2.1|59.0.3071.115|39603|
|[v1.8.2-beta.2](https://github.com/electron/electron/releases/tag/v1.8.2-beta.2)|November 6, 2017||yes|57|8.2.1|59.0.3071.115|33588|
|[v1.8.2-beta.1](https://github.com/electron/electron/releases/tag/v1.8.2-beta.1)|October 19, 2017||yes|57|8.2.1|59.0.3071.115|20435|
|[v1.8.1](https://github.com/electron/electron/releases/tag/v1.8.1)|September 29, 2017||yes|57|8.2.1|59.0.3071.115|380986|
|[v1.8.0](https://github.com/electron/electron/releases/tag/v1.8.0)|December 12, 2017||yes|57|8.2.1|59.0.3071.115|1929476|
|[v1.7.16](https://github.com/electron/electron/releases/tag/v1.7.16)|August 22, 2018|1-7-x|no|54|7.9.0|58.0.3029.110|273355|
|[v1.7.15](https://github.com/electron/electron/releases/tag/v1.7.15)|May 16, 2018||no|54|7.9.0|58.0.3029.110|34219|
|[v1.7.14](https://github.com/electron/electron/releases/tag/v1.7.14)|April 27, 2018||no|54|7.9.0|58.0.3029.110|19455|
|[v1.7.13](https://github.com/electron/electron/releases/tag/v1.7.13)|March 15, 2018||no|54|7.9.0|58.0.3029.110|84374|
|[v1.7.12](https://github.com/electron/electron/releases/tag/v1.7.12)|January 31, 2018||no|54|7.9.0|58.0.3029.110|322535|
|[v1.7.11](https://github.com/electron/electron/releases/tag/v1.7.11)|January 23, 2018||no|54|7.9.0|58.0.3029.110|498144|
|[v1.7.10](https://github.com/electron/electron/releases/tag/v1.7.10)|December 18, 2017||no|54|7.9.0|58.0.3029.110|890207|
|[v1.7.9](https://github.com/electron/electron/releases/tag/v1.7.9)|October 11, 2017||no|54|7.9.0|58.0.3029.110|1336784|
|[v1.7.8](https://github.com/electron/electron/releases/tag/v1.7.8)|September 24, 2017||no|54|7.9.0|58.0.3029.110|371188|
|[v1.7.7](https://github.com/electron/electron/releases/tag/v1.7.7)|September 5, 2017||yes|54|7.9.0|58.0.3029.110|150550|
|[v1.7.6](https://github.com/electron/electron/releases/tag/v1.7.6)|August 9, 2017||no|54|7.9.0|58.0.3029.110|457445|
|[v1.7.5](https://github.com/electron/electron/releases/tag/v1.7.5)|July 17, 2017||no|54|7.9.0|58.0.3029.110|446634|
|[v1.7.4](https://github.com/electron/electron/releases/tag/v1.7.4)|June 28, 2017||yes|54|7.9.0|58.0.3029.110|82008|
|[v1.7.3](https://github.com/electron/electron/releases/tag/v1.7.3)|June 8, 2017||yes|54|7.9.0|58.0.3029.110|94360|
|[v1.7.2](https://github.com/electron/electron/releases/tag/v1.7.2)|May 26, 2018||yes|54|7.9.0|58.0.3029.110|51307|
|[v1.7.1](https://github.com/electron/electron/releases/tag/v1.7.1)|May 16, 2018||yes|54|7.9.0|58.0.3029.110|222157|
|[v1.7.0](https://github.com/electron/electron/releases/tag/v1.7.0)|May 10, 2018||yes|54|7.9.0|58.0.3029.110|837863|
|[v1.6.18](https://github.com/electron/electron/releases/tag/v1.6.18)|May 15, 2018||no|53|7.4.0|56.0.2924.87|58431|
|[v1.6.17](https://github.com/electron/electron/releases/tag/v1.6.17)|January 31, 2018||no|53|7.4.0|56.0.2924.87|25814|
|[v1.6.16](https://github.com/electron/electron/releases/tag/v1.6.16)|January 23, 2018||no|53|7.4.0|56.0.2924.87|30015|
|[v1.6.15](https://github.com/electron/electron/releases/tag/v1.6.15)|October 11, 2017||no|53|7.4.0|56.0.2924.87|82529|
|[v1.6.14](https://github.com/electron/electron/releases/tag/v1.6.14)|September 28, 2017||no|53|7.4.0|56.0.2924.87|30227|
|[v1.6.13](https://github.com/electron/electron/releases/tag/v1.6.13)|September 6, 2017||yes|53|7.4.0|56.0.2924.87|45324|
|[v1.6.12](https://github.com/electron/electron/releases/tag/v1.6.12)|September 6, 2017||yes|53|7.4.0|56.0.2924.87|50029|
|[v1.6.11](https://github.com/electron/electron/releases/tag/v1.6.11)|May 25, 2017||no|53|7.4.0|56.0.2924.87|794967|
|[v1.6.10](https://github.com/electron/electron/releases/tag/v1.6.10)|May 16, 2017||no|53|7.4.0|56.0.2924.87|276375|
|[v1.6.9](https://github.com/electron/electron/releases/tag/v1.6.9)|May 10, 2017||no|53|7.4.0|56.0.2924.87|18824|
|[v1.6.8](https://github.com/electron/electron/releases/tag/v1.6.8)|May 1, 2017||no|53|7.4.0|56.0.2924.87|155832|
|[v1.6.7](https://github.com/electron/electron/releases/tag/v1.6.7)|April 18, 2017||no|53|7.4.0|56.0.2924.87|153857|
|[v1.6.6](https://github.com/electron/electron/releases/tag/v1.6.6)|April 7, 2017||no|53|7.4.0|56.0.2924.87|344451|
|[v1.6.5](https://github.com/electron/electron/releases/tag/v1.6.5)|March 31, 2017||no|53|7.4.0|56.0.2924.87|160881|
|[v1.6.4](https://github.com/electron/electron/releases/tag/v1.6.4)|March 22, 2017||yes|53|7.4.0|56.0.2924.87|37122|
|[v1.6.3](https://github.com/electron/electron/releases/tag/v1.6.3)|March 7, 2017||yes|53|7.4.0|56.0.2924.87|58223|
|[v1.6.2](https://github.com/electron/electron/releases/tag/v1.6.2)|March 1, 2017||no|53|7.4.0|56.0.2924.87|622226|
|[v1.6.1](https://github.com/electron/electron/releases/tag/v1.6.1)|February 21, 2017||no|53|7.4.0|56.0.2924.87|222672|
|[v1.6.0](https://github.com/electron/electron/releases/tag/v1.6.0)|February 7, 2017||yes|53|7.4.0|56.0.2924.87|415183|
|[v1.5.1](https://github.com/electron/electron/releases/tag/v1.5.1)|February 6, 2017||yes|51|7.4.0|54.0.2840.101|19119|
|[v1.5.0](https://github.com/electron/electron/releases/tag/v1.5.0)|January 24, 2017||yes|51|7.4.0|54.0.2840.101|208034|
|[v1.4.16](https://github.com/electron/electron/releases/tag/v1.4.16)|April 5, 2017||no|50|6.5.0|53.0.2785.143|255670|
|[v1.4.15](https://github.com/electron/electron/releases/tag/v1.4.15)|January 19, 2017||no|50|6.5.0|53.0.2785.143|1307114|
|[v1.4.14](https://github.com/electron/electron/releases/tag/v1.4.14)|January 10, 2017||no|50|6.5.0|53.0.2785.143|192474|
|[v1.4.13](https://github.com/electron/electron/releases/tag/v1.4.13)|December 20, 2016||no|50|6.5.0|53.0.2785.143|1280942|
|[v1.4.12](https://github.com/electron/electron/releases/tag/v1.4.12)|December 10, 2016||no|50|6.5.0|54.0.2840.51|122997|
|[v1.4.11](https://github.com/electron/electron/releases/tag/v1.4.11)|December 7, 2016||no|50|6.5.0|53.0.2785.143|27759|
|[v1.4.10](https://github.com/electron/electron/releases/tag/v1.4.10)|November 28, 2016||no|50|6.5.0|53.0.2785.143|97710|
|[v1.4.8](https://github.com/electron/electron/releases/tag/v1.4.8)|November 22, 2016||no|50|6.5.0|53.0.2785.143|47028|
|[v1.4.7](https://github.com/electron/electron/releases/tag/v1.4.7)|November 16, 2016||no|50|6.5.0|53.0.2785.143|52064|
|[v1.4.6](https://github.com/electron/electron/releases/tag/v1.4.6)|November 9, 2016||no|50|6.5.0|53.0.2785.143|124977|
|[v1.4.5](https://github.com/electron/electron/releases/tag/v1.4.5)|November 1, 2016||no|50|6.5.0|53.0.2785.113|63149|
|[v1.4.4](https://github.com/electron/electron/releases/tag/v1.4.4)|October 20, 2016||no|50|6.5.0|53.0.2785.113|100649|
|[v1.4.3](https://github.com/electron/electron/releases/tag/v1.4.3)|October 6, 2016||no|50|6.5.0|53.0.2785.113|141522|
|[v1.4.2](https://github.com/electron/electron/releases/tag/v1.4.2)|September 30, 2016||no|50|6.5.0|53.0.2785.113|41885|
|[v1.4.1](https://github.com/electron/electron/releases/tag/v1.4.1)|September 22, 2016||no|50|6.5.0|53.0.2785.113|63398|
|[v1.4.0](https://github.com/electron/electron/releases/tag/v1.4.0)|September 15, 2016||no|50|6.5.0|53.0.2785.113|246174|
|[v1.3.15](https://github.com/electron/electron/releases/tag/v1.3.15)|April 21, 2017||no|49|6.5.0|52.0.2743.82|19628|
|[v1.3.14](https://github.com/electron/electron/releases/tag/v1.3.14)|March 14, 2017||no|49|6.5.0|52.0.2743.82|21153|
|[v1.3.13](https://github.com/electron/electron/releases/tag/v1.3.13)|December 6, 2016||no|49|6.5.0|52.0.2743.82|29477|
|[v1.3.12](https://github.com/electron/electron/releases/tag/v1.3.12)|November 28, 2016||no||||2191|
|[v1.3.10](https://github.com/electron/electron/releases/tag/v1.3.10)|November 22, 2016||no|49|6.5.0|52.0.2743.82|2028|
|[v1.3.9](https://github.com/electron/electron/releases/tag/v1.3.9)|November 16, 2016||no|49|6.5.0|52.0.2743.82|54801|
|[v1.3.8](https://github.com/electron/electron/releases/tag/v1.3.8)|October 20, 2016||no||||36009|
|[v1.3.7](https://github.com/electron/electron/releases/tag/v1.3.7)|September 27, 2016||no|49|6.5.0|52.0.2743.82|13546|
|[v1.3.6](https://github.com/electron/electron/releases/tag/v1.3.6)|September 15, 2016||no|49|6.3.0|52.0.2743.82|39447|
|[v1.3.5](https://github.com/electron/electron/releases/tag/v1.3.5)|September 2, 2016||no|49|6.3.0|52.0.2743.82|92696|
|[v1.3.4](https://github.com/electron/electron/releases/tag/v1.3.4)|August 23, 2016||no|49|6.3.0|52.0.2743.82|110498|
|[v1.3.3](https://github.com/electron/electron/releases/tag/v1.3.3)|August 10, 2016||no|49|6.3.0|52.0.2743.82|135867|
|[v1.3.2](https://github.com/electron/electron/releases/tag/v1.3.2)|August 2, 2016||no|49|6.3.0|52.0.2743.82|77558|
|[v1.3.1](https://github.com/electron/electron/releases/tag/v1.3.1)|July 27, 2016||no|49|6.3.0|52.0.2743.82|135931|
|[v1.3.0](https://github.com/electron/electron/releases/tag/v1.3.0)|July 25, 2016||no|49|6.3.0|52.0.2743.82|133786|
|[v1.2.8](https://github.com/electron/electron/releases/tag/v1.2.8)|July 21, 2016||no|48|6.1.0|51.0.2704.106|114526|
|[v1.2.7](https://github.com/electron/electron/releases/tag/v1.2.7)|July 13, 2016||no|48|6.1.0|51.0.2704.106|69953|
|[v1.2.6](https://github.com/electron/electron/releases/tag/v1.2.6)|July 6, 2016||no|48|6.1.0|51.0.2704.106|75920|
|[v1.2.5](https://github.com/electron/electron/releases/tag/v1.2.5)|June 23, 2016||no|48|6.1.0|51.0.2704.103|78503|
|[v1.2.4](https://github.com/electron/electron/releases/tag/v1.2.4)|June 22, 2016||no|48|6.1.0|51.0.2704.103|30758|
|[v1.2.3](https://github.com/electron/electron/releases/tag/v1.2.3)|June 16, 2016||no|48|6.1.0|51.0.2704.84|54950|
|[v1.2.2](https://github.com/electron/electron/releases/tag/v1.2.2)|June 8, 2016||no|48|6.1.0|51.0.2704.84|156904|
|[v1.2.1](https://github.com/electron/electron/releases/tag/v1.2.1)|June 1, 2016||no|48|6.1.0|51.0.2704.63|65274|
|[v1.2.0](https://github.com/electron/electron/releases/tag/v1.2.0)|May 26, 2016||no|48|6.1.0|51.0.2704.63|120793|
|[v1.1.3](https://github.com/electron/electron/releases/tag/v1.1.3)|May 25, 2016||no|48|6.1.0|50.0.2661.102|76578|
|[v1.1.2](https://github.com/electron/electron/releases/tag/v1.1.2)|May 24, 2016||no|48|6.1.0|50.0.2661.102|31922|
|[v1.1.1](https://github.com/electron/electron/releases/tag/v1.1.1)|May 20, 2016||no|48|6.1.0|50.0.2661.102|74799|
|[v1.1.0](https://github.com/electron/electron/releases/tag/v1.1.0)|May 14, 2016||no|48|6.1.0|50.0.2661.102|83900|
|[v1.0.2](https://github.com/electron/electron/releases/tag/v1.0.2)|May 13, 2016||no|47|5.10.0|49.0.2623.75|50638|
|[v1.0.1](https://github.com/electron/electron/releases/tag/v1.0.1)|May 11, 2016||no|47|5.10.0|49.0.2623.75|44819|
|[v1.0.0](https://github.com/electron/electron/releases/tag/v1.0.0)|May 11, 2016||no|47|5.10.0|49.0.2623.75|155648|
|[v0.37.8](https://github.com/electron/electron/releases/tag/v0.37.8)|April 29, 2016||no|47|5.10.0|49.0.2623.75|277172|
|[v0.37.7](https://github.com/electron/electron/releases/tag/v0.37.7)|April 22, 2016||no|47|5.10.0|49.0.2623.75|58792|
|[v0.37.6](https://github.com/electron/electron/releases/tag/v0.37.6)|April 15, 2016||no|47|5.10.0|49.0.2623.75|98520|
|[v0.37.5](https://github.com/electron/electron/releases/tag/v0.37.5)|April 7, 2016||no|47|5.10.0|49.0.2623.75|58290|
|[v0.37.4](https://github.com/electron/electron/releases/tag/v0.37.4)|April 3, 2016||no|47|6.0.0-pre|49.0.2623.75|61421|
|[v0.37.3](https://github.com/electron/electron/releases/tag/v0.37.3)|March 27, 2016||no|47|5.1.1|49.0.2623.75|201049|
|[v0.37.2](https://github.com/electron/electron/releases/tag/v0.37.2)|March 14, 2016||no||||76810|
|[v0.37.1](https://github.com/electron/electron/releases/tag/v0.37.1)|March 13, 2016||no|47|5.1.1|49.0.2623.75|24507|
|[v0.37.0](https://github.com/electron/electron/releases/tag/v0.37.0)|March 12, 2016||no|47|5.1.1|49.0.2623.75|133669|
|[v0.36.12](https://github.com/electron/electron/releases/tag/v0.36.12)|March 27, 2016||no|47|5.1.1|47.0.2526.110|248377|
|[v0.36.11](https://github.com/electron/electron/releases/tag/v0.36.11)|March 11, 2016||no|47|5.1.1|47.0.2526.110|47235|
|[v0.36.10](https://github.com/electron/electron/releases/tag/v0.36.10)|March 5, 2016||no|47|5.1.1|47.0.2526.110|47888|
|[v0.36.9](https://github.com/electron/electron/releases/tag/v0.36.9)|February 26, 2016||no|47|5.1.1|47.0.2526.110|63097|
|[v0.36.8](https://github.com/electron/electron/releases/tag/v0.36.8)|February 19, 2016||no|47|5.1.1|47.0.2526.110|54267|
|[v0.36.7](https://github.com/electron/electron/releases/tag/v0.36.7)|January 30, 2016||no|47|5.1.1|47.0.2526.110|132407|
|[v0.36.6](https://github.com/electron/electron/releases/tag/v0.36.6)|January 29, 2016||no|47|5.1.1|47.0.2526.110|20357|
|[v0.36.5](https://github.com/electron/electron/releases/tag/v0.36.5)|January 22, 2016||no|47|5.1.1|47.0.2526.110|42706|
|[v0.36.4](https://github.com/electron/electron/releases/tag/v0.36.4)|January 15, 2016||no|47|5.1.1|47.0.2526.73|63742|
|[v0.36.3](https://github.com/electron/electron/releases/tag/v0.36.3)|January 11, 2016||no|47|5.1.1|47.0.2526.73|37232|
|[v0.36.2](https://github.com/electron/electron/releases/tag/v0.36.2)|December 25, 2015||no|47|5.1.1|47.0.2526.73|59918|
|[v0.36.1](https://github.com/electron/electron/releases/tag/v0.36.1)|December 18, 2015||no||||34569|
|[v0.36.0](https://github.com/electron/electron/releases/tag/v0.36.0)|December 11, 2015||no|47|5.1.1|47.0.2526.73|107410|
|[v0.35.6](https://github.com/electron/electron/releases/tag/v0.35.6)|January 11, 2016||no||||126607|
|[v0.35.5](https://github.com/electron/electron/releases/tag/v0.35.5)|December 31, 2015||no|46|4.1.1|45.0.2454.85|18122|
|[v0.35.4](https://github.com/electron/electron/releases/tag/v0.35.4)|December 4, 2015||no|46|4.1.1|45.0.2454.85|89550|
|[v0.35.3](https://github.com/electron/electron/releases/tag/v0.35.3)|December 4, 2015||no|46|4.1.1|45.0.2454.85|55370|
|[v0.35.2](https://github.com/electron/electron/releases/tag/v0.35.2)|November 27, 2015||no|46|4.1.1|45.0.2454.85|38303|
|[v0.35.1](https://github.com/electron/electron/releases/tag/v0.35.1)|November 20, 2015||no|46|4.1.1|45.0.2454.85|36587|
|[v0.35.0](https://github.com/electron/electron/releases/tag/v0.35.0)|November 11, 2015||no||||45073|
|[v0.34.5](https://github.com/electron/electron/releases/tag/v0.34.5)|November 26, 2015||no||||65577|
|[v0.34.4](https://github.com/electron/electron/releases/tag/v0.34.4)|November 24, 2015||no|46|4.1.1|45.0.2454.85|14871|
|[v0.34.3](https://github.com/electron/electron/releases/tag/v0.34.3)|November 6, 2015||no|46|4.1.1|45.0.2454.85|52211|
|[v0.34.2](https://github.com/electron/electron/releases/tag/v0.34.2)|October 30, 2015||no|46|4.1.1|45.0.2454.85|38397|
|[v0.34.1](https://github.com/electron/electron/releases/tag/v0.34.1)|October 23, 2015||no|46|4.1.1|45.0.2454.85|39321|
|[v0.34.0](https://github.com/electron/electron/releases/tag/v0.34.0)|October 16, 2015||no|46|4.1.1|45.0.2454.85|118330|
|[v0.33.9](https://github.com/electron/electron/releases/tag/v0.33.9)|October 16, 2015||no|46|4.1.1|45.0.2454.85|52628|
|[v0.33.8](https://github.com/electron/electron/releases/tag/v0.33.8)|October 14, 2015||no|46|4.1.1|45.0.2454.85|15426|
|[v0.33.7](https://github.com/electron/electron/releases/tag/v0.33.7)|October 10, 2015||no|46|4.1.1|45.0.2454.85|21813|
|[v0.33.6](https://github.com/electron/electron/releases/tag/v0.33.6)|October 5, 2015||no|46|4.1.1|45.0.2454.85|23405|
|[v0.33.5](https://github.com/electron/electron/releases/tag/v0.33.5)|October 5, 2015||no||||12387|
|[v0.33.4](https://github.com/electron/electron/releases/tag/v0.33.4)|October 2, 2015||no|46|4.1.1|45.0.2454.85|17220|
|[v0.33.3](https://github.com/electron/electron/releases/tag/v0.33.3)|September 26, 2015||no|46|4.1.1|45.0.2454.85|31075|
|[v0.33.2](https://github.com/electron/electron/releases/tag/v0.33.2)|September 25, 2015||no|46|4.1.1|45.0.2454.85|13089|
|[v0.33.1](https://github.com/electron/electron/releases/tag/v0.33.1)|September 22, 2015||no|46|4.1.1|45.0.2454.85|16425|
|[v0.33.0](https://github.com/electron/electron/releases/tag/v0.33.0)|September 17, 2015||no|46|5.0.0-pre|45.0.2454.85|31553|
|[v0.32.3](https://github.com/electron/electron/releases/tag/v0.32.3)|September 15, 2015||no|46|5.0.0-pre|45.0.2454.85|21042|
|[v0.32.2](https://github.com/electron/electron/releases/tag/v0.32.2)|September 10, 2015||no|45|3.3.0|45.0.2454.85|15014|
|[v0.32.1](https://github.com/electron/electron/releases/tag/v0.32.1)|September 9, 2015||no||||18179|
|[v0.32.0](https://github.com/electron/electron/releases/tag/v0.32.0)|September 9, 2015||no||||1532|
|[v0.31.2](https://github.com/electron/electron/releases/tag/v0.31.2)|September 2, 2015||no|45|3.3.0|45.0.2454.85|25675|
|[v0.31.1](https://github.com/electron/electron/releases/tag/v0.31.1)|August 28, 2015||no||||9158|
|[v0.31.0](https://github.com/electron/electron/releases/tag/v0.31.0)|August 26, 2015||no|45|3.1.0|44.0.2403.125|6397|
|[v0.30.8](https://github.com/electron/electron/releases/tag/v0.30.8)|September 26, 2015||no||||157284|
|[v0.30.7](https://github.com/electron/electron/releases/tag/v0.30.7)|September 24, 2015||no||||23485|
|[v0.30.6](https://github.com/electron/electron/releases/tag/v0.30.6)|August 26, 2015||no||||10938|
|[v0.30.5](https://github.com/electron/electron/releases/tag/v0.30.5)|August 21, 2015||no||||4108|
|[v0.30.4](https://github.com/electron/electron/releases/tag/v0.30.4)|August 10, 2015||no|45|3.1.0|44.0.2403.125|15364|
|[v0.30.3](https://github.com/electron/electron/releases/tag/v0.30.3)|August 7, 2015||no||||6399|
|[v0.30.2](https://github.com/electron/electron/releases/tag/v0.30.2)|July 30, 2015||no||||25040|
|[v0.30.1](https://github.com/electron/electron/releases/tag/v0.30.1)|July 24, 2015||no||||14765|
|[v0.30.0](https://github.com/electron/electron/releases/tag/v0.30.0)|July 16, 2015||no||||30634|
|[v0.29.2](https://github.com/electron/electron/releases/tag/v0.29.2)|July 7, 2015||no|44|2.3.1|43.0.2357.65|57315|
|[v0.29.1](https://github.com/electron/electron/releases/tag/v0.29.1)|July 3, 2015||no|44|2.3.1|43.0.2357.65|3954|
|[v0.29.0](https://github.com/electron/electron/releases/tag/v0.29.0)|July 3, 2015||no||||2345|
|[v0.28.3](https://github.com/electron/electron/releases/tag/v0.28.3)|June 23, 2015||no|44|2.2.1|43.0.2357.65|26251|
|[v0.28.2](https://github.com/electron/electron/releases/tag/v0.28.2)|June 18, 2015||no|44|2.2.1|43.0.2357.65|7251|
|[v0.28.1](https://github.com/electron/electron/releases/tag/v0.28.1)|June 12, 2015||no|44|2.2.1|43.0.2357.65|8356|
|[v0.28.0](https://github.com/electron/electron/releases/tag/v0.28.0)|June 11, 2015||no|44|2.2.1|43.0.2357.65|1312|
|[v0.27.3](https://github.com/electron/electron/releases/tag/v0.27.3)|June 8, 2015||no|43|1.6.3|43.0.2357.65|15365|
|[v0.27.2](https://github.com/electron/electron/releases/tag/v0.27.2)|June 1, 2015||no|43|1.6.3|43.0.2357.65|6691|
|[v0.27.1](https://github.com/electron/electron/releases/tag/v0.27.1)|May 28, 2015||no|43|1.6.3|42.0.2311.107|3128|
|[v0.27.0](https://github.com/electron/electron/releases/tag/v0.27.0)|May 27, 2015||no|43|1.6.3|42.0.2311.107|1515|
|[v0.26.1](https://github.com/electron/electron/releases/tag/v0.26.1)|May 21, 2015||no|43|1.6.3|42.0.2311.107|12384|
|[v0.26.0](https://github.com/electron/electron/releases/tag/v0.26.0)|May 12, 2015||no|43|1.6.3|42.0.2311.107|10992|
|[v0.25.3](https://github.com/electron/electron/releases/tag/v0.25.3)|May 8, 2015||no|43|1.6.3|42.0.2311.107|16223|
|[v0.25.2](https://github.com/electron/electron/releases/tag/v0.25.2)|May 1, 2015||no|43|1.6.3|42.0.2311.107|8439|
|[v0.25.1](https://github.com/electron/electron/releases/tag/v0.25.1)|April 23, 2015||no|43|1.6.3|42.0.2311.107|15829|
|[v0.25.0](https://github.com/electron/electron/releases/tag/v0.25.0)|April 22, 2015||no|43|1.6.3|42.0.2311.107|1734|
|[v0.24.0](https://github.com/electron/electron/releases/tag/v0.24.0)|April 17, 2015||no|43|1.6.3|41.0.2272.76|8388|
|[v0.23.0](https://github.com/electron/electron/releases/tag/v0.23.0)|April 12, 2015||no|43|1.6.3|41.0.2272.76|3119|
|[v0.22.3](https://github.com/electron/electron/releases/tag/v0.22.3)|March 30, 2015||no|43|1.6.3|41.0.2272.76|40933|
|[v0.22.2](https://github.com/electron/electron/releases/tag/v0.22.2)|March 23, 2015||no|43|1.5.1|41.0.2272.76|1642|
|[v0.22.1](https://github.com/electron/electron/releases/tag/v0.22.1)|March 18, 2015||no|43|1.5.1|41.0.2272.76|4267|
|[v0.22.0](https://github.com/electron/electron/releases/tag/v0.22.0)|March 18, 2015||no||||33571|
|[v0.21.3](https://github.com/electron/electron/releases/tag/v0.21.3)|March 3, 2015||no|43|1.5.1|41.0.2272.76|8404|
|[v0.21.2](https://github.com/electron/electron/releases/tag/v0.21.2)|February 5, 2015||no|41|1.0.0-pre|40.0.2214.91|4489|
|[v0.21.1](https://github.com/electron/electron/releases/tag/v0.21.1)|February 3, 2015||no|41|1.0.0-pre|40.0.2214.91|1632|
|[v0.21.0](https://github.com/electron/electron/releases/tag/v0.21.0)|January 28, 2015||no|41|1.0.0-pre|40.0.2214.91|13170|
|[v0.20.8](https://github.com/electron/electron/releases/tag/v0.20.8)|January 27, 2015||no|17|0.13.0-pre|39.0.2171.65|324|
|[v0.20.7](https://github.com/electron/electron/releases/tag/v0.20.7)|January 20, 2015||no|17|0.13.0-pre|39.0.2171.65|1897|
|[v0.20.6](https://github.com/electron/electron/releases/tag/v0.20.6)|January 19, 2015||no|17|0.13.0-pre|39.0.2171.65|1520|
|[v0.20.5](https://github.com/electron/electron/releases/tag/v0.20.5)|January 8, 2015||no|17|0.13.0-pre|39.0.2171.65|4711|
|[v0.20.4](https://github.com/electron/electron/releases/tag/v0.20.4)|January 6, 2015||no|17|0.13.0-pre|39.0.2171.65|1472|
|[v0.20.3](https://github.com/electron/electron/releases/tag/v0.20.3)|December 29, 2014||no|17|0.13.0-pre|39.0.2171.65|2957|
|[v0.20.2](https://github.com/electron/electron/releases/tag/v0.20.2)|December 22, 2014||no|17|0.13.0-pre|39.0.2171.65|2698|
|[v0.20.1](https://github.com/electron/electron/releases/tag/v0.20.1)|December 18, 2014||no|17|0.13.0-pre|39.0.2171.65|1327|
|[v0.20.0](https://github.com/electron/electron/releases/tag/v0.20.0)|December 13, 2014||no|17|0.13.0-pre|39.0.2171.65|1184|
|[v0.19.5](https://github.com/electron/electron/releases/tag/v0.19.5)|November 28, 2014||no||||7681|
|[v0.19.4](https://github.com/electron/electron/releases/tag/v0.19.4)|November 21, 2014||no||||7491|
|[v0.19.3](https://github.com/electron/electron/releases/tag/v0.19.3)|November 20, 2014||no||||397|
|[v0.19.2](https://github.com/electron/electron/releases/tag/v0.19.2)|November 15, 2014||no||||2919|
|[v0.19.1](https://github.com/electron/electron/releases/tag/v0.19.1)|November 4, 2014||no||||4267|
|[v0.19.0](https://github.com/electron/electron/releases/tag/v0.19.0)|October 30, 2014||no||||1133|
|[v0.18.2](https://github.com/electron/electron/releases/tag/v0.18.2)|October 21, 2014||no||||4474|
|[v0.18.1](https://github.com/electron/electron/releases/tag/v0.18.1)|October 17, 2014||no||||2316|
|[v0.18.0](https://github.com/electron/electron/releases/tag/v0.18.0)|October 14, 2014||no||||2105|
|[v0.17.2](https://github.com/electron/electron/releases/tag/v0.17.2)|October 6, 2014||no||||1848|
|[v0.17.1](https://github.com/electron/electron/releases/tag/v0.17.1)|October 1, 2014||no||||4126|
|[v0.17.0](https://github.com/electron/electron/releases/tag/v0.17.0)|October 1, 2014||no||||378|
|[v0.16.3](https://github.com/electron/electron/releases/tag/v0.16.3)|September 20, 2014||no||||1191|
|[v0.16.2](https://github.com/electron/electron/releases/tag/v0.16.2)|September 9, 2014||no||||5577|
|[v0.16.1](https://github.com/electron/electron/releases/tag/v0.16.1)|September 8, 2014||no||||506|
|[v0.16.0](https://github.com/electron/electron/releases/tag/v0.16.0)|September 6, 2014||no||||480|
|[v0.15.9](https://github.com/electron/electron/releases/tag/v0.15.9)|August 20, 2014||no||||6613|
|[v0.15.8](https://github.com/electron/electron/releases/tag/v0.15.8)|August 18, 2014||no||||8126|
|[v0.15.7](https://github.com/electron/electron/releases/tag/v0.15.7)|August 15, 2014||no||||9036|
|[v0.15.6](https://github.com/electron/electron/releases/tag/v0.15.6)|August 13, 2014||no||||10370|
|[v0.15.5](https://github.com/electron/electron/releases/tag/v0.15.5)|August 11, 2014||no||||8040|
|[v0.15.4](https://github.com/electron/electron/releases/tag/v0.15.4)|August 7, 2014||no||||8422|
|[v0.15.3](https://github.com/electron/electron/releases/tag/v0.15.3)|August 6, 2014||no||||10162|
|[v0.15.2](https://github.com/electron/electron/releases/tag/v0.15.2)|August 4, 2014||no||||7907|
|[v0.15.1](https://github.com/electron/electron/releases/tag/v0.15.1)|July 31, 2014||no||||8344|
|[v0.15.0](https://github.com/electron/electron/releases/tag/v0.15.0)|July 29, 2014||no||||8086|
|[v0.14.3](https://github.com/electron/electron/releases/tag/v0.14.3)|July 27, 2014||no||||7609|
|[v0.14.2](https://github.com/electron/electron/releases/tag/v0.14.2)|July 25, 2014||no||||7439|
|[v0.14.1](https://github.com/electron/electron/releases/tag/v0.14.1)|July 24, 2014||no||||7409|
|[v0.14.0](https://github.com/electron/electron/releases/tag/v0.14.0)|July 22, 2014||no||||7657|
|[v0.13.3](https://github.com/electron/electron/releases/tag/v0.13.3)|June 25, 2014||no||||15531|
|[v0.13.2](https://github.com/electron/electron/releases/tag/v0.13.2)|June 18, 2014||no||||4130|
|[v0.13.1](https://github.com/electron/electron/releases/tag/v0.13.1)|June 14, 2014||no||||2075|
|[v0.13.0](https://github.com/electron/electron/releases/tag/v0.13.0)|June 5, 2014||no||||3921|
|[v0.12.7](https://github.com/electron/electron/releases/tag/v0.12.7)|May 27, 2014||no||||4807|
|[v0.12.6](https://github.com/electron/electron/releases/tag/v0.12.6)|May 26, 2014||no||||413|
|[v0.12.5](https://github.com/electron/electron/releases/tag/v0.12.5)|May 19, 2014||no||||21269|
|[v0.12.4](https://github.com/electron/electron/releases/tag/v0.12.4)|May 12, 2014||no||||20172|
|[v0.12.3](https://github.com/electron/electron/releases/tag/v0.12.3)|May 7, 2014||no||||6487|
|[v0.12.2](https://github.com/electron/electron/releases/tag/v0.12.2)|May 5, 2014||no||||5097|
|[v0.12.1](https://github.com/electron/electron/releases/tag/v0.12.1)|May 5, 2014||no||||316|
|[v0.12.0](https://github.com/electron/electron/releases/tag/v0.12.0)|April 29, 2014||no||||286|
|[v0.11.10](https://github.com/electron/electron/releases/tag/v0.11.10)|April 14, 2014||no||||194|
|[v0.11.9](https://github.com/electron/electron/releases/tag/v0.11.9)|April 11, 2014||no||||186|
|[v0.11.8](https://github.com/electron/electron/releases/tag/v0.11.8)|April 10, 2014||no||||182|
|[v0.11.7](https://github.com/electron/electron/releases/tag/v0.11.7)|April 8, 2014||no||||184|
|[v0.11.6](https://github.com/electron/electron/releases/tag/v0.11.6)|April 7, 2014||no||||183|
|[v0.11.5](https://github.com/electron/electron/releases/tag/v0.11.5)|April 2, 2014||no||||189|
|[v0.11.4](https://github.com/electron/electron/releases/tag/v0.11.4)|March 28, 2014||no||||277|
|[v0.11.3](https://github.com/electron/electron/releases/tag/v0.11.3)|March 25, 2014||no||||266|
|[v0.11.2](https://github.com/electron/electron/releases/tag/v0.11.2)|March 24, 2024||no||||273|
|[v0.11.1](https://github.com/electron/electron/releases/tag/v0.11.1)|March 18, 2014||no||||269|
|[v0.11.0](https://github.com/electron/electron/releases/tag/v0.11.0)|March 16, 2014||no||||269|
|[v0.10.7](https://github.com/electron/electron/releases/tag/v0.10.7)|March 11, 2014||no||||310|
|[v0.10.6](https://github.com/electron/electron/releases/tag/v0.10.6)|March 7, 2014||no||||270|
|[v0.10.5](https://github.com/electron/electron/releases/tag/v0.10.5)|March 5, 2014||no||||268|
|[v0.10.4](https://github.com/electron/electron/releases/tag/v0.10.4)|March 2, 2014||no||||259|
|[v0.10.3](https://github.com/electron/electron/releases/tag/v0.10.3)|February 28, 2014||no||||342|
|[v0.10.2](https://github.com/electron/electron/releases/tag/v0.10.2)|February 27, 2014||no||||303|
|[v0.10.1](https://github.com/electron/electron/releases/tag/v0.10.1)|February 25, 2014||no||||290|
|[v0.10.0](https://github.com/electron/electron/releases/tag/v0.10.0)|February 24, 2014||no||||104|
|[v0.9.3](https://github.com/electron/electron/releases/tag/v0.9.3)|February 17, 2014||no||||3727|
|[v0.9.2](https://github.com/electron/electron/releases/tag/v0.9.2)|February 12, 2014||no||||3740|
|[v0.9.1](https://github.com/electron/electron/releases/tag/v0.9.1)|February 4, 2014||no||||3728|
|[v0.9.0](https://github.com/electron/electron/releases/tag/v0.9.0)|February 2, 2014||no||||3716|
|[v0.8.7](https://github.com/electron/electron/releases/tag/v0.8.7)|January 27, 2014||no||||3750|
|[v0.8.6](https://github.com/electron/electron/releases/tag/v0.8.6)|January 23, 2014||no||||3731|
|[v0.8.5](https://github.com/electron/electron/releases/tag/v0.8.5)|January 14, 2014||no||||3759|
|[v0.8.4](https://github.com/electron/electron/releases/tag/v0.8.4)|January 13, 2014||no||||3737|
|[v0.8.3](https://github.com/electron/electron/releases/tag/v0.8.3)|January 8, 2014||no||||1867|
|[v0.8.2](https://github.com/electron/electron/releases/tag/v0.8.2)|January 7, 2014||no||||3813|
|[v0.8.1](https://github.com/electron/electron/releases/tag/v0.8.1)|December 29, 2013||no||||3751|
|[v0.8.0](https://github.com/electron/electron/releases/tag/v0.8.0)|December 27, 2013||no||||1873|
|[v0.7.6](https://github.com/electron/electron/releases/tag/v0.7.6)|December 9, 2013||no||||3828|
|[v0.7.5](https://github.com/electron/electron/releases/tag/v0.7.5)|December 5, 2013||no||||3732|
|[v0.7.4](https://github.com/electron/electron/releases/tag/v0.7.4)|December 4, 2013||no||||3811|
|[v0.7.3](https://github.com/electron/electron/releases/tag/v0.7.3)|November 29, 2013||no||||3823|
|[v0.7.2](https://github.com/electron/electron/releases/tag/v0.7.2)|November 28, 2013||no||||3772|
|[v0.7.1](https://github.com/electron/electron/releases/tag/v0.7.1)|November 28, 2013||no||||3762|
|[v0.7.0](https://github.com/electron/electron/releases/tag/v0.7.0)|November 27, 2013||no||||3749|
|[v0.6.12](https://github.com/electron/electron/releases/tag/v0.6.12)|November 22, 2013||no||||1872|
|[v0.6.11](https://github.com/electron/electron/releases/tag/v0.6.11)|November 20, 2013||no||||1873|
|[v0.6.10](https://github.com/electron/electron/releases/tag/v0.6.10)|November 11, 2013||no||||1883|
|[v0.6.9](https://github.com/electron/electron/releases/tag/v0.6.9)|November 7, 2013||no||||1877|
|[v0.6.8](https://github.com/electron/electron/releases/tag/v0.6.8)|November 5, 2013||no||||1858|
|[v0.6.7](https://github.com/electron/electron/releases/tag/v0.6.7)|November 2, 2013||no||||1867|
|[v0.6.6](https://github.com/electron/electron/releases/tag/v0.6.6)|October 28, 2013||no||||1879|
|[v0.6.5](https://github.com/electron/electron/releases/tag/v0.6.5)|October 26, 2013||no||||1834|
|[v0.6.4](https://github.com/electron/electron/releases/tag/v0.6.4)|October 22, 2013||no||||1873|
|[v0.6.3](https://github.com/electron/electron/releases/tag/v0.6.3)|October 21, 2013||no||||913|
|[v0.6.2](https://github.com/electron/electron/releases/tag/v0.6.2)|October 17, 2013||no||||916|
|[v0.6.1](https://github.com/electron/electron/releases/tag/v0.6.1)|October 14, 2013||no||||916|
|[v0.6.0](https://github.com/electron/electron/releases/tag/v0.6.0)|October 10, 2013||no||||919|
|[v0.5.4](https://github.com/electron/electron/releases/tag/v0.5.4)|October 4, 2013||no||||942|
|[v0.5.3](https://github.com/electron/electron/releases/tag/v0.5.3)|September 29, 2013||no||||903|
|[v0.5.2](https://github.com/electron/electron/releases/tag/v0.5.2)|September 29, 2013||no||||905|
|[v0.5.1](https://github.com/electron/electron/releases/tag/v0.5.1)|September 26, 2013||no||||924|
|[v0.5.0](https://github.com/electron/electron/releases/tag/v0.5.0)|September 25, 2013||no||||913|
|[v0.4.9](https://github.com/electron/electron/releases/tag/v0.4.9)|September 20, 2013||no||||904|
|[v0.4.8](https://github.com/electron/electron/releases/tag/v0.4.8)|September 20, 2013||no||||903|
|[v0.4.7](https://github.com/electron/electron/releases/tag/v0.4.7)|September 13, 2013||no||||905|
|[v0.4.6](https://github.com/electron/electron/releases/tag/v0.4.6)|September 12, 2013||no||||907|
|[v0.4.5](https://github.com/electron/electron/releases/tag/v0.4.5)|September 9, 2013||no||||907|
|[v0.4.4](https://github.com/electron/electron/releases/tag/v0.4.4)|September 5, 2013||no||||907|
|[v0.4.3](https://github.com/electron/electron/releases/tag/v0.4.3)|September 2, 2013||no||||906|
|[v0.4.2](https://github.com/electron/electron/releases/tag/v0.4.2)|September 2, 2013||no||||1832|
|[v0.4.1](https://github.com/electron/electron/releases/tag/v0.4.1)|August 27, 2013||no||||0|
|[v0.4.0](https://github.com/electron/electron/releases/tag/v0.4.0)|August 19, 2023||no||||0|
|[v0.3.5](https://github.com/electron/electron/releases/tag/v0.3.5)|August 16, 2013||no||||0|
|[v0.3.4](https://github.com/electron/electron/releases/tag/v0.3.4)|August 15, 2013||no||||0|
|[v0.3.3](https://github.com/electron/electron/releases/tag/v0.3.3)|August 15, 2013||no||||0|
|[v0.3.2](https://github.com/electron/electron/releases/tag/v0.3.2)|August 13, 2013||no||||0|
|[v0.3.1](https://github.com/electron/electron/releases/tag/v0.3.1)|August 12, 2013||no||||0|

<!-- END RELEASES TABLE -->
