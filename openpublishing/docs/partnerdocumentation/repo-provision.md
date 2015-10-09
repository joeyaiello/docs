# Provisioning the GIT repos - This is done by VSC

**All these steps are done by VSC, so no worry about them**

After all the following steps are completed, Open Publishing will automatically build and publish the updated content from a monitored docset to MSDN, TechNet, or VS.com web sites.

## Making the repo an Open Publishing repo

### Adding the Publishing Service Configuration File
Once the GIT repo has been created, some configuration files should be added to make it an Open Publishing repo. You can get sample files from this repository.

Create [.openpublishing.publish.config.json](repo-config.md#-openpublishing-publish-config-json) file under the repository. This file tells Open Publishing how to build and publish the content found in the GIT repo. 

### Provisioning on the portal
Once you have the publish configuration file under the repository, go to [portal](https://op-portal-prod.azurewebsites.net) to have the repo monitored.

## Adding the Build Tools Configuration
The Open Publishing service provides the entry point for how to build the content. Users can either use their own build tools or use the build tool provided by Open Publishing service.

Open publishing currently has two build tools. The first build tool only has a simple function to build Markdown content. The is a powerful build tool called DocasCode (link will follow). In addition to Markdown it can build documentation from specific language source code.   

### How to use the build tools provided by Open Publishing
- **Simple Build Tool**
	- Two files need to be added under the repository folder **Tools/Nuget**. They are [Nuget.Config](https://github.com/openpublish/docs/blob/master/Tools/NuGet/Nuget.Config) and [nuget.exe](https://github.com/openpublish/docs/blob/master/Tools/NuGet/nuget.exe). You can directly copy them to your repository.
	- Some global build configuration files need to be added at the root of the repository.
		- [.openpublishing.build.config.json](repo-config.md#-openpublish-build-config-json): Tells build tool how many docsets need to be built. Once a docset is added into this configuration file, two corresponding docset configuration file should be also added to that docset: [.openpublish.build.docset.json](repo-config.md#-openpublish-build-docset-json) and [TOC.md](repo-config.md#TOC-md) 
		- [.openpublishing.build.mdproj](repo-config.md#-openpublish-build-mdproj): The build target of msbuild. User can also inject custom steps using msbuild language.
		- [packages.config](repo-config.md#packages-config): Indicates the version of build tool. Tool with different versions will have different capabilities.
- **DocasCode**
	- Coming Soon~

### How to use the external tool to build the markdown content
Coming soon~
