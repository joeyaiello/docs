# Provisioning the GIT repos
After all the following steps are completed, for all changes in a monitored docset, open publishing will automatically build it and publish the content to MSDN, TechNet, or VS.com web site.

## Making the repo an Open Publishing repo
After GIT repo is created, some configuration file should be add to make it as an Open Publishing repo. After that, user could do the provision on the [portal](https://op-portal-prod.azurewebsites.net) to make the repository be monitored.

### Adding the Publishing Service Configuration File
Open Pulbishing service needs a file [.openpublishing.publish.config.json](repo-config.md) under the repository. This file tells how to build and publish the content in the repository.

### provision on the portal  ###
Once you have the publish configuration file under the repository. You could go to our [portal](https://op-portal-prod.azurewebsites.net) to provision your repo to make it be monitored.

## Adding the Build Tools Configuration
Open publishing service provide the entry point of how to build the content. Users can either use their own build tools to build the content or use the build tool provided by us directly.

Open publishing currently has two build tools. One has only simple function to build markdown content. The other one is an powerful build tool names DocasCode. It can build not only markdown content but also some specific language source code to generate page.   

### How to use the build tool provided by Open Publishing
- **Simple Build Tool**
	- Two file need to be added under the repository folder Tools/Nuget. They are [Nuget.Config](https://github.com/openpublish/docs/blob/master/Tools/NuGet/Nuget.Config) and [nuget.exe](https://github.com/openpublish/docs/blob/master/Tools/NuGet/nuget.exe). You can directly copy them to your repository.
	- Some global build configuration files need to be added under the repository root.
		- [.openpublishing.build.config.json](repo-config.md): Tells build tool how many docsets need to be built. Once a docset is added into this configuration file. Two corresponding docset configuration file should be also added to that docset. [.openpublish.build.docset.json](repo-config.md) and [TOC.md](repo-config.md) 
		- [.openpublishing.build.mdproj](repo-config.md): Then build target of msbuild. User can also inject customer step in it with msbuild language.
		- [packages.config](repo-config.md): Indicate the version of build tool. Tool with different version contains different functions.
- **DocasCode**
	- Coming Soon~

### How to use the external tool to build the markdown content
Coming soon~