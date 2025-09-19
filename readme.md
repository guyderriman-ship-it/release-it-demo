
npx release-process-ci -- Run by CICD - where the commit has a tag v[something] e.g. v3.3.5 then run this command to: create the GitHub release in "prerelease" mode
npx release-finalise-ci -- Run by CICD - post production release task to change release from "prerelease" to "latest"
    

npm config set cafile "C:\certs\AGLCorp-RootCA.cer"




# Release-It Demo

## Setup

1. **Create your `.env` file**
	 - Copy `template.env` and rename it to `.env` in the project root.
	 - Create a GitHub PAT (Personal Access Token) with `repo` access.
	 - Add your new PAT token to the `.env` file.

## Usage

- **Developer (local):**
	```bash
	npx release-setup
	```
	Instantiates the release, increments the version, and upserts `CHANGELOG.md`.

- **CI/CD (prerelease):**
	```bash
	npx release-process-ci
	```
	Run when the commit has a tag (e.g., `v3.3.5`). Creates the GitHub release in "prerelease" mode.

- **CI/CD (finalise):**
	```bash
	npx release-finalise-ci
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

- **(Unsafe) Disable certificate validation:**
	- Node.js:
		```bash
		export NODE_TLS_REJECT_UNAUTHORIZED=0
		```
	- npm:
		```bash
		npm set strict-ssl false
		```