---
title: "Import API to microcks with gitlab user token"
date: 2021-09-01T06:00:00+01:00
type: Engineering
tags:
  - GitLab
  - Microcks
authors:
  - name: Romain Gil
---

> tl;dr

Microcks can import API esealy with a Git repository using. 

But is not the same mean for a private gitlab repository if you are simple user.

The token gives access only to Gitlab API and Git and do not give access to RAW url.

This post will show you a mean to connect Microcks with Gitlab even if you are simple user.

## Summary

To connect Microcks with RAW format to gitlab even if your repository is private you must use the API.

Follow the few steps to do it:

1. Create a Repository token
2. Add token to microcks
3. Know the project ID
4. Make the api URL (return a raw format)
5. Importation exemple
6. Conclusion

## Create Repository token


### Go to your gitlab repository

The gitlab repository token can be created on the setting.

![image](/images/blog/import-api-with-gitlab-private-repo-setting_access_token.jpg)

### Create access token

You must configure the token of the gitlab repository like this:

![image](/images/blog/import-api-with-gitlab-private-repo-token.jpg)

## Add token to microcks

To add token to microcks your user must be administrator who permit acces to administration settings.

![image](/images/blog/import-api-with-gitlab-private-repo-add_token_microcks.jpg)

## Know project ID 

You can find the id of your project on the home page of your repository on gitlab UI interface.

![image](/images/blog/import-api-with-gitlab-private-repo-project_ID.jpg)

## Make the api URL

The Api url to get a RAW file must look like this:

https://<GITLAB_URL>/api/v4/projects/<ID_PROJECT>/repository/files/<PATH>%2F<FILE_NAME>/raw?ref=<PROJECT_BRANCH>

If the file is in directory you need to encode the character '/' with %2 on the <PATH> string.

## Importation exemple

### Configure repository url

![image](/images/blog/import-api-with-gitlab-private-repo-import_exemple.jpg)

### Select Token

![image](/images/blog/import-api-with-gitlab-private-repo-select_token.jpg)

## Conclusion

This workaround is working only with Gitlab if your user is not an admin user.

