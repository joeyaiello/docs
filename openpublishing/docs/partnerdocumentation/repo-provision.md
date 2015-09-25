## Repo provisioning ##
After all the following steps are completed, for all changes in a monitored docset, open publishing will automatically build it and publish the content to MSDN, TechNet, or VS.com web site.


### Making the repo an Open Publishing repo ###
After GIT repo is created, VSC will configure it to be monitored by open publishing. Eventually, we will extend the provisioning rights to other users in the content teams. 

### Adding the docset to the Open Publishing  ###
**VSC will do this step**

Under an Open Publishing GIT repository there will be multiple docsets. A docset is a group of documents that share the same configuration like template, base url, etc. (similar to center in current OA). Each docset is a folder, under which there is a .openpublish.build.docset.json that defines the basic properties of a docset.

Under the root folder of a repository, there is a **siteCatalog.json** that defines all docsets in this repo.

A docset must be added to siteCatalog.json to be detected by open publishing. Docset must be added to the monitor list manually, open publishing won't monitor docset creation/deletion and automatically provision them.


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
This file defines the paths for the different configuration files.

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


