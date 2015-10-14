# Provisioning the GIT repos - (VSC task)

After all the following steps are completed, Open Publishing will automatically build and publish the updated content from a monitored docset to MSDN, TechNet, or VS.com web sites. You should have got from the partner the information listed in the (repo creation page)[..\partnerdocs\repo-creation.md]

You can get a sample of the files to be added to the repo from this site.
 
## 1. Making the repo an Open Publishing repo


### 1.1. Adding the Publishing Service Configuration File: .openpublishing.publish.config.json
This file needs to be under the repository. This file tells Open Publishing how to build and publish the content found in the GIT repo. 

- **build_entry_point**: Indicate how to run the build. User can either use the build tool OP provides or use their own tools to build the content.
- **docsets_to_publish**: A collection of docsets that need to be published.
	- **docset_name** - Provide the name of the docset. This docset need to provisioned on portal at first, otherwise the content under the docset won't be published.
		- For different docsets the names should be different.
		- For docsets that just different in locale or version, the name should be same. Otherwise, the fallback logic won't work.
	- **"build_output_subfolder"** - The relative output sub folder of build tool. Content that has been built will be put there. Only content under that folder will be published. So this value depends on the build tools.  
	- **version** - Version of current content. Start from 0.
	- **locale** - Indicate current docset language.
	- **open_to_public_contributors**
		- Set to true if you want your customers to contribute to the content.
		- Set to false if you do not want your customers to contribute to the content.
- **notification_subscribers** - Provide the email array of some ones who want to receive the notification.


### 1.2. Provisioning on the portal
- Once you have the publish configuration file under the repository, go to [portal](https://op-portal-prod.azurewebsites.net) to have the repo monitored.
- The repo needs to have a live branch in order to be monitored by Open Publishing.
- Ignore the "Base Path" field. It cannot be configured via the portal. This field would be the common base path for all the topics in this docset, and is eventually part of the rendering URL.

## 2. Adding the Build Tools Configuration
The Open Publishing service provides the entry point for how to build the content. Users can either use their own build tools or use the build tool provided by Open Publishing service.

Open publishing currently has two build tools. The first build tool only has a simple function to build Markdown content. The is a powerful build tool called DocasCode (link will follow). In addition to Markdown it can build documentation from specific language source code.   

### 2.1 Assign the build tools provided by Open Publishing

#### 2.1.1 Simple Build Tool for Markdown
Two files need to be added under the repository folder **Tools/Nuget**. They are [Nuget.Config](https://github.com/openpublish/docs/blob/master/Tools/NuGet/Nuget.Config) and [nuget.exe](https://github.com/openpublish/docs/blob/master/Tools/NuGet/nuget.exe).

Some global build configuration files need to be added at the root of the repository.
- **.openpublishing.build.config.json**: Tells build tool how many docsets to build. 
- Two corresponding docset configuration file should be also added to each  docset:
	- **.openpublish.build.docset.json**
		- **toc_file**: Points to the location of the curerent docset file, in general, "TOC.md".
		- **exclude_path_patterns** - specify file extensions of files you would like the build to ignore. Example: [ "*.vsdx" ]
		- **common_metadata** - Metadata supported  so far: 
		- "ROBOTS": "NOINDEX, NOFOLLOW"
	- [TOC.md](../partnerdocs/repo-config.md#TOC-md)
	
- **.openpublishing.build.mdproj**: The build target of msbuild. User can also inject custom steps using msbuild language.
- [packages.config](../partnerdocs/repo-config.md#packages-config): Indicates the version of build tool. Tool with different versions will have different capabilities. By default, the latest version will always be used. However, if you user like to use a previous version (they might not need all the functionality that is available and might make your build slower), then they can specify the version here. The engineering team will maintain a list of all the packages available and main features for each.

2.1.2 **DocasCode**
	- Coming Soon~

### 2.2. How to use the external tool to build the markdown content
	- Coming Soon~

