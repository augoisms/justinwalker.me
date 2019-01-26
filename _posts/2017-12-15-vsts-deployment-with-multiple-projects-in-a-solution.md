---
layout: post
title: VSTS deployment with multiple projects in a solution
date: '2017-12-15 00:21:22'
---

If you have multiple projects in a solution and want to specify the project to deploy, simply name it! By default, in your build definition, the _Azure App Service Deploy_ task will default to the following under _Package or Folder_:

`$(build.artifactstagingdirectory)/**/*.zip`

Instead of looking for any zip file, specify the one you want:

 `$(build.artifactstagingdirectory)/ProjectName.zip` or
 `$(build.artifactstagingdirectory)/Company.ProjectName.zip`

![azure app service deployment task](/content/images/2017/12/azure-app-deploy.png)

Basically, whatever your project is named. Hope this helps someone because I struggled with this for a while.
