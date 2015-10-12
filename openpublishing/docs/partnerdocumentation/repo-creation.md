# Creating the GIT repos
It is the content owner's responsibility to create the GIT repos and provide the right permissions to the users to access them. 
A GIT repo is either GitHub or Visual Studio Online.

If you are not familiar with GitHub, check out a summary of [GitHub terminology](GitHub-terminology.md) used in this documentation as well as the [GitHub tutorials](https://github.com/).

The first step is to create a GIT repository and make it either public or private (see next section for information):
- For GitHub repository setup, follow the [GitHub tutorials](https://help.github.com/articles/set-up-git/). 
- For Visual Studio Online see (TBD).
 
**Note that you do not have to create localized repos. This is done automatically based on the [localization file configuration](repo-creation.md)**.

## Default branch
Open Publishing provision is made out of the "live" branch. So once you have created the repos, make sure that you select the "live" branch as the default one. 

## GitHub Private vs. public repo

If you do not want/need external contributions (i.e. external to Microsoft), you would need create a private repo.
If you want/need external contributions (i.e. external to Microsoft), then you would need to create two repos: one public and one private.

- The private repo will contain the under development content, that is, the content that your customers cannot see. 
- The public repo will contain the content that is widely available, which your customers can contribute to. Note, even if you have not published you content live, anything in the public repo will be visible to external users.

You can also create a private fork out of your private repo. This [article](https://opensourcehub.microsoft.com/articles/github-create-private-fork-of-public-repo) shows you how. 

If you create both kinds of repo (private and public), you need to manually synchronize your private repo to your public repo when you are ready to make the content available to your customers. 
Here is a recommendation:  

- Pull the changes made in the public repo into a local branch of the private repo. 
- Fix any merge conflicts and submit a pull request to the (master)(GitHub-terminology.md) branch in the private repo.
- Once the pull request passes validation, merge it to the master branch in the private repo. 
- Create a pull request to add the info from the private repo into the public repo. Revolve any conficts.
- Once the two repos have synced, you can publish the content you merged in from the public repo.
 
As Open Publishing offers local preview, you can always pull changes from the public repo to your private repo to have a full view of your content. 

The following two images show a graphical view of the recommended workflow. Note this is only added here for your reference.

### Internal contributions only workflow
![Internal created content](../images/GitHub_InternalWorkflow.png)

### External contributions workflow
![Internal created content](../images/GitHub_ExternalWorkflow.png)

## Creating your repo in the Microsoft GitHub Organization
We recommend that you create the repo in the Microsoft GibHub Organization. That way, you can benefit of all the advantages the organizaiton provides, including enabling Contributaion License Agreement (CLA) automation. See [How to Create a Repo in the Microsoft GitHub Organization](https://opensourcehub.microsoft.com/articles/how-to-create-new-repo-in-microsoft-github-org-self-service) for details.

## Set up permissions to the GIT repo
For permission to access the content repo, the content owner is responsible for leveraging GITHUB permission system. The owner will need to give the appropriate users read or write permission to the repo (private or public). Our recommendation is you create an org and host the repo under that org, then add users to that org to give them write permission. 

Users are always able to publish by pushing a change to a branch, as long as they have the push permission to the repo.

## Creating and setting up localized repos
The localized content will live in a separated repo, connected to the English one. 

For that, you need to modify the config file **.localization-config**.This file contains the definition of the localized repos.
 
- **locales** - add the locales you would like to localize in the form of locale-culture set. E.g. "ja-jp", "de-de",...
- **files** - List all the folders and file types to localize, include the docset name plus "**" to include all the folders underneath, and then mask the file types. E.g. "virtualization/**/*.md" includes all the Markdown files under the docset, including all the subfolders.
- **includeDependencies**
	- Set to true to include in the handoffs the topic dependencies (includes). 
	- Set to false to only include the Markdown files.
- **autoPush**
	- Set to true to automatically check-in the hand back files into the localized repo.
	- Set to false to create a pull request for the hand back so an admin can approve.

Once this file has been committed, if there is a new language added under locales, the localized repo will be created automatically after the English branches publish.

## Next steps
The next step we need to do is to [provision the repo](repo-provision.md). VSC will do that for you. Please make sure that:
Please send Xiaokai He and Sandra Aldana the following information:

- Repo URLs
- Make sure that the live branch is the default in the repo(s) to provision.
- Repo branches and which one to associate to stage and live. In general, master should be for staging and live should be for publishing to live. See (Publis)[publish.md] topic. 
- Publishing end-points: MSDN, TechNet, VS.com, other. If other, we need the canonical URL you would like to have for your site.
