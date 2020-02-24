<!--
SPDX-FileCopyrightText: © 2020 Liferay Inc. <https://liferay.com>

SPDX-License-Identifier: MIT
-->

# Release process

1.  Confirm that you have a clean worktree.

    `git status` should show no changed, staged, or untracked files.

2.  Run the `yarn ci` script.

    This checks formatting, runs lints checks, and runs all tests.

    If necessary, apply fixes, submit a pull request, and when it is merged, start again at step 1.

3.  Update [CHANGELOG.md](./CHANGELOG.md).

    Run [liferay-changelog-generator](https://www.npmjs.com/package/liferay-changelog-generator):

        npx liferay-changelog-generator --version=v4.1.0

4.  Review the changes.

    Use `git diff` to confirm that the CHANGELOG.md looks correct. Feel free to edit it if you want to make improvements. Then stage the changes:

        git add CHANGELOG.md

5.  Tag and publish the new release.

    Run `yarn version --minor` (or `--major`, or `--patch`, as appropriate).

    This will update the package.json and create a tagged commit, including the updates to the CHANGELOG that you previously made.

        We use [liferay-js-publish](https://github.com/liferay/liferay-npm-tools/tree/master/packages/liferay-js-publish) from the "postversion" script to take care of pushing to the repo, and actually publishing to the NPM registry; just follow the prompts.

6.  Update the release notes.

    Take the new section from the top of the CHANGELOG and add it to [the release page](https://github.com/liferay/eslint-config-liferay/releases) on GitHub.

7.  Sanity check [the eslint-config-liferay page](https://www.npmjs.com/package/eslint-config-liferay) on npmjs.com

    Specifically, you should see the version you just released under the "Versions" tab on that page.
