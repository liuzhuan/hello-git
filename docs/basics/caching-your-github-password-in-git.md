# Caching your Github password in Git

https://help.github.com/articles/caching-your-github-password-in-git/

If you're cloning GitHub repositories using HTTPS, you can use a credential helper to tell Git to remember your GitHub username and password every time it talks to GitHub.

If you clone GitHub repositories using SSH, then you authenticate using SSH keys instead of a username and password. For help setting up an SSH connection, see Generating an SSH Key.

> Tip: You need Git 1.7.10 or newer to use the credential helper.

Turn on the credential helper so that Git will save your password in memory for some time. By default, Git will cache your password for 15 minutes.

## In Terminal, enter the following:

```
git config --global credential.helper cache
# Set git to use the credential memory cache
```

## To change the default password cache timeout, enter the following:

```
git config --global credential.helper 'cache --timeout=3600'
# Set the cache to timeout after 1 hour (setting is in seconds)
```