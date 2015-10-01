# Creating the English repos #
It is the content owner responsibility to create the English GIT repos and provide the right permissions to the users to access them. 
A GIT repo is either GitHub or Visual Studio Online.

If you are not familiar with GitHub, check out a summary of [GitHub terminology](GitHub-terminology.md) used in this documentation.

The first step is to create a GIT repository and make it either public or private (see next section for information).

- For GitHub repository setup, follow the [GitHub tutorials](https://help.github.com/articles/set-up-git/). 
- For Visual Studio Online see (TBD).

**Note that you do not have to create localized repos. This is done automatically based on the [localization file configuration](repo-provision.md)**.

## GitHub Private vs. public repo ##

If you do not want/need external contributions (i.e. external to Microsoft), you would need create a private repo.
If you want/need external contributions (i.e. external to Microsoft), then you would need to create two repos: one public and one private.

- The private repo will contain the under development content, that is, the content that your customers cannot see yet. 
- The public repo will contain the content that is widely available and, hence, your customers can contribute to. Note that even you have not publish live your content, as long as it is in your public repo, external people can access it. 

You can also create a private fork out of your private repo. This [article](https://opensourcehub.microsoft.com/articles/github-create-private-fork-of-public-repo) shows you how. 

If you create the two repos (private and public), you need to manually synchronize your private repo to your public repo whenever you are ready to make the content available to your customers. Here is a recommendation:  

- Pull the changes made in the public repo into a local branch of the private repo. 
- Fix any merge conflicts and submit a pull request to the master branch in the private repo. 
- Once the pull request passes validation, merge it to the master branch in the private repo. 
- Create a pull request to add the info from the private repo to the public repo. Revolved any conficts.
- Once the two repos are synced, you can publish the content from the public repo.
 
As Open Publishing offers local preview, you can always pull changes from the public repo to your private repo to have a full view of your content. 

The following two images show a graphical view of the recommended workflow. Note this is only added here for your reference.

### Internal contributions only workflow ###
![Internal created content](../images/GitHub_InternalWorkflow.png)

### External contributions workflow ### 
![Internal created content](../images/GitHub_ExternalWorkflow.png)

## Creating your repo in the Microsoft GitHub Organization##
We recommend that you create the repo in the Microsoft GibHub Organization. That way, you can benefit of all the advantages the organizaiton provides, including enabling Contributaion License Agreement (CLA) automation. See [How to Create a Repo in the Microsoft GitHub Organization](https://opensourcehub.microsoft.com/articles/how-to-create-new-repo-in-microsoft-github-org-self-service) for details.

## Set up permissions to the GIT repo
For permission to access the content repo, the content owner is responsible for leveraging GITHUB permission system, and give certain people read or write permission to the repo. Our recommendation is you create an org and host the repo under that org, then add people to that org to give them write permission.

Users are always able to publish by pushing a change to a branch, as long as he has the push permission to the repo.




## Next steps ##
The next steps the team will do is to do the [Repo and provisioning](repo-provision.md). Thus, please send Xiaokai He and Sandra Aldana the following information:

- Repo URLs
- Publishing end-points: MSDN, TechNet, VS.com, other. If other, we need the canonical URL you would like to have for your site.
