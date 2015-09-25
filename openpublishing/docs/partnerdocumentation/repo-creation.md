It is the content owner responsibility to create the GIT repo and provide the right permissions to the users to access to them. 

For GIT repo, we currently plan to support both GitHub and Visual Studio Online.


## GitHub Terms ##
The GitHub documentation provides very good guidelines to ramp you up and get familiar. In any case, we include here some basic terminology to get you started.

- **Git** - An open-source version control system. Linus Torvalds created it.
- **GitHub** - A company that provides open source code repository hosting as a service. We are using their service as a content management system. GitHub is built on top of Git. To interact with GitHub, you can use their web interface or install Git tools (like Git Bash, or Visual Studio 2015) on your local machine.
- **repository (repo)** - Our content databases in GitHub. At the command line, commands that include “upstream” are acting on the repository. 
- **‘the public repo’** - External facing content repo; customers and infrequent contributors can submit changes to articles.
- **‘the private repo’** - Internal facing content repo; anyone inside Microsoft can obtain perms and contribute new articles and changes to existing articles. Frequent contributors should use the private repo, and all content with a disclosure date must be authored here.
- **fork** - Your online copy of the repository in GitHub. You push your changes into your fork first to help protect the core repository. At the command line, commands that include “origin” are acting on your fork of the repo.
- **clone** - The local copy of your fork on your computer. 
- **branch** - A copy of the repository within each core, fork, or local version of the repo. The core repository has a master branch, a daily publishing branch, and some milestone release branches. You check content into the branch that corresponds to the release you are targeting. On your local computer, you create and author within local working branches.
- **pull request** - You create a pull request to move changes from your fork to the main repository – the pull request shows all the diffs between your fork and the branch you want to changes to go to in the main repository. All pull requests are reviewed before acceptance to ensure that metadata is present, basic markdown is correct, content regressions are avoided, and that validation issues are resolved.
- **merge conflict** - When Git cannot automatically merge two different sets of changes to the same file. Merge conflicts have to be resolved manually.


## Repo creation ##

The first step is to create a GIT repository and setup it up as an open publishing repo.

- For GitHub repository setup, follow the [GitHub tutorials](https://help.github.com/articles/set-up-git/). 
- For Visual Studio Online see (TBD).


### GitHub Private vs. public repo ###

If you do not want/need external contributions (i.e. external to Microsoft), create a private repo.
If you want/need external contributions (i.e. external to Microsoft), then you need to create two repos: one public and one private.

- The private repo will contain the under development content, that is, the content that your customers cannot see yet. 
- The public repo will contain the content that is widely available and, hence, your customers can contribute to. Note that even you have not publish live your content, as long as it is in your public repo, external people can access it. 

You need to manually synchronize your private repo to your public repo whenever you are ready to make the content available to your customers. This is a method of how Azure does it:  

- Pull the changes made in the public repo into a local branch of the private repo. 
- Fix any merge conflicts and submit a pull request to the master branch in the private repo. 
- Once the pull request passes validation, merge it to the master branch in the private repo. 
- Repeat the process for the public repo and once the repos are synced, you can publish the content.
 
As Open Publishing offers local preview, you can always pull changes from the public repo to your private repo to have a full view of your content. 

The following two images show a graphical view of the recommended workflow. Note this is only added here for your reference. Original images were taken from Azure GitHub training from Tyson Nevil.

Internal contributions only workflow
![Internal created content](images/GitHub_InternalWorkflow.png)

External contributions workflow
![Internal created content](images/GitHub_ExternalWorkflow.png)

## Set up permissions to the GIT repo
For permission to access the content repo, the content owner is responsible for leveraging GITHUB permission system, and give certain people read or write permission to the repo. Our recommendation is you create an org and host the repo under that org, then add people to that org to give them write permission.

Users are always able to publish by pushing a change to a branch, as long as he has the push permission to the repo.


# Next steps #
The next steps the team will do is to do the [Repo and provisioning](repo-provision.md). Thus, we need the following information:

- Repo URLs
- Publishing end-points: MSDN, TechNet, VS.com, other. If other, we need the canonical URL you would like to have.