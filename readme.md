   
usage
npx release-setup -- Run by developer In the current branch instantiates the release, increments the version & upserts changelog.md  
npx release-process-ci -- Run by CICD - where the commit has a tag v[something] e.g. v3.3.5 then run this command to: create the GitHub release in "prerelease" mode
npx release-finalise-ci -- Run by CICD - post production release task to change release from "prerelease" to "latest"
    

NOTE: when working behind a corporate network you might have to 
#set npm to use the corporate cert 
npm config set cafile "C:\certs\AGLCorp-RootCA.cer"

#set node to use a the corporate cert
export NODE_EXTRA_CA_CERTS="C:\certs\AGLCorp-RootCA.cer"

#or the unsafe way 
#Node
export NODE_TLS_REJECT_UNAUTHORIZED=0

#NPM
npm set strict-ssl false