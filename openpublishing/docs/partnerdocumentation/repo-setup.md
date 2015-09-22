# Repository Set Up #
The following steps show how to setup and provision the repo.

## Repo creation ##
The first step of open publishing is to create a GIT repository and setup it as an open publishing repo.
For GIT repo, we currently plan to support both GitHub and Visual Studio Online.

- For GitHub repository setup, follow the [GitHub tutorials](https://help.github.com/articles/set-up-git/). 
- For Visual Studio Online see (TBD).

## Repo provisioning ##
After all the following steps are completed, for all changes in a monitored docset, open publishing will automatically build it and publish the content to MSDN web site.


### Making the repo an Open Publishing repo ###
After GIT repo is created, VSC will configure it to be monitored by open publishing. Eventually, we will extend the provisioning rights to other users in the content teams. 

### Adding the docset to the Open Publishing  ###
**VSC will do this step**

Under an Open Publishing GIT repository there will be multiple docsets. A docset is a group of documents that share the same configuration like template, base url, etc. (similar to center in current OA). Each docset is a folder, under which there is a .openpublish.build.docset.json that defines the basic properties of a docset.

Under the root folder of a repository, there is a **siteCatalog.json** that defines all docsets in this repo.

A docset must be added to siteCatalog.json to be detected by open publishing. Docset must be added to the monitor list manually, open publishing won't monitor docset creation/deletion and automatically provision them.

Here is a diagram that illustrates the structure of an open publishing GIT repo.

/

|- siteCatalog.json

|- docset1/

|  |- docset.json

|  |- a.md

|  \- b.md

\- docset2/

   |- docset.json

   |- c.md

   \- d.md

### Creating and setting up localized repos ###
The localized content will live in a separated repo, connected to the English one. 

For that, you need to modify the file **.localization-config**.This file contains the definition of the localized repos.
 
- **locales** - add the locales you would like to localize in the form of locale-culture set. E.g. "ja-jp", "de-de",...
- **files** - List all the folders and file types to localize. E.g. "virtualization/**/*.md"
- **includeDependencies**
	- Set to true to include in the handoffs the topic dependencies (includes). 
	- Set to false to only include the Markdown files.
- **autoPush**
	- Set to true to automatically check-in the hand back files into the localized repo.
	- Set to false to create a pull request for the hand back so an admin can approve.

Once this file has been committed, if there is a new language added under locales, the localized repo will be created automatically.


## Configure the repo ##
Here is the repo configuration you need to do after setting up and provisioning the repo.

### .openpublish.build.config.json ###
This file defines some basic properties for the full repo.

- **docset_files** - Defines the path for the docset.json file. Example: *openpublishing/corefx/Docset.json*
- **build_config** - Build configurations
	- **incremental**
		- Set to true if you want to build only the files that have changed. 
		- Set to false to build the full docset each time.
	- **force_build** 
		- Set to true if you want the build automatically triggered once the content is added to the branch.
		- Set to false if you want to do manual builds.
	- **notification_subscribers** - Add the full mail alias of the user or Distribution List that should receive mail notifications. For example "OPBuild@microsoft.com" 

### .openpublish.build.docset.json ###
This file defines the basic properties of a docset.

- **docset_name** - Provide the name of the docset. This would be part of the URL.
- **site_name** - Site where you are publishing. See metadata.
- **toc_file** - Link to your TOC file. By default it would be TOC.md. 
- **template** - Leave it to ThreeColumns, as we only support one type of template right now. 
- **product_family** - If publishing to MSDN or TechNet, you need to provide this information. See metadata. 
- **product_version** - If publishing to MSDN or TechNet, you need to provide this information. See metadata. 
- **Locale** - Leave it is  "en-us", localized repos are defined in a separated config file.
- **open_to_public_contributors**
	- Set to true if you want your customers to contribute to the content.
	- Set to false if you do not want your customers to contribute to the content.
- **common_metadata** - Provide other metadata  you would like to use.


