# Remember Github account

https://help.github.com/articles/connecting-to-github-with-ssh/

You can connect to Github using SSH.

## About SSH

Using the SSH protocol, you can connect and authenticate to remote servers and services. With SSH keys, you can connect to GitHub without supplying your username or password at each visit.

When you set up SSH, you'll generate an SSH key and add it to the ssh-agent and then add the key to your GitHub account. Adding the SSH key to the ssh-agent ensures that your SSH key has an extra layer of security through the use of a passphrase. 

We recommend that you regularly review your SSH keys list and revoke any that are invalid or have been compromised.

> **revoke**: When people in authority revoke something such as a license, a law, or an agreement, they cancel it.

> **compromise**: cause to become vulnerable or function less effectively.

## Checking for existing SSH keys

Before you generate an SSH key, you can check to see if you have any existing SSH keys.

Note: DSA keys were deprecated in OpenSSH 7.0. If your operating system uses OpenSSH, you'll need to use an alternate type of key when setting up SSH, such as an RSA key.

```
ls -al ~/.ssh
```

to see if existing SSH keys are present.

## Generating a new SSH key and adding it to the ssh-agent

After you've checked for existing SSH keys, you can generate a new SSH key to use for authentication, then add it to the ssh-agent.

### Generating a new SSH key

1. Open Terminal
2. Paste the text below, substituting in your GitHub email address.

```
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

This creates a new ssh key, using the provided email as a label.

### Adding your SSH key to the ssh-agent

1. Start the ssh-agent in the background

```
eval "$(ssh-agent -s)"
```

2. Add your SSH private key to the ssh-agent. 

```
ssh-add ~/.ssh/id_rsa
```

## [Adding a new SSH key to your GitHub account](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/)

To configure your GitHub account to use your new SSH key, you'll also need to add it to your GitHub account.

## Testing your SSH connection

After you've set up your SSH key and added it to your GitHub account, you can test your connection.

```
ssh -T git@github.com
# Attempts to ssh to GitHub
```

## Working with SSH key passphrases

You can secure your SSH keys and configure an authentication agent so that you won't have to reenter your passphrase every time you use your SSH keys.

> **passphrase**: A passphrase is a sequence of words or other text used to control access to a computer system, program or data. A passphrase is similar to a password in usage, but is generally longer for added security.

[Reviewing your SSH keys](./reviewing-your-ssh-keys.md)