---
title: Generating and Adding an SSH Key to GitHub
layout: blog_post
include_math: false
citations: ["GitHub Docs: Connecting to GitHub with SSH, https://docs.github.com/en/authentication/connecting-to-github-with-ssh/"]
---
> **Note**
>
> GitHub improved security by dropping older, insecure key types on March 15, 2022.
>
> As of that date, DSA keys (`ssh-dss`) are no longer supported. You cannot add new DSA keys to your personal account on GitHub.
>
> RSA keys (`ssh-rsa`) with a `valid_after` before November 2, 2021 may continue to use any signature algorithm. RSA keys generated after that date must use a SHA-2 signature algorithm. Some older clients may need to be upgraded in order to use SHA-2 signatures.

## Generating a new SSH key

You can generate a new SSH key on your local machine. After you generate the key, you can add the public key to your account on GitHub.com to enable authentication for Git operations over SSH.

1. Open Terminal.

2. Paste the text below, replacing the email used in the example with your GitHub email address.

   ```shell
   ssh-keygen -t ed25519 -C "your_email@example.com"
   ```

   > **Note**
   >
   > If you are using a legacy system that doesn't support the Ed25519 algorithm, use:
   >
   > ```shell
   > ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
   > ```

   This creates a new SSH key, using the provided email as a label.

   ```shell
   > Generating public/private ALGORITHM key pair.
   ```

   When you're prompted to "Enter a file in which to save the key", you can press **Enter** to accept the default file location. Please note that if you created SSH keys previously, ssh-keygen may ask you to rewrite another key, in which case we recommend creating a custom-named SSH key. To do so, type the default file location and replace id_ALGORITHM with your custom key name.

   ```shell
   > Enter a file in which to save the key (/home/YOU/.ssh/id_ALGORITHM):[Press enter]
   ```

3. At the prompt, type a secure passphrase. For more information, see [Working with SSH key passphrases](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/working-with-ssh-key-passphrases).

   ```shell
   > Enter passphrase (empty for no passphrase): [Type a passphrase]
   > Enter same passphrase again: [Type passphrase again]
   ```

## Adding a new SSH key to your account

You can add an SSH key and use it for authentication, or commit signing, or both. If you want to use the same SSH key for both authentication and signing, you need to upload it twice.

After adding a new SSH authentication key to your account on GitHub.com, you can reconfigure any local repositories to use SSH. For more information, see [Managing remote repositories](https://docs.github.com/en/get-started/getting-started-with-git/managing-remote-repositories).

1. Copy the SSH public key to your clipboard.

   If your SSH public key file has a different name than the example code, modify the filename to match your current setup. When copying your key, don't add any newlines or whitespace.

   ```shell
   $ cat ~/.ssh/id_ed25519.pub
   # Then select and copy the contents of the id_ed25519.pub file
   # displayed in the terminal to your clipboard
   ```

   > **Tip**
   >
   > Alternatively, you can locate the hidden `.ssh` folder, open the file in your favorite text editor, and copy it to your clipboard.

2. In the upper-right corner of any page on GitHub, click your profile picture, then click **Settings**.

3. In the "Access" section of the sidebar, click **SSH and GPG keys**.

4. Click **New SSH key** or **Add SSH key**.

5. In the "Title" field, add a descriptive label for the new key. For example, if you're using a personal laptop, you might call this key "Personal laptop".

6. Select the type of key, either authentication or signing. For more information about commit signing, see [About commit signature verification](https://docs.github.com/en/authentication/managing-commit-signature-verification/about-commit-signature-verification).

7. In the "Key" field, paste your public key.

8. Click **Add SSH key**.

9. If prompted, confirm access to your account on GitHub. For more information, see [Sudo mode](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/sudo-mode).
