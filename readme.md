# Release-It Demo

## Setup

1. **Create your `.env` file**
	 - Copy `template.env` and rename it to `.env` in the project root.
	 - Create a GitHub PAT (Personal Access Token) with `repo` access.
	 - Add your new PAT token to the `.env` file.

## Usage

- **Developer (local):**
	```bash
	npx release-initiate
	```
	Instantiates the release, increments the version, and upserts `CHANGELOG.md`.

- **CI/CD (prerelease):**
	```bash
	npx release-publish-prerelease-ci
	```
	Used in the CI - detect if commit has a tag (e.g., `v3.3.5`) then run this command. It creates the GitHub release in "prerelease" mode.

- **CI/CD (finalise):**
	```bash
	npx release-finalise-prerelease-ci
	```
	Post-production release task to change the release from "prerelease" to "latest".

## Corporate Network Notes

If working behind a corporate network, you may need to configure certificates:

- **Set npm to use the corporate cert:**
	```bash
	npm config set cafile "C:\certs\AGLCorp-RootCA.cer"
	```

- **Set Node.js to use the corporate cert:**
	```bash
	export NODE_EXTRA_CA_CERTS="C:\certs\AGLCorp-RootCA.cer"
	```

- **(OR UNSAFE NOT RECOMMENDED ) Disable certificate validation:**
	- *** Node.js:**
		```bash
		export NODE_TLS_REJECT_UNAUTHORIZED=0
		```
	- *** npm:**
		```bash
		npm set strict-ssl false
		```