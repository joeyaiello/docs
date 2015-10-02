# URL Management #
Your URL will be defined by the domain where content gets published, locale, docset name,  folder structure, and file names in your repo. 

 `http://{site}/{locale}/[{"version"}][{"product"}]/{ContentPath}`



**Parameter**|**Required**|**Source**|**Description**  
---------|---------|---------|---------|---------
Site| Required | Publishing metadata set at account provisioning | The URLs to the host name of the Web app that renders the content. It can be the URL for public site, internal testing or staging environment, or even localhost of local preview.
Locale| Required | Document metadata from metadata file in [GIT repository](repo-config.md) | A string in {language}-{territory} format to indicate the locale of the content.
Version | Optional | Document metadata from metadata file in [GIT repository](repo-config.md) | A SEO friendly version string that contains a human friendly product name and a version
Product | Required | Document metadata from metadata file in [GIT repository](repo-config.md) | A string that describes the product for which the content is written        
ContentPath | Required | File name in [GIT repository](repo-config.md) | A path structure for a content item that authors their content. This path structure is the folder path of a content item in a repo.


With this URL schema defined, content author and site management are given great flexibility in the layout of the content files in repo as well as rendering URLs. 






