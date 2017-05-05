# Reviewing your SSH keys

https://help.github.com/articles/reviewing-your-ssh-keys/

To keep your credentials secure, you should regularly audit your SSH keys, deploy keys, and review authorized applications that access your GitHub account.

You can delete unauthorized (or possibly compromised) SSH keys to ensure that an attacker no longer has access to your repositories. You can also approve existing SSH keys that are valid.

1. In the upper-right corner of any page, click your profile photo, then click Settings.

2. In the user settings sidebar, click **SSH and GPG keys**.

3. On the SSH Settings page, take note of the SSH keys associated with your account. For those that you don't recognize, or that are out-of-date, click Delete. If there are valid SSH keys you'd like to keep, click Approve.

> Note: If you're auditing your SSH keys due to an unsuccessful Git operation, the unverified key that caused the SSH key audit error will be highlighted in the list of SSH keys.

4. Open Terminal.

5. Start the ssh-agent in the background.

```
eval "$(ssh-agent -s)"
Agent pid 59566
```

6. Find and take a note of your public key fingerprint. If you're using OpenSSH 6.7 or older:

```
ssh-add -l
2048 a0:dd:42:3c:5a:9d:e4:2a:21:52:4e:78:07:6e:c8:4d /Users/USERNAME/.ssh/id_rsa (RSA)
```

If you're using OpenSSH 6.8 or newer:

```
ssh-add -l -E md5
2048 MD5:a0:dd:42:3c:5a:9d:e4:2a:21:52:4e:78:07:6e:c8:4d /Users/USERNAME/.ssh/id_rsa (RSA)
```

7. The SSH keys on GitHub should match the same keys on your computer.

> Warning: If you see an SSH key you're not familiar with on GitHub, delete it immediately and contact GitHub Support for further help. An unidentified public key may indicate a possible security concern.