# Provisioning the GIT repos
After all the following steps are completed, open publishing will automatically build and publish automatically the updated content to MSDN, TechNet, or VS.com web sites.

## Making the repo an Open Publishing repo

### Adding the Publishing Service Configuration File
Once the GIT repo is created, create  [.openpublishing.publish.config.json](repo-config.md#-openpublishing-publish-config-json) file under the repository. This file tells Open Publishing how to build and publish the content in the repository.

### Provision on the portal
Once you have the publish configuration file under the repository. You could go to our [portal](https://op-portal-prod.azurewebsites.net) to provision your repo to make it be monitored.

## Adding the Build Tools Configuration
Open publishing service provides the entry point of how to build the content. Users can either use their own build tools to build the content or use the build tool provided by Open Publishing directly.

Open publishing currently has two build tools. One has only simple function to build Markdown content. The other one is a powerful build tool names DocasCode. It can build not only markdown content but also some specific language source code to generate a page.   

### How to use the build tool provided by Open Publishing
- **Simple Build Tool**
	- Two file need to be added under the repository folder Tools/Nuget. They are [Nuget.Config](https://github.com/openpublish/docs/blob/master/Tools/NuGet/Nuget.Config) and [nuget.exe](https://github.com/openpublish/docs/blob/master/Tools/NuGet/nuget.exe). You can directly copy them to your repository.
	- Some global build configuration files need to be added under the repository root.
		- [.openpublishing.build.config.json](repo-config.md#-openpublish-build-config-json): Tells build tool how many docsets need to be built. Once a docset is added into this configuration file. Two corresponding docset configuration file should be also added to that docset. [.openpublish.build.docset.json](repo-config.md#-openpublish-build-docset-json) and [TOC.md](repo-config.md#TOC-md) 
		- [.openpublishing.build.mdproj](repo-config.md#-openpublish-build-mdproj): The build target of msbuild. User can also inject customer step in it with msbuild language.
		- [packages.config](repo-config.md#packages-config): Indicate the version of build tool. Tool with different version contains different functions.
- **DocasCode**
	- Coming Soon~

### How to use the external tool to build the markdown content
Coming soon~
