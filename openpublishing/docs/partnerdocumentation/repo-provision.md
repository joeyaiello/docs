# Provisioning the GIT repos#
After all the following steps are completed, for all changes in a monitored docset, open publishing will automatically build it and publish the content to MSDN, TechNet, or VS.com web site.


## Making the repo an Open Publishing repo ##
After GIT repo is created, VSC will configure it to be monitored by open publishing. Eventually, we will extend the provisioning rights to other users in the content teams. 

### Adding the docset to the Open Publishing  ###
**VSC will do this step**

Under an Open Publishing GIT repository there will be multiple docsets. A docset is a group of documents that share the same configuration like template, base url, etc. (similar to center in current OA). Each docset is a folder, under which there is a .openpublish.build.docset.json that defines the basic properties of a docset.

Under the root folder of a repository, there is a **siteCatalog.json** that defines all docsets in this repo.

A docset must be added to siteCatalog.json to be detected by open publishing. Docset must be added to the monitor list manually, open publishing won't monitor docset creation/deletion and automatically provision them.

