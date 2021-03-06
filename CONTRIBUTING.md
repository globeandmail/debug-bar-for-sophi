# Contributing and Maintaining

First, thank you for taking the time to contribute!

The following is a set of guidelines for contributors as well as information and instructions around our maintenance process.  The two are closely tied together in terms of how we all work together and set expectations, so while you may not need to know everything in here to submit an issue or pull request, it's best to keep them in the same document.

## Ways to contribute

Contributing isn't just writing code - it's anything that improves the project.  All contributions are managed right here on GitHub.  Here are some ways you can help:

### Reporting bugs

If you're running into an issue, please take a look through [existing issues](https://github.com/globeandmail/debug-bar-for-sophi/issues) and [open a new one](https://github.com/globeandmail/debug-bar-for-sophi/issues/new) if needed.  If you're able, include steps to reproduce, environment information, and screenshots/screencasts as relevant.

### Suggesting enhancements

New features and enhancements are also managed via [issues](https://github.com/globeandmail/debug-bar-for-sophi/issues).

### Pull requests

Pull requests represent a proposed solution to a specified problem.  They should always reference an issue that describes the problem and contains discussion about the problem itself.  Discussion on pull requests should be limited to the pull request itself, i.e. code review.

For more on how 10up writes and manages code, check out our [10up Engineering Best Practices](https://10up.github.io/Engineering-Best-Practices/).

## Workflow

The `develop` branch is the development branch which means it contains the next version to be released.  `trunk` contains the latest released version as reflected in the WordPress.org plugin repository.  Always work on the `develop` branch and open up PRs against `develop`.

## Release instructions

1. Branch: Starting from `develop`, cut a release branch named `release/X.Y.Z` for your changes.
1. Version bump: Bump the version number in `package.json`, `readme.txt`, `sophi-debug-bar.php` and any other relevant files if it does not already reflect the version being released.  Update both the plugin "Version:" property and the plugin `SOPHI_DEBUG_BAR_VERSION` constant in `sophi-debug-bar.php`.
1. Changelog: Add/update the changelog in `CHANGELOG.md` and `readme.txt`.
1. Props: update `CREDITS.md` file with any new contributors, confirm 
intainers are accurate.
1. New files: Check to be sure any new files/paths that are unnecessary in the production version are included in `.distignore`.
1. Readme updates: Make any other readme changes as necessary.  `README.md` is geared toward GitHub and `readme.txt` contains WordPress.org-specific content.  The two are slightly different.
1. Merge: Make a non-fast-forward merge from your release branch to `develop` (or merge the pull request), then do the same for `develop` into `trunk` (`git checkout trunk && git merge --no-ff develop`). `trunk` contains the stable development version.
1. Test: While still on the `trunk` branch, test for functionality locally.
1. Push: Push your `trunk` branch to GitHub (e.g. `git push origin trunk`).
1. Release: Create a [new release](https://github.com/globeandmail/debug-bar-for-sophi/releases/new), naming the tag and the release with the new version number, and targeting the `trunk` branch. Paste the changelog from `CHANGELOG.md` into the body of the release and include a link to the closed issues on the [milestone](https://github.com/globeandmail/debug-bar-for-sophi/milestone/#?closed=1).
1. SVN: Wait for the [GitHub Action](https://github.com/globeandmail/debug-bar-for-sophi/actions) to finish deploying to the WordPress.org repository. If all goes well, users with SVN commit access for that plugin will receive an emailed diff of changes.
1. Check WordPress.org: Ensure that the changes are live on https://wordpress.org/plugins/debug-bar-for-sophi/. This may take a few minutes.
1. Close milestone: Edit the [milestone](https://github.com/globeandmail/debug-bar-for-sophi/milestone/#) with release date (in the `Due date (optional)` field) and link to GitHub release (in the `Description` field), then close the milestone.
1. Punt incomplete items: If any open issues or PRs which were milestoned for `X.Y.Z` do not make it into the release, update their milestone to `X.Y.Z+1`, `X.Y+1.0`, `X+1.0.0` or `Future Release`.
1. Test sites: Check the Sophi test sites to ensure the new version has been deployed there.

### What to do if things go wrong

If you run into issues during the release process and things have NOT fully deployed to WordPress.org / npm / whatever external-to-GitHub location that we might be publishing to, then the best thing to do will be to delete any Tag (e.g., https://github.com/globeandmail/debug-bar-for-sophi/releases/tag/TAGNAME) or Release that's been created, research what's wrong, and once things are resolved work on re-tagging and re-releasing on GitHub and publishing externally where needed.

If you run into issues during the release process and things HAVE deployed to WordPress.org / npm / whatever external-to-GitHub location that we might be publishing to, then the best thing to do will be to research what's wrong and once things are resolved work on a patch release and tag on GitHub and publishing externally where needed.  At the top of the changelog / release notes it's best to note that its a hotfix to resolve whatever issues were found after the previous release.
