# Configuring the repos
Content teams need to configure their repos after provisoning.

## Open Publishing Service Configuration
Open publishing service need to know how to publish the content user provide. The following file ".openpublishing.publish.config.json" is a configuration of the service.

### .openpublishing.publish.config.json
This file defines the basic properties of a docset.

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

## Build Tools Configuration
Open Publishing provide a build tool for user to build the markdown file. If user want to use that tool, the following three configuration files need to be added in the repository root.

### .openpublish.build.config.json
This file defines the paths for the different docsets configuration files. There is nothing else to be configured in this file.

### .openpublish.build.docset.json
- **toc_file**: Points to the location of the curerent docset file, in general, "TOC.md".
- **exclude_path_patterns** - specify file extensions of files you would like the build to ignore. Example: [ "*.vsdx" ]
- **common_metadata** - Metadata supported  so far: 
	- "ROBOTS": "NOINDEX, NOFOLLOW"

### packages.config
This file contains the latest version of the build package. By default, the latest version will always be used. However, if you would like to use a previous version (you might not need all the functionality that is available and might make your build slower), then you can specify the version here. The engineering team will maintain a list of all the packages available and main features for each. 


## Branches
In open publishing, we use GIT branches to maintain different copies of the same content. Same topic in different branches will be published to different urls of rendering sites. This could be used in several scenarios:
1. Stage/promote. User can use one branch as staging branch and merge it to a live branch as a promote operation.
2. Private working branch. User can create his own branch to save files that is still under writing, and merge it to common branch when it's ready. Files in private branch can still be validated/previewed by open publishing.

### Live Branch
Among all branches, there should be only one branch that is exposed to external users, and other staging/working branches are only used by writers for internal testing. This branch is called "Live" branch. Live branch can be identified by a special branch name. Content in live branch will be published to the live site. Content in other branches will still be published, but only to stage or sandbox.

### Dogfooding new features using Branches

It'll be a common case that user wants to try new features (like a new markdown extension) in his working branch while keep live branch using stable features. We're going to support this by allowing the user to specify the build toolset they want to use (in GIT repo). We'll release multiple versions of the build tool (specified in packages.config) and let the user choose which one they want to use. After they test the feature in working branch, they can merge the content to live branch then live branch will also upgrade to use the new build tool.

