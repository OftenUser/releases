# electron-releases

[![Greenkeeper badge](https://badges.greenkeeper.io/electron/releases.svg)](https://greenkeeper.io/)

> Complete and up-to-date info about every release of Electron.

This package:

- includes all [GitHub Releases](https://developer.github.com/v3/repos/releases/#get-a-single-release) data about Electron.
- does not include draft releases.
- includes prereleases which are not published to npm.
- tracks which versions are published to npm.
- tracks [npm dist-tags](https://docs.npmjs.com/cli/dist-tag) like `latest` and `beta`.
- includes V8, Chromium, and Node.js version data.
- includes [GitHub-flavored HTML](https://ghub.io/hubdown) for each release's changelog.
- ignores npm versions from the days before [Electron was `electron`](https://electronjs.org/blog/npm-install-electron).
- is [updated regularly](#updates).

## Sources

This module collects metadata from various sources:

- [GitHub Releases of `electron/electron`](https://github.com/electron/electron)
- [dist-tags from npm registry for `electron`](https://registry.npmjs.com/electron)
- [dist-tags from npm registry `electron-prebuilt`](https://registry.npmjs.com/electron-prebuilt)
- [Dependency data for Chromium, Node.js, V8, etc](https://atom.io/download/electron/index.json)

## Releases

<!-- START RELEASES TABLE -->
|Tag|Published|npm|Prerelease|Node|Chrome|Downloads|
|----|----|----|----|----|----|----|
|[v8.0.0-nightly.20191006](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20191006)|2019-10-06|nightly|yes|12.9.1|79|6|
|[v8.0.0-nightly.20191005](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20191005)|2019-10-05||yes|12.9.1|79|7|
|[v8.0.0-nightly.20191004](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20191004)|2019-10-04||yes|12.9.1|79|6|
|[v8.0.0-nightly.20191001](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20191001)|2019-10-01||yes|12.9.1|79|15|
|[v8.0.0-nightly.20190930](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190930)|2019-09-30||yes|12.9.1|79|11|
|[v8.0.0-nightly.20190929](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190929)|2019-09-29||yes|12.9.1|79|9|
|[v8.0.0-nightly.20190926](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190926)|2019-09-26||yes|12.9.1|79|12|
|[v8.0.0-nightly.20190924](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190924)|2019-09-24||yes|12.9.1|79|9|
|[v8.0.0-nightly.20190923](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190923)|2019-09-23||yes|12.9.1|79|10|
|[v8.0.0-nightly.20190920](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190920)|2019-09-20||yes|12.9.1|79|19|
|[v8.0.0-nightly.20190919](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190919)|2019-09-19||yes|12.9.1|79|11|
|[v8.0.0-nightly.20190917](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190917)|2019-09-17||yes|12.9.1|78|9|
|[v8.0.0-nightly.20190915](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190915)|2019-09-15||yes|12.9.1|78|6|
|[v8.0.0-nightly.20190914](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190914)|2019-09-14||yes|12.9.1|78|10|
|[v8.0.0-nightly.20190913](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190913)|2019-09-13||yes|12.9.1|78|8|
|[v8.0.0-nightly.20190911](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190911)|2019-09-11||yes|12.9.1|78|7|
|[v8.0.0-nightly.20190910](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190910)|2019-09-10||yes|12.9.1|78|9|
|[v8.0.0-nightly.20190909](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190909)|2019-09-09||yes|12.9.1|78|8|
|[v8.0.0-nightly.20190907](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190907)|2019-09-08||yes|12.9.1|78|7|
|[v8.0.0-nightly.20190902](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190902)|2019-09-02||yes|12.9.1|78|12|
|[v8.0.0-nightly.20190901](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190901)|2019-09-01||yes|12.9.1|78|29|
|[v8.0.0-nightly.20190830](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190830)|2019-08-30||yes|12.9.1|78|17|
|[v8.0.0-nightly.20190828](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190828)|2019-08-28||yes|12.9.1|78|9|
|[v8.0.0-nightly.20190827](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190827)|2019-08-28||yes|12.9.1|78|7|
|[v8.0.0-nightly.20190825](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190825)|2019-08-25||yes|12.9.0|78|22|
|[v8.0.0-nightly.20190824](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190824)|2019-08-24||yes|12.9.0|78|6|
|[v8.0.0-nightly.20190820](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190820)|2019-08-20||yes|12.8.1|78|8|
|[v8.0.0-nightly.20190819](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190819)|2019-08-20||yes|12.8.0|78|19|
|[v8.0.0-nightly.20190818](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190818)|2019-08-18||yes|12.8.0|78|7|
|[v8.0.0-nightly.20190817](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190817)|2019-08-17||yes|12.8.0|78|7|
|[v8.0.0-nightly.20190816](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190816)|2019-08-16||yes|12.8.0|78|9|
|[v8.0.0-nightly.20190815](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190815)|2019-08-15||yes|12.8.0|78|8|
|[v8.0.0-nightly.20190814](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190814)|2019-08-14||yes|12.8.0|78|10|
|[v8.0.0-nightly.20190813](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190813)|2019-08-13||yes|12.8.0|78|12|
|[v8.0.0-nightly.20190812](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190812)|2019-08-12||yes|12.6.0|78|8|
|[v8.0.0-nightly.20190811](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190811)|2019-08-12||yes|12.6.0|78|9|
|[v8.0.0-nightly.20190810](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190810)|2019-08-11||yes|12.6.0|78|8|
|[v8.0.0-nightly.20190809](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190809)|2019-08-09||yes|12.6.0|78|8|
|[v8.0.0-nightly.20190808](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190808)|2019-08-08||yes|12.6.0|78|11|
|[v8.0.0-nightly.20190807](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190807)|2019-08-07||yes|12.6.0|78|10|
|[v8.0.0-nightly.20190806](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190806)|2019-08-06||yes|12.6.0|78|9|
|[v8.0.0-nightly.20190803](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190803)|2019-08-04||yes|12.6.0|78|29|
|[v8.0.0-nightly.20190802](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190802)|2019-08-02||yes|12.6.0|78|10|
|[v8.0.0-nightly.20190801](https://github.com/electron/electron/releases/tag/v8.0.0-nightly.20190801)|2019-08-01||yes|12.6.0|78|6|
|[v7.0.0-nightly.20190731](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190731)|2019-07-31||yes|12.6.0|78|27|
|[v7.0.0-nightly.20190730](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190730)|2019-07-30||yes|12.6.0|78|20|
|[v7.0.0-nightly.20190729](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190729)|2019-07-29||yes|12.6.0|78|15|
|[v7.0.0-nightly.20190728](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190728)|2019-07-28||yes|12.6.0|78|11|
|[v7.0.0-nightly.20190727](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190727)|2019-07-27||yes|12.6.0|78|15|
|[v7.0.0-nightly.20190726](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190726)|2019-07-26||yes|12.6.0|77|10|
|[v7.0.0-nightly.20190721](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190721)|2019-07-21||yes|12.6.0|77|62|
|[v7.0.0-nightly.20190720](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190720)|2019-07-20||yes|12.6.0|77|12|
|[v7.0.0-nightly.20190719](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190719)|2019-07-19||yes|12.6.0|77|9|
|[v7.0.0-nightly.20190705](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190705)|2019-07-05||yes|12.0.0|77|12|
|[v7.0.0-nightly.20190704](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190704)|2019-07-04||yes|12.0.0|77|48|
|[v7.0.0-nightly.20190702](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190702)|2019-07-02||yes|12.0.0|77|13|
|[v7.0.0-nightly.20190701](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190701)|2019-07-01||yes|12.0.0|77|8|
|[v7.0.0-nightly.20190630](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190630)|2019-07-01||yes|12.0.0|77|7|
|[v7.0.0-nightly.20190629](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190629)|2019-06-29||yes|12.0.0|77|8|
|[v7.0.0-nightly.20190627](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190627)|2019-06-27||yes|12.0.0|77|10|
|[v7.0.0-nightly.20190624](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190624)|2019-06-24||yes|12.0.0|77|15|
|[v7.0.0-nightly.20190623](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190623)|2019-06-23||yes|12.0.0|77|7|
|[v7.0.0-nightly.20190622](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190622)|2019-06-22||yes|12.0.0|77|9|
|[v7.0.0-nightly.20190619](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190619)|2019-06-19||yes|12.0.0|77|14|
|[v7.0.0-nightly.20190618](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190618)|2019-06-18||yes|12.0.0|77|11|
|[v7.0.0-nightly.20190616](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190616)|2019-06-16||yes|12.0.0|77|17|
|[v7.0.0-nightly.20190615](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190615)|2019-06-15||yes|12.0.0|77|9|
|[v7.0.0-nightly.20190613](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190613)|2019-06-13||yes|12.0.0|77|10|
|[v7.0.0-nightly.20190612](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190612)|2019-06-12||yes|12.0.0|77|13|
|[v7.0.0-nightly.20190611](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190611)|2019-06-11||yes|12.0.0|77|10|
|[v7.0.0-nightly.20190609](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190609)|2019-06-09||yes|12.0.0|77|6|
|[v7.0.0-nightly.20190608](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190608)|2019-06-08||yes|12.0.0|77|10|
|[v7.0.0-nightly.20190607](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190607)|2019-06-07||yes|12.0.0|77|12|
|[v7.0.0-nightly.20190606](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190606)|2019-06-06||yes|12.0.0|77|11|
|[v7.0.0-nightly.20190605](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190605)|2019-06-05||yes|12.0.0|77|8|
|[v7.0.0-nightly.20190604](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190604)|2019-06-04||yes|12.0.0|77|7|
|[v7.0.0-nightly.20190603](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190603)|2019-06-03||yes|12.0.0|76|8|
|[v7.0.0-nightly.20190602](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190602)|2019-06-02||yes|12.0.0|76|10|
|[v7.0.0-nightly.20190531](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190531)|2019-05-31||yes|12.0.0|76|11|
|[v7.0.0-nightly.20190530](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190530)|2019-05-30||yes|12.0.0|76|12|
|[v7.0.0-nightly.20190529](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190529)|2019-05-29||yes|12.0.0|76|13|
|[v7.0.0-nightly.20190521](https://github.com/electron/electron/releases/tag/v7.0.0-nightly.20190521)|2019-05-21||yes|12.0.0|76|63|
|[v7.0.0-beta.5](https://github.com/electron/electron/releases/tag/v7.0.0-beta.5)|2019-09-24|beta, beta-7-0-x|yes|12.8.1|78|360|
|[v7.0.0-beta.4](https://github.com/electron/electron/releases/tag/v7.0.0-beta.4)|2019-09-03||yes|12.8.1|78|663|
|[v7.0.0-beta.3](https://github.com/electron/electron/releases/tag/v7.0.0-beta.3)|2019-08-15||yes|12.8.0|78|655|
|[v7.0.0-beta.2](https://github.com/electron/electron/releases/tag/v7.0.0-beta.2)|2019-08-07||yes|12.6.0|78|290|
|[v7.0.0-beta.1](https://github.com/electron/electron/releases/tag/v7.0.0-beta.1)|2019-08-01||yes|12.6.0|78|302|
|[v6.0.11](https://github.com/electron/electron/releases/tag/v6.0.11)|2019-10-02|latest, 6-0-x|no|12.4.0|76|5855|
|[v6.0.10](https://github.com/electron/electron/releases/tag/v6.0.10)|2019-09-19||no|12.4.0|76|17691|
|[v6.0.9](https://github.com/electron/electron/releases/tag/v6.0.9)|2019-09-12||no|12.4.0|76|12272|
|[v6.0.8](https://github.com/electron/electron/releases/tag/v6.0.8)|2019-09-09||no|12.4.0|76|6442|
|[v6.0.7](https://github.com/electron/electron/releases/tag/v6.0.7)|2019-08-31||no|12.4.0|76|18540|
|[v6.0.6](https://github.com/electron/electron/releases/tag/v6.0.6)|2019-08-30||no|12.4.0|76|2352|
|[v6.0.5](https://github.com/electron/electron/releases/tag/v6.0.5)|2019-08-27||no|12.4.0|76|8557|
|[v6.0.4](https://github.com/electron/electron/releases/tag/v6.0.4)|2019-08-24||no|12.4.0|76|6348|
|[v6.0.3](https://github.com/electron/electron/releases/tag/v6.0.3)|2019-08-20||no|12.4.0|76|8373|
|[v6.0.2](https://github.com/electron/electron/releases/tag/v6.0.2)|2019-08-12||no|12.4.0|76|12534|
|[v6.0.1](https://github.com/electron/electron/releases/tag/v6.0.1)|2019-08-07||no|12.4.0|76|9270|
|[v6.0.0](https://github.com/electron/electron/releases/tag/v6.0.0)|2019-07-29||no|12.4.0|76|23373|
|[v6.0.0-nightly.20190311](https://github.com/electron/electron/releases/tag/v6.0.0-nightly.20190311)|2019-03-11||yes|12.0.0|74|269|
|[v6.0.0-nightly.20190213](https://github.com/electron/electron/releases/tag/v6.0.0-nightly.20190213)|2019-02-14||yes|12.0.0|72|194|
|[v6.0.0-nightly.20190212](https://github.com/electron/electron/releases/tag/v6.0.0-nightly.20190212)|2019-02-12||yes|12.0.0|72|9|
|[v6.0.0-beta.15](https://github.com/electron/electron/releases/tag/v6.0.0-beta.15)|2019-07-20|beta-6-0-x|yes|12.4.0|76|684|
|[v6.0.0-beta.14](https://github.com/electron/electron/releases/tag/v6.0.0-beta.14)|2019-07-17||yes|12.4.0|76|425|
|[v6.0.0-beta.13](https://github.com/electron/electron/releases/tag/v6.0.0-beta.13)|2019-07-10||yes|12.0.0|76|480|
|[v6.0.0-beta.12](https://github.com/electron/electron/releases/tag/v6.0.0-beta.12)|2019-07-04||yes|12.0.0|76|572|
|[v6.0.0-beta.11](https://github.com/electron/electron/releases/tag/v6.0.0-beta.11)|2019-06-26||yes|12.0.0|76|372|
|[v6.0.0-beta.10](https://github.com/electron/electron/releases/tag/v6.0.0-beta.10)|2019-06-22||yes|12.0.0|76|400|
|[v6.0.0-beta.9](https://github.com/electron/electron/releases/tag/v6.0.0-beta.9)|2019-06-18||yes|12.0.0|76|306|
|[v6.0.0-beta.8](https://github.com/electron/electron/releases/tag/v6.0.0-beta.8)|2019-06-14||yes|12.0.0|76|230|
|[v6.0.0-beta.7](https://github.com/electron/electron/releases/tag/v6.0.0-beta.7)|2019-06-11||yes|12.0.0|76|286|
|[v6.0.0-beta.6](https://github.com/electron/electron/releases/tag/v6.0.0-beta.6)|2019-06-05||yes|12.0.0|76|284|
|[v6.0.0-beta.5](https://github.com/electron/electron/releases/tag/v6.0.0-beta.5)|2019-05-29||yes|12.0.0|76|220|
|[v6.0.0-beta.4](https://github.com/electron/electron/releases/tag/v6.0.0-beta.4)|2019-05-21||yes|12.0.0|76|311|
|[v6.0.0-beta.3](https://github.com/electron/electron/releases/tag/v6.0.0-beta.3)|2019-05-14||yes|12.0.0|76|1234|
|[v6.0.0-beta.2](https://github.com/electron/electron/releases/tag/v6.0.0-beta.2)|2019-05-08||yes|12.0.0|76|315|
|[v6.0.0-beta.1](https://github.com/electron/electron/releases/tag/v6.0.0-beta.1)|2019-05-01||yes|12.0.0|76|299|
|[v5.0.11](https://github.com/electron/electron/releases/tag/v5.0.11)|2019-09-24|5-0-x|no|12.0.0|73|4487|
|[v5.0.10](https://github.com/electron/electron/releases/tag/v5.0.10)|2019-08-20||no|12.0.0|73|17122|
|[v5.0.9](https://github.com/electron/electron/releases/tag/v5.0.9)|2019-08-06||no|12.0.0|73|7648|
|[v5.0.8](https://github.com/electron/electron/releases/tag/v5.0.8)|2019-07-23||no|12.0.0|73|16519|
|[v5.0.7](https://github.com/electron/electron/releases/tag/v5.0.7)|2019-07-16||no|12.0.0|73|15708|
|[v5.0.6](https://github.com/electron/electron/releases/tag/v5.0.6)|2019-06-26||no|12.0.0|73|40194|
|[v5.0.5](https://github.com/electron/electron/releases/tag/v5.0.5)|2019-06-21||no|12.0.0|73|14002|
|[v5.0.4](https://github.com/electron/electron/releases/tag/v5.0.4)|2019-06-15||no|12.0.0|73|16092|
|[v5.0.3](https://github.com/electron/electron/releases/tag/v5.0.3)|2019-06-07||no|12.0.0|73|12673|
|[v5.0.2](https://github.com/electron/electron/releases/tag/v5.0.2)|2019-05-23||no|12.0.0|73|31480|
|[v5.0.1](https://github.com/electron/electron/releases/tag/v5.0.1)|2019-05-04||no|12.0.0|73|49594|
|[v5.0.0](https://github.com/electron/electron/releases/tag/v5.0.0)|2019-04-24||no|12.0.0|73|23064|
|[v5.0.0-nightly.20190122](https://github.com/electron/electron/releases/tag/v5.0.0-nightly.20190122)|2019-01-22||yes|12.0.0|71|23|
|[v5.0.0-nightly.20190121](https://github.com/electron/electron/releases/tag/v5.0.0-nightly.20190121)|2019-01-22||yes|12.0.0|71|35|
|[v5.0.0-nightly.20190107](https://github.com/electron/electron/releases/tag/v5.0.0-nightly.20190107)|2019-01-08||yes|11.0.0|70|97|
|[v5.0.0-beta.9](https://github.com/electron/electron/releases/tag/v5.0.0-beta.9)|2019-04-20|beta-5-0-x|yes|12.0.0|73|548|
|[v5.0.0-beta.8](https://github.com/electron/electron/releases/tag/v5.0.0-beta.8)|2019-04-04||yes|12.0.0|73|1389|
|[v5.0.0-beta.7](https://github.com/electron/electron/releases/tag/v5.0.0-beta.7)|2019-03-28||yes|12.0.0|73|3435|
|[v5.0.0-beta.6](https://github.com/electron/electron/releases/tag/v5.0.0-beta.6)|2019-03-20||yes|12.0.0|73|663|
|[v5.0.0-beta.5](https://github.com/electron/electron/releases/tag/v5.0.0-beta.5)|2019-03-05||yes|12.0.0|73|742|
|[v5.0.0-beta.4](https://github.com/electron/electron/releases/tag/v5.0.0-beta.4)|2019-02-27||yes|12.0.0|73|474|
|[v5.0.0-beta.3](https://github.com/electron/electron/releases/tag/v5.0.0-beta.3)|2019-02-15||yes|12.0.0|73|801|
|[v5.0.0-beta.2](https://github.com/electron/electron/releases/tag/v5.0.0-beta.2)|2019-02-04||yes|12.0.0|72|761|
|[v5.0.0-beta.1](https://github.com/electron/electron/releases/tag/v5.0.0-beta.1)|2019-01-23||yes|12.0.0|72|1765|
|[v4.2.11](https://github.com/electron/electron/releases/tag/v4.2.11)|2019-09-24|4-2-x|no|10.11.0|69|2625|
|[v4.2.10](https://github.com/electron/electron/releases/tag/v4.2.10)|2019-08-29||no|10.11.0|69|10016|
|[v4.2.9](https://github.com/electron/electron/releases/tag/v4.2.9)|2019-08-06||no|10.11.0|69|13987|
|[v4.2.8](https://github.com/electron/electron/releases/tag/v4.2.8)|2019-07-20||no|10.11.0|69|7220|
|[v4.2.7](https://github.com/electron/electron/releases/tag/v4.2.7)|2019-07-16||no|10.11.0|69|5721|
|[v4.2.6](https://github.com/electron/electron/releases/tag/v4.2.6)|2019-07-02||no|10.11.0|69|9842|
|[v4.2.5](https://github.com/electron/electron/releases/tag/v4.2.5)|2019-06-21||no|10.11.0|69|10967|
|[v4.2.4](https://github.com/electron/electron/releases/tag/v4.2.4)|2019-06-05||no|10.11.0|69|23711|
|[v4.2.3](https://github.com/electron/electron/releases/tag/v4.2.3)|2019-05-31||no|10.11.0|69|8389|
|[v4.2.2](https://github.com/electron/electron/releases/tag/v4.2.2)|2019-05-17||no|10.11.0|69|11576|
|[v4.2.1](https://github.com/electron/electron/releases/tag/v4.2.1)|2019-05-14||no|10.11.0|69|1833|
|[v4.2.0](https://github.com/electron/electron/releases/tag/v4.2.0)|2019-05-03||no|10.11.0|69|14893|
|[v4.1.5](https://github.com/electron/electron/releases/tag/v4.1.5)|2019-04-24|4-1-x|no|10.11.0|69|11350|
|[v4.1.4](https://github.com/electron/electron/releases/tag/v4.1.4)|2019-04-04||no|10.11.0|69|44556|
|[v4.1.3](https://github.com/electron/electron/releases/tag/v4.1.3)|2019-03-29||no|10.11.0|69|16342|
|[v4.1.2](https://github.com/electron/electron/releases/tag/v4.1.2)|2019-03-28||no|10.11.0|69|2355|
|[v4.1.1](https://github.com/electron/electron/releases/tag/v4.1.1)|2019-03-20||no|10.11.0|69|17930|
|[v4.1.0](https://github.com/electron/electron/releases/tag/v4.1.0)|2019-03-14||no|10.11.0|69|18410|
|[v4.0.8](https://github.com/electron/electron/releases/tag/v4.0.8)|2019-03-08|4-0-x|no|10.11.0|69|14349|
|[v4.0.7](https://github.com/electron/electron/releases/tag/v4.0.7)|2019-03-05||no|10.11.0|69|10482|
|[v4.0.6](https://github.com/electron/electron/releases/tag/v4.0.6)|2019-02-27||no|10.11.0|69|12468|
|[v4.0.5](https://github.com/electron/electron/releases/tag/v4.0.5)|2019-02-15||no|10.11.0|69|24884|
|[v4.0.4](https://github.com/electron/electron/releases/tag/v4.0.4)|2019-02-02||no|10.11.0|69|34555|
|[v4.0.3](https://github.com/electron/electron/releases/tag/v4.0.3)|2019-01-29||no|10.11.0|69|10454|
|[v4.0.2](https://github.com/electron/electron/releases/tag/v4.0.2)|2019-01-22||no|10.11.0|69|14813|
|[v4.0.1](https://github.com/electron/electron/releases/tag/v4.0.1)|2019-01-04||no|10.11.0|69|48413|
|[v4.0.0](https://github.com/electron/electron/releases/tag/v4.0.0)|2018-12-20||no|10.11.0|69|59990|
|[v4.0.0-nightly.20181010](https://github.com/electron/electron/releases/tag/v4.0.0-nightly.20181010)|2018-10-10||yes|10.11.0|69|1349|
|[v4.0.0-nightly.20181006](https://github.com/electron/electron/releases/tag/v4.0.0-nightly.20181006)|2018-10-06||yes|10.11.0|68|117|
|[v4.0.0-nightly.20180929](https://github.com/electron/electron/releases/tag/v4.0.0-nightly.20180929)|2018-09-29||yes|10.6.0|67|86|
|[v4.0.0-nightly.20180821](https://github.com/electron/electron/releases/tag/v4.0.0-nightly.20180821)|2018-08-21||yes|10.2.0|66|77|
|[v4.0.0-nightly.20180819](https://github.com/electron/electron/releases/tag/v4.0.0-nightly.20180819)|2018-08-19||yes|10.2.0|66|19|
|[v4.0.0-nightly.20180817](https://github.com/electron/electron/releases/tag/v4.0.0-nightly.20180817)|2018-08-18||yes|10.2.0|66|11|
|[v4.0.0-beta.11](https://github.com/electron/electron/releases/tag/v4.0.0-beta.11)|2018-12-19|beta-4-0-x|yes|10.11.0|69|760|
|[v4.0.0-beta.10](https://github.com/electron/electron/releases/tag/v4.0.0-beta.10)|2018-12-17||yes|10.11.0|69|1071|
|[v4.0.0-beta.9](https://github.com/electron/electron/releases/tag/v4.0.0-beta.9)|2018-12-11||yes|10.11.0|69|750|
|[v4.0.0-beta.8](https://github.com/electron/electron/releases/tag/v4.0.0-beta.8)|2018-11-30||yes|10.11.0|69|864|
|[v4.0.0-beta.7](https://github.com/electron/electron/releases/tag/v4.0.0-beta.7)|2018-11-06||yes|10.11.0|69|2386|
|[v4.0.0-beta.6](https://github.com/electron/electron/releases/tag/v4.0.0-beta.6)|2018-11-01||yes|10.11.0|69|708|
|[v4.0.0-beta.5](https://github.com/electron/electron/releases/tag/v4.0.0-beta.5)|2018-10-23||yes|10.11.0|69|1158|
|[v4.0.0-beta.4](https://github.com/electron/electron/releases/tag/v4.0.0-beta.4)|2018-10-19||yes|10.11.0|69|813|
|[v4.0.0-beta.3](https://github.com/electron/electron/releases/tag/v4.0.0-beta.3)|2018-10-12||yes|10.11.0|69|700|
|[v4.0.0-beta.2](https://github.com/electron/electron/releases/tag/v4.0.0-beta.2)|2018-10-12||yes|10.11.0|69|505|
|[v4.0.0-beta.1](https://github.com/electron/electron/releases/tag/v4.0.0-beta.1)|2018-10-11||yes|10.11.0|69|1330|
|[v3.1.13](https://github.com/electron/electron/releases/tag/v3.1.13)|2019-07-31|HEAD|no|10.2.0|66|8132|
|[v3.1.12](https://github.com/electron/electron/releases/tag/v3.1.12)|2019-07-11|3-1-x|no|10.2.0|66|2873|
|[v3.1.11](https://github.com/electron/electron/releases/tag/v3.1.11)|2019-06-06||no|10.2.0|66|5665|
|[v3.1.10](https://github.com/electron/electron/releases/tag/v3.1.10)|2019-05-29||no|10.2.0|66|3202|
|[v3.1.9](https://github.com/electron/electron/releases/tag/v3.1.9)|2019-05-01||no|10.2.0|66|6853|
|[v3.1.8](https://github.com/electron/electron/releases/tag/v3.1.8)|2019-03-28||no|10.2.0|66|26671|
|[v3.1.7](https://github.com/electron/electron/releases/tag/v3.1.7)|2019-03-21||no|10.2.0|66|14497|
|[v3.1.6](https://github.com/electron/electron/releases/tag/v3.1.6)|2019-03-08||no|10.2.0|66|26247|
|[v3.1.5](https://github.com/electron/electron/releases/tag/v3.1.5)|2019-03-04||no|10.2.0|66|1635|
|[v3.1.4](https://github.com/electron/electron/releases/tag/v3.1.4)|2019-02-15||no|10.2.0|66|6223|
|[v3.1.3](https://github.com/electron/electron/releases/tag/v3.1.3)|2019-01-31||no|10.2.0|66|21560|
|[v3.1.2](https://github.com/electron/electron/releases/tag/v3.1.2)|2019-01-24||no|10.2.0|66|6519|
|[v3.1.1](https://github.com/electron/electron/releases/tag/v3.1.1)|2019-01-14||no|10.2.0|66|9463|
|[v3.1.0](https://github.com/electron/electron/releases/tag/v3.1.0)|2019-01-07||no|10.2.0|66|5439|
|[v3.1.0-beta.5](https://github.com/electron/electron/releases/tag/v3.1.0-beta.5)|2019-01-04|beta-3-1-x|yes|10.2.0|66|623|
|[v3.1.0-beta.4](https://github.com/electron/electron/releases/tag/v3.1.0-beta.4)|2018-12-17||yes|10.2.0|66|781|
|[v3.1.0-beta.3](https://github.com/electron/electron/releases/tag/v3.1.0-beta.3)|2018-12-14||yes|10.2.0|66|354|
|[v3.1.0-beta.2](https://github.com/electron/electron/releases/tag/v3.1.0-beta.2)|2018-12-04||yes|10.2.0|66|502|
|[v3.1.0-beta.1](https://github.com/electron/electron/releases/tag/v3.1.0-beta.1)|2018-12-02||yes|10.2.0|66|276|
|[v3.0.16](https://github.com/electron/electron/releases/tag/v3.0.16)|2019-03-08|3-0-x|no|10.2.0|66|2927|
|[v3.0.15](https://github.com/electron/electron/releases/tag/v3.0.15)|2019-01-31||no|10.2.0|66|675|
|[v3.0.14](https://github.com/electron/electron/releases/tag/v3.0.14)|2019-01-04||no|10.2.0|66|11632|
|[v3.0.13](https://github.com/electron/electron/releases/tag/v3.0.13)|2018-12-17||no|10.2.0|66|39623|
|[v3.0.12](https://github.com/electron/electron/releases/tag/v3.0.12)|2018-12-14||no|10.2.0|66|6680|
|[v3.0.11](https://github.com/electron/electron/releases/tag/v3.0.11)|2018-12-11||no|10.2.0|66|13467|
|[v3.0.10](https://github.com/electron/electron/releases/tag/v3.0.10)|2018-11-19||no|10.2.0|66|59076|
|[v3.0.9](https://github.com/electron/electron/releases/tag/v3.0.9)|2018-11-13||no|10.2.0|66|12813|
|[v3.0.8](https://github.com/electron/electron/releases/tag/v3.0.8)|2018-11-05||no|10.2.0|66|19835|
|[v3.0.7](https://github.com/electron/electron/releases/tag/v3.0.7)|2018-11-01||no|10.2.0|66|15477|
|[v3.0.6](https://github.com/electron/electron/releases/tag/v3.0.6)|2018-10-24||no|10.2.0|66|15560|
|[v3.0.5](https://github.com/electron/electron/releases/tag/v3.0.5)|2018-10-19||no|10.2.0|66|12198|
|[v3.0.4](https://github.com/electron/electron/releases/tag/v3.0.4)|2018-10-11||no|10.2.0|66|22063|
|[v3.0.3](https://github.com/electron/electron/releases/tag/v3.0.3)|2018-10-07||no|10.2.0|66|15300|
|[v3.0.2](https://github.com/electron/electron/releases/tag/v3.0.2)|2018-09-27||no|10.2.0|66|19568|
|[v3.0.1](https://github.com/electron/electron/releases/tag/v3.0.1)|2018-09-27||no|10.2.0|66|3031|
|[v3.0.0](https://github.com/electron/electron/releases/tag/v3.0.0)|2018-09-18||no|10.2.0|66|172266|
|[v3.0.0-nightly.20180904](https://github.com/electron/electron/releases/tag/v3.0.0-nightly.20180904)|2018-09-05||yes|10.2.0|66|204|
|[v3.0.0-nightly.20180823](https://github.com/electron/electron/releases/tag/v3.0.0-nightly.20180823)|2018-08-24||yes|10.2.0|66|20|
|[v3.0.0-nightly.20180821](https://github.com/electron/electron/releases/tag/v3.0.0-nightly.20180821)|2018-08-21||yes|10.2.0|66|254|
|[v3.0.0-nightly.20180818](https://github.com/electron/electron/releases/tag/v3.0.0-nightly.20180818)|2018-08-18||yes|10.2.0|66|68|
|[v3.0.0-beta.13](https://github.com/electron/electron/releases/tag/v3.0.0-beta.13)|2018-09-17||yes|10.2.0|66|520|
|[v3.0.0-beta.12](https://github.com/electron/electron/releases/tag/v3.0.0-beta.12)|2018-09-12||yes|10.2.0|66|1059|
|[v3.0.0-beta.11](https://github.com/electron/electron/releases/tag/v3.0.0-beta.11)|2018-09-12||yes|10.2.0|66|425|
|[v3.0.0-beta.10](https://github.com/electron/electron/releases/tag/v3.0.0-beta.10)|2018-09-08||yes|10.2.0|66|649|
|[v3.0.0-beta.9](https://github.com/electron/electron/releases/tag/v3.0.0-beta.9)|2018-09-06||yes|10.2.0|66|550|
|[v3.0.0-beta.8](https://github.com/electron/electron/releases/tag/v3.0.0-beta.8)|2018-08-29||yes|10.2.0|66|1383|
|[v3.0.0-beta.7](https://github.com/electron/electron/releases/tag/v3.0.0-beta.7)|2018-08-22||yes|10.2.0|66|786|
|[v3.0.0-beta.6](https://github.com/electron/electron/releases/tag/v3.0.0-beta.6)|2018-08-20||yes|10.2.0|66|1027|
|[v3.0.0-beta.5](https://github.com/electron/electron/releases/tag/v3.0.0-beta.5)|2018-08-13||yes|10.2.0|66|1301|
|[v3.0.0-beta.4](https://github.com/electron/electron/releases/tag/v3.0.0-beta.4)|2018-08-01||yes|10.2.0|66|5109|
|[v3.0.0-beta.3](https://github.com/electron/electron/releases/tag/v3.0.0-beta.3)|2018-07-17||yes|10.2.0|66|1516|
|[v3.0.0-beta.2](https://github.com/electron/electron/releases/tag/v3.0.0-beta.2)|2018-07-10||yes|10.2.0|66|1000|
|[v3.0.0-beta.1](https://github.com/electron/electron/releases/tag/v3.0.0-beta.1)|2018-06-21||yes|10.2.0|66|8684|
|[v2.1.0-unsupported.20180809](https://github.com/electron/electron/releases/tag/v2.1.0-unsupported.20180809)|2018-08-09|unsupported|no|8.9.3|61|1083|
|[v2.0.18](https://github.com/electron/electron/releases/tag/v2.0.18)|2019-03-08|2-0-x|no|8.9.3|61|60818|
|[v2.0.17](https://github.com/electron/electron/releases/tag/v2.0.17)|2019-01-31||no|8.9.3|61|11738|
|[v2.0.16](https://github.com/electron/electron/releases/tag/v2.0.16)|2018-12-18||no|8.9.3|61|27833|
|[v2.0.15](https://github.com/electron/electron/releases/tag/v2.0.15)|2018-12-13||no|8.9.3|61|2504|
|[v2.0.14](https://github.com/electron/electron/releases/tag/v2.0.14)|2018-11-19||no|8.9.3|61|16554|
|[v2.0.13](https://github.com/electron/electron/releases/tag/v2.0.13)|2018-11-01||no|8.9.3|61|18509|
|[v2.0.12](https://github.com/electron/electron/releases/tag/v2.0.12)|2018-10-19||no|8.9.3|61|31479|
|[v2.0.11](https://github.com/electron/electron/releases/tag/v2.0.11)|2018-10-01||no|8.9.3|61|18249|
|[v2.0.10](https://github.com/electron/electron/releases/tag/v2.0.10)|2018-09-19||no|8.9.3|61|13786|
|[v2.0.9](https://github.com/electron/electron/releases/tag/v2.0.9)|2018-09-10||no|8.9.3|61|39248|
|[v2.0.8](https://github.com/electron/electron/releases/tag/v2.0.8)|2018-08-22||no|8.9.3|61|53949|
|[v2.0.8-nightly.20180820](https://github.com/electron/electron/releases/tag/v2.0.8-nightly.20180820)|2018-08-21||yes|8.9.3|61|14|
|[v2.0.8-nightly.20180819](https://github.com/electron/electron/releases/tag/v2.0.8-nightly.20180819)|2018-08-20||yes|8.9.3|61|11|
|[v2.0.7](https://github.com/electron/electron/releases/tag/v2.0.7)|2018-08-08||no|8.9.3|61|39040|
|[v2.0.6](https://github.com/electron/electron/releases/tag/v2.0.6)|2018-08-01||no|8.9.3|61|45085|
|[v2.0.5](https://github.com/electron/electron/releases/tag/v2.0.5)|2018-07-13||no|8.9.3|61|40060|
|[v2.0.4](https://github.com/electron/electron/releases/tag/v2.0.4)|2018-07-03||no|8.9.3|61|30670|
|[v2.0.3](https://github.com/electron/electron/releases/tag/v2.0.3)|2018-06-21||no|8.9.3|61|23144|
|[v2.0.2](https://github.com/electron/electron/releases/tag/v2.0.2)|2018-05-22||no|8.9.3|61|86283|
|[v2.0.1](https://github.com/electron/electron/releases/tag/v2.0.1)|2018-05-16||no|8.9.3|61|28377|
|[v2.0.0](https://github.com/electron/electron/releases/tag/v2.0.0)|2018-05-01||no|8.9.3|61|116967|
|[v2.0.0-beta.8](https://github.com/electron/electron/releases/tag/v2.0.0-beta.8)|2018-04-26||yes|8.9.3|61|2712|
|[v2.0.0-beta.7](https://github.com/electron/electron/releases/tag/v2.0.0-beta.7)|2018-04-03||yes|8.9.3|61|8288|
|[v2.0.0-beta.6](https://github.com/electron/electron/releases/tag/v2.0.0-beta.6)|2018-03-27||yes|8.9.3|61|2477|
|[v2.0.0-beta.5](https://github.com/electron/electron/releases/tag/v2.0.0-beta.5)|2018-03-20||yes|8.9.3|61|2317|
|[v2.0.0-beta.4](https://github.com/electron/electron/releases/tag/v2.0.0-beta.4)|2018-03-15||yes|8.9.3|61|2080|
|[v2.0.0-beta.3](https://github.com/electron/electron/releases/tag/v2.0.0-beta.3)|2018-03-09||yes|8.9.3|61|1911|
|[v2.0.0-beta.2](https://github.com/electron/electron/releases/tag/v2.0.0-beta.2)|2018-03-05||yes|8.9.3|61|5382|
|[v2.0.0-beta.1](https://github.com/electron/electron/releases/tag/v2.0.0-beta.1)|2018-02-21||yes|8.9.3|61|1432|
|[v1.8.8](https://github.com/electron/electron/releases/tag/v1.8.8)|2018-08-22|1-8-x|no|8.2.1|59|362486|
|[v1.8.7](https://github.com/electron/electron/releases/tag/v1.8.7)|2018-05-16||no|8.2.1|59|137822|
|[v1.8.6](https://github.com/electron/electron/releases/tag/v1.8.6)|2018-04-27||no|8.2.1|59|39004|
|[v1.8.5](https://github.com/electron/electron/releases/tag/v1.8.5)|2018-04-26||no|8.2.1|59|2641|
|[v1.8.4](https://github.com/electron/electron/releases/tag/v1.8.4)|2018-03-16||no|8.2.1|59|136542|
|[v1.8.3](https://github.com/electron/electron/releases/tag/v1.8.3)|2018-03-06||no|8.2.1|59|61354|
|[v1.8.2](https://github.com/electron/electron/releases/tag/v1.8.2)|2018-02-07||no|8.2.1|59|85123|
|[v1.8.2-beta.5](https://github.com/electron/electron/releases/tag/v1.8.2-beta.5)|2018-01-31||yes|8.2.1|59|7194|
|[v1.8.2-beta.4](https://github.com/electron/electron/releases/tag/v1.8.2-beta.4)|2018-01-23||yes|8.2.1|59|3758|
|[v1.8.2-beta.3](https://github.com/electron/electron/releases/tag/v1.8.2-beta.3)|2017-12-04||yes|8.2.1|59|6590|
|[v1.8.2-beta.2](https://github.com/electron/electron/releases/tag/v1.8.2-beta.2)|2017-11-06||yes|8.2.1|59|6627|
|[v1.8.2-beta.1](https://github.com/electron/electron/releases/tag/v1.8.2-beta.1)|2017-10-19||yes|8.2.1|59|3187|
|[v1.8.1](https://github.com/electron/electron/releases/tag/v1.8.1)|2017-09-29||yes|8.2.1|59|67582|
|[v1.8.0](https://github.com/electron/electron/releases/tag/v1.8.0)|2017-12-12||yes|8.2.1|59|172298|
|[v1.7.16](https://github.com/electron/electron/releases/tag/v1.7.16)|2018-08-22|1-7-x|no|7.9.0|58|23493|
|[v1.7.15](https://github.com/electron/electron/releases/tag/v1.7.15)|2018-05-16||no|7.9.0|58|7620|
|[v1.7.14](https://github.com/electron/electron/releases/tag/v1.7.14)|2018-04-27||no|7.9.0|58|2311|
|[v1.7.13](https://github.com/electron/electron/releases/tag/v1.7.13)|2018-03-15||no|7.9.0|58|5692|
|[v1.7.12](https://github.com/electron/electron/releases/tag/v1.7.12)|2018-01-31||no|7.9.0|58|45812|
|[v1.7.11](https://github.com/electron/electron/releases/tag/v1.7.11)|2018-01-23||no|7.9.0|58|53406|
|[v1.7.10](https://github.com/electron/electron/releases/tag/v1.7.10)|2017-12-18||no|7.9.0|58|244948|
|[v1.7.9](https://github.com/electron/electron/releases/tag/v1.7.9)|2017-10-11||no|7.9.0|58|204000|
|[v1.7.8](https://github.com/electron/electron/releases/tag/v1.7.8)|2017-09-24||no|7.9.0|58|55521|
|[v1.7.7](https://github.com/electron/electron/releases/tag/v1.7.7)|2017-09-05||yes|7.9.0|58|38171|
|[v1.7.6](https://github.com/electron/electron/releases/tag/v1.7.6)|2017-08-09||no|7.9.0|58|51303|
|[v1.7.5](https://github.com/electron/electron/releases/tag/v1.7.5)|2017-07-17||no|7.9.0|58|69458|
|[v1.7.4](https://github.com/electron/electron/releases/tag/v1.7.4)|2017-06-28||yes|7.9.0|58|16195|
|[v1.7.3](https://github.com/electron/electron/releases/tag/v1.7.3)|2017-06-08||yes|7.9.0|58|22177|
|[v1.7.2](https://github.com/electron/electron/releases/tag/v1.7.2)|2017-05-26||yes|7.9.0|58|12076|
|[v1.7.1](https://github.com/electron/electron/releases/tag/v1.7.1)|2017-05-16||yes|7.9.0|58|14873|
|[v1.7.0](https://github.com/electron/electron/releases/tag/v1.7.0)|2017-05-10||yes|7.9.0|58|116424|
|[v1.6.18](https://github.com/electron/electron/releases/tag/v1.6.18)|2018-05-15||no|7.4.0|56|5639|
|[v1.6.17](https://github.com/electron/electron/releases/tag/v1.6.17)|2018-01-31||no|7.4.0|56|5499|
|[v1.6.16](https://github.com/electron/electron/releases/tag/v1.6.16)|2018-01-23||no|7.4.0|56|6112|
|[v1.6.15](https://github.com/electron/electron/releases/tag/v1.6.15)|2017-10-11||no|7.4.0|56|12548|
|[v1.6.14](https://github.com/electron/electron/releases/tag/v1.6.14)|2017-09-28||no|7.4.0|56|5268|
|[v1.6.13](https://github.com/electron/electron/releases/tag/v1.6.13)|2017-09-06||yes|7.4.0|56|9660|
|[v1.6.12](https://github.com/electron/electron/releases/tag/v1.6.12)|2017-09-06||yes|7.4.0|56|10080|
|[v1.6.11](https://github.com/electron/electron/releases/tag/v1.6.11)|2017-05-25||no|7.4.0|56|116214|
|[v1.6.10](https://github.com/electron/electron/releases/tag/v1.6.10)|2017-05-16||no|7.4.0|56|35881|
|[v1.6.9](https://github.com/electron/electron/releases/tag/v1.6.9)|2017-05-10||no|7.4.0|56|3254|
|[v1.6.8](https://github.com/electron/electron/releases/tag/v1.6.8)|2017-05-01||no|7.4.0|56|27256|
|[v1.6.7](https://github.com/electron/electron/releases/tag/v1.6.7)|2017-04-18||no|7.4.0|56|20586|
|[v1.6.6](https://github.com/electron/electron/releases/tag/v1.6.6)|2017-04-07||no|7.4.0|56|69366|
|[v1.6.5](https://github.com/electron/electron/releases/tag/v1.6.5)|2017-03-31||no|7.4.0|56|18437|
|[v1.6.4](https://github.com/electron/electron/releases/tag/v1.6.4)|2017-03-22||yes|7.4.0|56|8490|
|[v1.6.3](https://github.com/electron/electron/releases/tag/v1.6.3)|2017-03-07||yes|7.4.0|56|6288|
|[v1.6.2](https://github.com/electron/electron/releases/tag/v1.6.2)|2017-03-01||no|7.4.0|56|74391|
|[v1.6.1](https://github.com/electron/electron/releases/tag/v1.6.1)|2017-02-21||no|7.4.0|56|22947|
|[v1.6.0](https://github.com/electron/electron/releases/tag/v1.6.0)|2017-02-07||yes|7.4.0|56|69094|
|[v1.5.1](https://github.com/electron/electron/releases/tag/v1.5.1)|2017-02-06||yes|7.4.0|54|3763|
|[v1.5.0](https://github.com/electron/electron/releases/tag/v1.5.0)|2017-01-24||yes|7.4.0|54|11225|
|[v1.4.16](https://github.com/electron/electron/releases/tag/v1.4.16)|2017-04-05||no|6.5.0|53|46192|
|[v1.4.15](https://github.com/electron/electron/releases/tag/v1.4.15)|2017-01-19||no|6.5.0|53|84370|
|[v1.4.14](https://github.com/electron/electron/releases/tag/v1.4.14)|2017-01-10||no|6.5.0|53|76829|
|[v1.4.13](https://github.com/electron/electron/releases/tag/v1.4.13)|2016-12-20||no|6.5.0|53|124666|
|[v1.4.12](https://github.com/electron/electron/releases/tag/v1.4.12)|2016-12-10||no|6.5.0|54|22528|
|[v1.4.11](https://github.com/electron/electron/releases/tag/v1.4.11)|2016-12-07||no|6.5.0|53|7393|
|[v1.4.10](https://github.com/electron/electron/releases/tag/v1.4.10)|2016-11-28||no|6.5.0|53|17564|
|[v1.4.8](https://github.com/electron/electron/releases/tag/v1.4.8)|2016-11-22||no|6.5.0|53|9618|
|[v1.4.7](https://github.com/electron/electron/releases/tag/v1.4.7)|2016-11-16||no|6.5.0|53|10306|
|[v1.4.6](https://github.com/electron/electron/releases/tag/v1.4.6)|2016-11-09||no|6.5.0|53|31180|
|[v1.4.5](https://github.com/electron/electron/releases/tag/v1.4.5)|2016-11-01||no|6.5.0|53|13428|
|[v1.4.4](https://github.com/electron/electron/releases/tag/v1.4.4)|2016-10-20||no|6.5.0|53|19312|
|[v1.4.3](https://github.com/electron/electron/releases/tag/v1.4.3)|2016-10-06||no|6.5.0|53|38434|
|[v1.4.2](https://github.com/electron/electron/releases/tag/v1.4.2)|2016-09-30||no|6.5.0|53|9577|
|[v1.4.1](https://github.com/electron/electron/releases/tag/v1.4.1)|2016-09-22||no|6.5.0|53|14059|
|[v1.4.0](https://github.com/electron/electron/releases/tag/v1.4.0)|2016-09-15||no|6.5.0|53|68574|
|[v1.3.15](https://github.com/electron/electron/releases/tag/v1.3.15)|2017-04-21||no|6.5.0|52|2958|
|[v1.3.14](https://github.com/electron/electron/releases/tag/v1.3.14)|2017-03-14||no|6.5.0|52|3463|
|[v1.3.13](https://github.com/electron/electron/releases/tag/v1.3.13)|2016-12-06||no|6.5.0|52|4885|
|[v1.3.12](https://github.com/electron/electron/releases/tag/v1.3.12)|2016-11-28||no|||385|
|[v1.3.10](https://github.com/electron/electron/releases/tag/v1.3.10)|2016-11-22||no|6.5.0|52|371|
|[v1.3.9](https://github.com/electron/electron/releases/tag/v1.3.9)|2016-11-16||no|6.5.0|52|6983|
|[v1.3.8](https://github.com/electron/electron/releases/tag/v1.3.8)|2016-10-20||no|||7167|
|[v1.3.7](https://github.com/electron/electron/releases/tag/v1.3.7)|2016-09-27||no|6.5.0|52|2874|
|[v1.3.6](https://github.com/electron/electron/releases/tag/v1.3.6)|2016-09-15||no|6.3.0|52|3110|
|[v1.3.5](https://github.com/electron/electron/releases/tag/v1.3.5)|2016-09-02||no|6.3.0|52|18954|
|[v1.3.4](https://github.com/electron/electron/releases/tag/v1.3.4)|2016-08-23||no|6.3.0|52|19739|
|[v1.3.3](https://github.com/electron/electron/releases/tag/v1.3.3)|2016-08-10||no|6.3.0|52|25292|
|[v1.3.2](https://github.com/electron/electron/releases/tag/v1.3.2)|2016-08-02||no|6.3.0|52|16907|
|[v1.3.1](https://github.com/electron/electron/releases/tag/v1.3.1)|2016-07-27||no|6.3.0|52|23157|
|[v1.3.0](https://github.com/electron/electron/releases/tag/v1.3.0)|2016-07-25||no|6.3.0|52|32766|
|[v1.2.8](https://github.com/electron/electron/releases/tag/v1.2.8)|2016-07-21||no|6.1.0|51|15628|
|[v1.2.7](https://github.com/electron/electron/releases/tag/v1.2.7)|2016-07-13||no|6.1.0|51|15270|
|[v1.2.6](https://github.com/electron/electron/releases/tag/v1.2.6)|2016-07-06||no|6.1.0|51|14340|
|[v1.2.5](https://github.com/electron/electron/releases/tag/v1.2.5)|2016-06-23||no|6.1.0|51|18057|
|[v1.2.4](https://github.com/electron/electron/releases/tag/v1.2.4)|2016-06-22||no|6.1.0|51|5748|
|[v1.2.3](https://github.com/electron/electron/releases/tag/v1.2.3)|2016-06-16||no|6.1.0|51|10931|
|[v1.2.2](https://github.com/electron/electron/releases/tag/v1.2.2)|2016-06-08||no|6.1.0|51|14500|
|[v1.2.1](https://github.com/electron/electron/releases/tag/v1.2.1)|2016-06-01||no|6.1.0|51|12568|
|[v1.2.0](https://github.com/electron/electron/releases/tag/v1.2.0)|2016-05-26||no|6.1.0|51|24705|
|[v1.1.3](https://github.com/electron/electron/releases/tag/v1.1.3)|2016-05-25||no|6.1.0|50|20518|
|[v1.1.2](https://github.com/electron/electron/releases/tag/v1.1.2)|2016-05-24||no|6.1.0|50|6372|
|[v1.1.1](https://github.com/electron/electron/releases/tag/v1.1.1)|2016-05-20||no|6.1.0|50|19686|
|[v1.1.0](https://github.com/electron/electron/releases/tag/v1.1.0)|2016-05-14||no|6.1.0|50|19665|
|[v1.0.2](https://github.com/electron/electron/releases/tag/v1.0.2)|2016-05-13||no|5.10.0|49|10208|
|[v1.0.1](https://github.com/electron/electron/releases/tag/v1.0.1)|2016-05-11||no|5.10.0|49|9142|
|[v1.0.0](https://github.com/electron/electron/releases/tag/v1.0.0)|2016-05-11||no|5.10.0|49|50018|
|[v0.37.8](https://github.com/electron/electron/releases/tag/v0.37.8)|2016-04-29||no|5.10.0|49|44988|
|[v0.37.7](https://github.com/electron/electron/releases/tag/v0.37.7)|2016-04-22||no|5.10.0|49|10985|
|[v0.37.6](https://github.com/electron/electron/releases/tag/v0.37.6)|2016-04-15||no|5.10.0|49|23875|
|[v0.37.5](https://github.com/electron/electron/releases/tag/v0.37.5)|2016-04-07||no|5.10.0|49|13632|
|[v0.37.4](https://github.com/electron/electron/releases/tag/v0.37.4)|2016-04-03||no|6.0.0-pre|49|8659|
|[v0.37.3](https://github.com/electron/electron/releases/tag/v0.37.3)|2016-03-27||no|5.1.1|49|41320|
|[v0.37.2](https://github.com/electron/electron/releases/tag/v0.37.2)|2016-03-14||no|||16433|
|[v0.37.1](https://github.com/electron/electron/releases/tag/v0.37.1)|2016-03-13||no|5.1.1|49|4616|
|[v0.37.0](https://github.com/electron/electron/releases/tag/v0.37.0)|2016-03-12||no|5.1.1|49|27617|
|[v0.36.12](https://github.com/electron/electron/releases/tag/v0.36.12)|2016-03-27||no|5.1.1|47|40091|
|[v0.36.11](https://github.com/electron/electron/releases/tag/v0.36.11)|2016-03-11||no|5.1.1|47|11973|
|[v0.36.10](https://github.com/electron/electron/releases/tag/v0.36.10)|2016-03-05||no|5.1.1|47|11110|
|[v0.36.9](https://github.com/electron/electron/releases/tag/v0.36.9)|2016-02-26||no|5.1.1|47|13847|
|[v0.36.8](https://github.com/electron/electron/releases/tag/v0.36.8)|2016-02-19||no|5.1.1|47|12440|
|[v0.36.7](https://github.com/electron/electron/releases/tag/v0.36.7)|2016-01-30||no|5.1.1|47|24388|
|[v0.36.6](https://github.com/electron/electron/releases/tag/v0.36.6)|2016-01-29||no|5.1.1|47|4143|
|[v0.36.5](https://github.com/electron/electron/releases/tag/v0.36.5)|2016-01-22||no|5.1.1|47|11084|
|[v0.36.4](https://github.com/electron/electron/releases/tag/v0.36.4)|2016-01-15||no|5.1.1|47|26869|
|[v0.36.3](https://github.com/electron/electron/releases/tag/v0.36.3)|2016-01-11||no|5.1.1|47|7333|
|[v0.36.2](https://github.com/electron/electron/releases/tag/v0.36.2)|2015-12-25||no|5.1.1|47|16415|
|[v0.36.1](https://github.com/electron/electron/releases/tag/v0.36.1)|2015-12-18||no|||9154|
|[v0.36.0](https://github.com/electron/electron/releases/tag/v0.36.0)|2015-12-11||no|5.1.1|47|19747|
|[v0.35.6](https://github.com/electron/electron/releases/tag/v0.35.6)|2016-01-11||no|||22179|
|[v0.35.5](https://github.com/electron/electron/releases/tag/v0.35.5)|2015-12-31||no|4.1.1|45|3725|
|[v0.35.4](https://github.com/electron/electron/releases/tag/v0.35.4)|2015-12-04||no|4.1.1|45|12945|
|[v0.35.3](https://github.com/electron/electron/releases/tag/v0.35.3)|2015-12-04||no|4.1.1|45|13711|
|[v0.35.2](https://github.com/electron/electron/releases/tag/v0.35.2)|2015-11-27||no|4.1.1|45|8443|
|[v0.35.1](https://github.com/electron/electron/releases/tag/v0.35.1)|2015-11-20||no|4.1.1|45|11305|
|[v0.35.0](https://github.com/electron/electron/releases/tag/v0.35.0)|2015-11-16||no|||8293|
|[v0.34.5](https://github.com/electron/electron/releases/tag/v0.34.5)|2015-11-26||no|||10503|
|[v0.34.4](https://github.com/electron/electron/releases/tag/v0.34.4)|2015-11-24||no|4.1.1|45|2764|
|[v0.34.3](https://github.com/electron/electron/releases/tag/v0.34.3)|2015-11-06||no|4.1.1|45|13400|
|[v0.34.2](https://github.com/electron/electron/releases/tag/v0.34.2)|2015-10-30||no|4.1.1|45|9769|
|[v0.34.1](https://github.com/electron/electron/releases/tag/v0.34.1)|2015-10-23||no|4.1.1|45|11486|
|[v0.34.0](https://github.com/electron/electron/releases/tag/v0.34.0)|2015-10-16||no|4.1.1|45|26745|
|[v0.33.9](https://github.com/electron/electron/releases/tag/v0.33.9)|2015-10-16||no|4.1.1|45|9233|
|[v0.33.8](https://github.com/electron/electron/releases/tag/v0.33.8)|2015-10-14||no|4.1.1|45|3837|
|[v0.33.7](https://github.com/electron/electron/releases/tag/v0.33.7)|2015-10-10||no|4.1.1|45|6426|
|[v0.33.6](https://github.com/electron/electron/releases/tag/v0.33.6)|2015-10-05||no|4.1.1|45|6128|
|[v0.33.5](https://github.com/electron/electron/releases/tag/v0.33.5)|2015-10-05||no|||2476|
|[v0.33.4](https://github.com/electron/electron/releases/tag/v0.33.4)|2015-10-02||no|4.1.1|45|3731|
|[v0.33.3](https://github.com/electron/electron/releases/tag/v0.33.3)|2015-09-26||no|4.1.1|45|6827|
|[v0.33.2](https://github.com/electron/electron/releases/tag/v0.33.2)|2015-09-25||no|4.1.1|45|2550|
|[v0.33.1](https://github.com/electron/electron/releases/tag/v0.33.1)|2015-09-22||no|4.1.1|45|3996|
|[v0.33.0](https://github.com/electron/electron/releases/tag/v0.33.0)|2015-09-17||no|5.0.0-pre|45|7311|
|[v0.32.3](https://github.com/electron/electron/releases/tag/v0.32.3)|2015-09-15||no|5.0.0-pre|45|4707|
|[v0.32.2](https://github.com/electron/electron/releases/tag/v0.32.2)|2015-09-10||no|3.3.0|45|3393|
|[v0.32.1](https://github.com/electron/electron/releases/tag/v0.32.1)|2015-09-09||no|||3972|
|[v0.32.0](https://github.com/electron/electron/releases/tag/v0.32.0)|2015-09-09||no|||420|
|[v0.31.2](https://github.com/electron/electron/releases/tag/v0.31.2)|2015-09-02||no|3.3.0|45|9527|
|[v0.31.1](https://github.com/electron/electron/releases/tag/v0.31.1)|2015-08-28||no|||2593|
|[v0.31.0](https://github.com/electron/electron/releases/tag/v0.31.0)|2015-08-26||no|3.1.0|44|2318|
|[v0.30.8](https://github.com/electron/electron/releases/tag/v0.30.8)|2015-09-26||no|||12101|
|[v0.30.7](https://github.com/electron/electron/releases/tag/v0.30.7)|2015-09-24||no|||3162|
|[v0.30.6](https://github.com/electron/electron/releases/tag/v0.30.6)|2015-08-26||no|||3300|
|[v0.30.5](https://github.com/electron/electron/releases/tag/v0.30.5)|2015-08-21||no|||1351|
|[v0.30.4](https://github.com/electron/electron/releases/tag/v0.30.4)|2015-08-10||no|3.1.0|44|5166|
|[v0.30.3](https://github.com/electron/electron/releases/tag/v0.30.3)|2015-08-07||no|||2372|
|[v0.30.2](https://github.com/electron/electron/releases/tag/v0.30.2)|2015-07-30||no|||6436|
|[v0.30.1](https://github.com/electron/electron/releases/tag/v0.30.1)|2015-07-24||no|||2914|
|[v0.30.0](https://github.com/electron/electron/releases/tag/v0.30.0)|2015-07-16||no|||8928|
|[v0.29.2](https://github.com/electron/electron/releases/tag/v0.29.2)|2015-07-07||no|2.3.1|43|17517|
|[v0.29.1](https://github.com/electron/electron/releases/tag/v0.29.1)|2015-07-03||no|2.3.1|43|1522|
|[v0.29.0](https://github.com/electron/electron/releases/tag/v0.29.0)|2015-07-03||no|||558|
|[v0.28.3](https://github.com/electron/electron/releases/tag/v0.28.3)|2015-06-23||no|2.2.1|43|7585|
|[v0.28.2](https://github.com/electron/electron/releases/tag/v0.28.2)|2015-06-18||no|2.2.1|43|2687|
|[v0.28.1](https://github.com/electron/electron/releases/tag/v0.28.1)|2015-06-12||no|2.2.1|43|2704|
|[v0.28.0](https://github.com/electron/electron/releases/tag/v0.28.0)|2015-06-11||no|2.2.1|43|349|
|[v0.27.3](https://github.com/electron/electron/releases/tag/v0.27.3)|2015-06-08||no|1.6.3|43|3222|
|[v0.27.2](https://github.com/electron/electron/releases/tag/v0.27.2)|2015-06-01||no|1.6.3|43|3160|
|[v0.27.1](https://github.com/electron/electron/releases/tag/v0.27.1)|2015-05-28||no|1.6.3|42|1163|
|[v0.27.0](https://github.com/electron/electron/releases/tag/v0.27.0)|2015-05-27||no|1.6.3|42|344|
|[v0.26.1](https://github.com/electron/electron/releases/tag/v0.26.1)|2015-05-21||no|1.6.3|42|5557|
|[v0.26.0](https://github.com/electron/electron/releases/tag/v0.26.0)|2015-05-12||no|1.6.3|42|3821|
|[v0.25.3](https://github.com/electron/electron/releases/tag/v0.25.3)|2015-05-08||no|1.6.3|42|4334|
|[v0.25.2](https://github.com/electron/electron/releases/tag/v0.25.2)|2015-05-01||no|1.6.3|42|3170|
|[v0.25.1](https://github.com/electron/electron/releases/tag/v0.25.1)|2015-04-23||no|1.6.3|42|5447|
|[v0.25.0](https://github.com/electron/electron/releases/tag/v0.25.0)|2015-04-22||no|1.6.3|42|400|
|[v0.24.0](https://github.com/electron/electron/releases/tag/v0.24.0)|2015-04-17||no|1.6.3|41|3861|
|[v0.23.0](https://github.com/electron/electron/releases/tag/v0.23.0)|2015-04-12||no|1.6.3|41|1097|
|[v0.22.3](https://github.com/electron/electron/releases/tag/v0.22.3)|2015-03-30||no|1.6.3|41|7435|
|[v0.22.2](https://github.com/electron/electron/releases/tag/v0.22.2)|2015-03-23||no|1.5.1|41|571|
|[v0.22.1](https://github.com/electron/electron/releases/tag/v0.22.1)|2015-03-18||no|1.5.1|41|1986|
|[v0.22.0](https://github.com/electron/electron/releases/tag/v0.22.0)|2015-03-18||no|||4944|
|[v0.21.3](https://github.com/electron/electron/releases/tag/v0.21.3)|2015-03-03||no|1.5.1|41|1792|
|[v0.21.2](https://github.com/electron/electron/releases/tag/v0.21.2)|2015-02-05||no|1.0.0-pre|40|2038|
|[v0.21.1](https://github.com/electron/electron/releases/tag/v0.21.1)|2015-02-03||no|1.0.0-pre|40|592|
|[v0.21.0](https://github.com/electron/electron/releases/tag/v0.21.0)|2015-01-28||no|1.0.0-pre|40|1196|
|[v0.20.8](https://github.com/electron/electron/releases/tag/v0.20.8)|2015-01-27||no|0.13.0-pre|39|64|
|[v0.20.7](https://github.com/electron/electron/releases/tag/v0.20.7)|2015-01-20||no|0.13.0-pre|39|393|
|[v0.20.6](https://github.com/electron/electron/releases/tag/v0.20.6)|2015-01-19||no|0.13.0-pre|39|549|
|[v0.20.5](https://github.com/electron/electron/releases/tag/v0.20.5)|2015-01-08||no|0.13.0-pre|39|582|
|[v0.20.4](https://github.com/electron/electron/releases/tag/v0.20.4)|2015-01-06||no|0.13.0-pre|39|367|
|[v0.20.3](https://github.com/electron/electron/releases/tag/v0.20.3)|2014-12-29||no|0.13.0-pre|39|549|
|[v0.20.2](https://github.com/electron/electron/releases/tag/v0.20.2)|2014-12-22||no|0.13.0-pre|39|842|
|[v0.20.1](https://github.com/electron/electron/releases/tag/v0.20.1)|2014-12-18||no|0.13.0-pre|39|364|
|[v0.20.0](https://github.com/electron/electron/releases/tag/v0.20.0)|2014-12-13||no|0.13.0-pre|39|275|
|[v0.19.5](https://github.com/electron/electron/releases/tag/v0.19.5)|2014-11-28||no|||3197|
|[v0.19.4](https://github.com/electron/electron/releases/tag/v0.19.4)|2014-11-21||no|||823|
|[v0.19.3](https://github.com/electron/electron/releases/tag/v0.19.3)|2014-11-20||no|||104|
|[v0.19.2](https://github.com/electron/electron/releases/tag/v0.19.2)|2014-11-15||no|||402|
|[v0.19.1](https://github.com/electron/electron/releases/tag/v0.19.1)|2014-11-04||no|||898|
|[v0.19.0](https://github.com/electron/electron/releases/tag/v0.19.0)|2014-10-30||no|||397|
|[v0.18.2](https://github.com/electron/electron/releases/tag/v0.18.2)|2014-10-21||no|||598|
|[v0.18.1](https://github.com/electron/electron/releases/tag/v0.18.1)|2014-10-17||no|||299|
|[v0.18.0](https://github.com/electron/electron/releases/tag/v0.18.0)|2014-10-14||no|||526|
|[v0.17.2](https://github.com/electron/electron/releases/tag/v0.17.2)|2014-10-06||no|||588|
|[v0.17.1](https://github.com/electron/electron/releases/tag/v0.17.1)|2014-10-01||no|||296|
|[v0.17.0](https://github.com/electron/electron/releases/tag/v0.17.0)|2014-10-01||no|||60|
|[v0.16.3](https://github.com/electron/electron/releases/tag/v0.16.3)|2014-09-20||no|||421|
|[v0.16.2](https://github.com/electron/electron/releases/tag/v0.16.2)|2014-09-09||no|||967|
|[v0.16.1](https://github.com/electron/electron/releases/tag/v0.16.1)|2014-09-08||no|||99|
|[v0.16.0](https://github.com/electron/electron/releases/tag/v0.16.0)|2014-09-06||no|||103|
|[v0.15.9](https://github.com/electron/electron/releases/tag/v0.15.9)|2014-08-20||no|||1534|
|[v0.15.8](https://github.com/electron/electron/releases/tag/v0.15.8)|2014-08-18||no|||1919|
|[v0.15.7](https://github.com/electron/electron/releases/tag/v0.15.7)|2014-08-15||no|||1920|
|[v0.15.6](https://github.com/electron/electron/releases/tag/v0.15.6)|2014-08-13||no|||1931|
|[v0.15.5](https://github.com/electron/electron/releases/tag/v0.15.5)|2014-08-11||no|||1948|
|[v0.15.4](https://github.com/electron/electron/releases/tag/v0.15.4)|2014-08-07||no|||2157|
|[v0.15.3](https://github.com/electron/electron/releases/tag/v0.15.3)|2014-08-06||no|||3844|
|[v0.15.2](https://github.com/electron/electron/releases/tag/v0.15.2)|2014-08-04||no|||1914|
|[v0.15.1](https://github.com/electron/electron/releases/tag/v0.15.1)|2014-07-31||no|||2032|
|[v0.15.0](https://github.com/electron/electron/releases/tag/v0.15.0)|2014-07-29||no|||1968|
|[v0.14.3](https://github.com/electron/electron/releases/tag/v0.14.3)|2014-07-27||no|||1872|
|[v0.14.2](https://github.com/electron/electron/releases/tag/v0.14.2)|2014-07-25||no|||1855|
|[v0.14.1](https://github.com/electron/electron/releases/tag/v0.14.1)|2014-07-24||no|||1848|
|[v0.14.0](https://github.com/electron/electron/releases/tag/v0.14.0)|2014-07-22||no|||1922|
|[v0.13.3](https://github.com/electron/electron/releases/tag/v0.13.3)|2014-06-25||no|||2232|
|[v0.13.2](https://github.com/electron/electron/releases/tag/v0.13.2)|2014-06-18||no|||356|
|[v0.13.1](https://github.com/electron/electron/releases/tag/v0.13.1)|2014-06-14||no|||367|
|[v0.13.0](https://github.com/electron/electron/releases/tag/v0.13.0)|2014-06-05||no|||719|
|[v0.12.7](https://github.com/electron/electron/releases/tag/v0.12.7)|2014-05-27||no|||402|
|[v0.12.6](https://github.com/electron/electron/releases/tag/v0.12.6)|2014-05-26||no|||226|
|[v0.12.5](https://github.com/electron/electron/releases/tag/v0.12.5)|2014-05-19||no|||16905|
|[v0.12.4](https://github.com/electron/electron/releases/tag/v0.12.4)|2014-05-12||no|||588|
|[v0.12.3](https://github.com/electron/electron/releases/tag/v0.12.3)|2014-05-07||no|||918|
|[v0.12.2](https://github.com/electron/electron/releases/tag/v0.12.2)|2014-05-05||no|||880|
|[v0.12.1](https://github.com/electron/electron/releases/tag/v0.12.1)|2014-05-05||no|||80|
|[v0.12.0](https://github.com/electron/electron/releases/tag/v0.12.0)|2014-04-29||no|||77|
|[v0.11.10](https://github.com/electron/electron/releases/tag/v0.11.10)|2014-04-14||no|||86|
|[v0.11.9](https://github.com/electron/electron/releases/tag/v0.11.9)|2014-04-11||no|||74|
|[v0.11.8](https://github.com/electron/electron/releases/tag/v0.11.8)|2014-04-10||no|||70|
|[v0.11.7](https://github.com/electron/electron/releases/tag/v0.11.7)|2014-04-08||no|||73|
|[v0.11.6](https://github.com/electron/electron/releases/tag/v0.11.6)|2014-04-07||no|||76|
|[v0.11.5](https://github.com/electron/electron/releases/tag/v0.11.5)|2014-04-02||no|||77|
|[v0.11.4](https://github.com/electron/electron/releases/tag/v0.11.4)|2014-03-28||no|||76|
|[v0.11.3](https://github.com/electron/electron/releases/tag/v0.11.3)|2014-03-25||no|||71|
|[v0.11.2](https://github.com/electron/electron/releases/tag/v0.11.2)|2014-03-24||no|||73|
|[v0.11.1](https://github.com/electron/electron/releases/tag/v0.11.1)|2014-03-18||no|||71|
|[v0.11.0](https://github.com/electron/electron/releases/tag/v0.11.0)|2014-03-16||no|||65|
|[v0.10.7](https://github.com/electron/electron/releases/tag/v0.10.7)|2014-03-11||no|||107|
|[v0.10.6](https://github.com/electron/electron/releases/tag/v0.10.6)|2014-03-07||no|||75|
|[v0.10.5](https://github.com/electron/electron/releases/tag/v0.10.5)|2014-03-05||no|||79|
|[v0.10.4](https://github.com/electron/electron/releases/tag/v0.10.4)|2014-03-02||no|||72|
|[v0.10.3](https://github.com/electron/electron/releases/tag/v0.10.3)|2014-02-28||no|||99|
|[v0.10.2](https://github.com/electron/electron/releases/tag/v0.10.2)|2014-02-27||no|||71|
|[v0.10.1](https://github.com/electron/electron/releases/tag/v0.10.1)|2014-02-25||no|||90|
|[v0.10.0](https://github.com/electron/electron/releases/tag/v0.10.0)|2014-02-24||no|||0|
|[v0.9.3](https://github.com/electron/electron/releases/tag/v0.9.3)|2014-02-17||no|||1844|
|[v0.9.2](https://github.com/electron/electron/releases/tag/v0.9.2)|2014-02-12||no|||1866|
|[v0.9.1](https://github.com/electron/electron/releases/tag/v0.9.1)|2014-02-04||no|||1853|
|[v0.9.0](https://github.com/electron/electron/releases/tag/v0.9.0)|2014-02-02||no|||1843|
|[v0.8.7](https://github.com/electron/electron/releases/tag/v0.8.7)|2014-01-27||no|||1864|
|[v0.8.6](https://github.com/electron/electron/releases/tag/v0.8.6)|2014-01-23||no|||1853|
|[v0.8.5](https://github.com/electron/electron/releases/tag/v0.8.5)|2014-01-14||no|||1870|
|[v0.8.4](https://github.com/electron/electron/releases/tag/v0.8.4)|2014-01-13||no|||1852|
|[v0.8.3](https://github.com/electron/electron/releases/tag/v0.8.3)|2014-01-08||no|||1853|
|[v0.8.2](https://github.com/electron/electron/releases/tag/v0.8.2)|2014-01-07||no|||1902|
|[v0.8.1](https://github.com/electron/electron/releases/tag/v0.8.1)|2013-12-29||no|||1864|
|[v0.8.0](https://github.com/electron/electron/releases/tag/v0.8.0)|2013-12-27||no|||1847|
|[v0.7.6](https://github.com/electron/electron/releases/tag/v0.7.6)|2013-12-09||no|||1916|
|[v0.7.5](https://github.com/electron/electron/releases/tag/v0.7.5)|2013-12-05||no|||1851|
|[v0.7.4](https://github.com/electron/electron/releases/tag/v0.7.4)|2013-12-04||no|||1936|
|[v0.7.3](https://github.com/electron/electron/releases/tag/v0.7.3)|2013-11-29||no|||1905|
|[v0.7.2](https://github.com/electron/electron/releases/tag/v0.7.2)|2013-11-28||no|||1882|
|[v0.7.1](https://github.com/electron/electron/releases/tag/v0.7.1)|2013-11-28||no|||1863|
|[v0.7.0](https://github.com/electron/electron/releases/tag/v0.7.0)|2013-11-27||no|||1861|
|[v0.6.12](https://github.com/electron/electron/releases/tag/v0.6.12)|2013-11-22||no|||931|
|[v0.6.11](https://github.com/electron/electron/releases/tag/v0.6.11)|2013-11-20||no|||933|
|[v0.6.10](https://github.com/electron/electron/releases/tag/v0.6.10)|2013-11-11||no|||938|
|[v0.6.9](https://github.com/electron/electron/releases/tag/v0.6.9)|2013-11-07||no|||938|
|[v0.6.8](https://github.com/electron/electron/releases/tag/v0.6.8)|2013-11-05||no|||923|
|[v0.6.7](https://github.com/electron/electron/releases/tag/v0.6.7)|2013-11-02||no|||929|
|[v0.6.6](https://github.com/electron/electron/releases/tag/v0.6.6)|2013-10-28||no|||938|
|[v0.6.5](https://github.com/electron/electron/releases/tag/v0.6.5)|2013-10-26||no|||902|
|[v0.6.4](https://github.com/electron/electron/releases/tag/v0.6.4)|2013-10-22||no|||921|
|[v0.6.3](https://github.com/electron/electron/releases/tag/v0.6.3)|2013-10-21||no|||905|
|[v0.6.2](https://github.com/electron/electron/releases/tag/v0.6.2)|2013-10-17||no|||907|
|[v0.6.1](https://github.com/electron/electron/releases/tag/v0.6.1)|2013-10-14||no|||908|
|[v0.6.0](https://github.com/electron/electron/releases/tag/v0.6.0)|2013-10-10||no|||909|
|[v0.5.4](https://github.com/electron/electron/releases/tag/v0.5.4)|2013-10-04||no|||932|
|[v0.5.3](https://github.com/electron/electron/releases/tag/v0.5.3)|2013-09-29||no|||895|
|[v0.5.2](https://github.com/electron/electron/releases/tag/v0.5.2)|2013-09-29||no|||895|
|[v0.5.1](https://github.com/electron/electron/releases/tag/v0.5.1)|2013-09-26||no|||916|
|[v0.5.0](https://github.com/electron/electron/releases/tag/v0.5.0)|2013-09-25||no|||903|
|[v0.4.9](https://github.com/electron/electron/releases/tag/v0.4.9)|2013-09-20||no|||895|
|[v0.4.8](https://github.com/electron/electron/releases/tag/v0.4.8)|2013-09-20||no|||894|
|[v0.4.7](https://github.com/electron/electron/releases/tag/v0.4.7)|2013-09-13||no|||895|
|[v0.4.6](https://github.com/electron/electron/releases/tag/v0.4.6)|2013-09-12||no|||896|
|[v0.4.5](https://github.com/electron/electron/releases/tag/v0.4.5)|2013-09-09||no|||897|
|[v0.4.4](https://github.com/electron/electron/releases/tag/v0.4.4)|2013-09-05||no|||897|
|[v0.4.3](https://github.com/electron/electron/releases/tag/v0.4.3)|2013-09-02||no|||896|
|[v0.4.2](https://github.com/electron/electron/releases/tag/v0.4.2)|2013-09-02||no|||899|
|[v0.4.1](https://github.com/electron/electron/releases/tag/v0.4.1)|2013-08-27||no|||0|
|[v0.4.0](https://github.com/electron/electron/releases/tag/v0.4.0)|2013-08-19||no|||0|
|[v0.3.5](https://github.com/electron/electron/releases/tag/v0.3.5)|2013-08-16||no|||0|
|[v0.3.4](https://github.com/electron/electron/releases/tag/v0.3.4)|2013-08-15||no|||0|
|[v0.3.3](https://github.com/electron/electron/releases/tag/v0.3.3)|2013-08-15||no|||0|
|[v0.3.2](https://github.com/electron/electron/releases/tag/v0.3.2)|2013-08-13||no|||0|
|[v0.3.1](https://github.com/electron/electron/releases/tag/v0.3.1)|2013-08-12||no|||0|

<!-- END RELEASES TABLE -->

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

## Lite Version

The default export is about 10MB, as it includes a lot of metadata from the
GitHub API like release assets.

If you just need the basic info like version numbers, npm dist tags, and publish dates, there's a much smaller (<200K) dataset you can use:

```js
require('electron-releases/lite.json')
```

You can also get this at [unpkg.com/electron-releases/lite.json](https://unpkg.com/electron-releases/lite.json)

### Data

Each release contains all the data returned by the
[GitHub Releases API](https://developer.github.com/v3/repos/releases/#get-a-single-release),
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

This module is self-publishing. It runs in a
[Heroku Scheduler](https://devcenter.heroku.com/articles/scheduler)
process every ten minutes. A new version of this module is published if any of
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

If your change any file in the `script` folder you need to
bump module the following steps:

1. Create a [personal access token](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/#creating-a-token)
1. Copy-paste `.env.example` by following command:
    ```sh
    cp .env.example .env
    ```
1. Paste your token to `.env` file
1. Build the module
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

## Dependencies

None

## Dev Dependencies

- [chai](https://github.com/chaijs/chai): BDD/TDD assertion library for node.js and the browser. Test framework agnostic.
- [check-for-leaks](): avoid publishing secrets to git and npm
- [dotenv-safe](https://github.com/rolodato/dotenv-safe): Load environment variables from .env and ensure they are defined
- [github](): NodeJS wrapper for the GitHub API
- [got](): Simplified HTTP requests
- [hubdown](): Convert markdown to GitHub-style HTML using a common set of remark plugins
- [lodash](): Lodash modular utilities.
- [mocha](https://github.com/mochajs/mocha): simple, flexible, fun test framework
- [npm](https://github.com/npm/npm): a package manager for JavaScript
- [parse-link-header](https://github.com/thlorenz/parse-link-header): Parses a link header and returns paging information for each contained link.
- [semver](): The semantic version parser used by npm.
- [standard](https://github.com/standard/standard): JavaScript Standard Style
- [standard-markdown](): Test your Markdown files for Standard JavaScript Style™


## License

MIT
