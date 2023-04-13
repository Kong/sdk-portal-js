# sdk-portal-js


## Publishing Manually

Please note this section should be removed eventually by [this story](https://konghq.atlassian.net/browse/TDX-3077).

1. Clone the repo and enter the directory.
2. Make sure you are checked out on the `main` branch (`git checkout main && git pull origin main`)
3. Log in as `konginc` via NPM. The credentials and One-Time Password can be found in Kong's 1Password.
4. Manually edit the `version` property of [`package.json`](./package.json) to be the version you wish to publish (i.e. `0.0.1-beta.40`).
5. If you wish to verify what is being published, run `npm publish --dry-run`, and the library should build and the package contents will be listed as output.
6. Run `npm publish`
