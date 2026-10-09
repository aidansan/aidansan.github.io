---
title: Generating and Adding an SSH Key to GitHub
layout: blog_post
include_math: false
citations: ["GitHub Docs: Connecting to GitHub with SSH, https://docs.github.com/en/authentication/connecting-to-github-with-ssh/"]
---
## Generating a new SSH key

You can generate a new SSH key on your local machine. After you generate the key, you can add the public key to your account on GitHub.com to enable authentication for Git operations over SSH.

1. On Mac/Linux, open terminal. On Windows, open [Git Bash](https://git-scm.com/install/windows).

2. Paste the text below, replacing the email used in the example with your GitHub email address.

   ```shell
   ssh-keygen -t ed25519 -C "your_email@example.com"
   ```

   This creates a new SSH key, using the provided email as a label.

   ```shell
   > Generating public/private ed25519 key pair.
   ```

   When you're prompted to "Enter a file in which to save the key", type in `~/.ssh/id_ed25519_data120` and then press **Enter**.

   ```shell
   > Enter a file in which to save the key (/home/YOU/.ssh/id_ALGORITHM): ~/.ssh/id_ed25519_data120[Press enter]
   ```

3. At the prompt for passphrase, press Enter. (For no passphrase)

   ```shell
   > Enter passphrase (empty for no passphrase): [Type a passphrase]
   > Enter same passphrase again: [Type passphrase again]
   ```

## Adding a new SSH key to your account

1. Copy the SSH public key to your clipboard.

   ```shell
   $ cat ~/.ssh/id_ed25519_data120.pub
   # Then select and copy the contents of the id_ed25519.pub file
   # displayed in the terminal to your clipboard
   ```

   > **Tip**
   >
   > Alternatively, you can locate the hidden `.ssh` folder, open the file in your favorite text editor, and copy it to your clipboard.

2. In the upper-right corner of any page on GitHub, click your profile picture, then click **Settings**.

3. In the "Access" section of the sidebar, click **SSH and GPG keys**.

4. Click **New SSH key** or **Add SSH key**.

5. In the "Title" field, add a descriptive label for the new key. For example, if you're using a personal laptop, you might call this key "Personal laptop DATA120".

6. Select authentication key.

7. In the "Key" field, paste your public key.

8. Click **Add SSH key**.

9. If prompted, confirm access to your account on GitHub. For more information, see [Sudo mode](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/sudo-mode).
