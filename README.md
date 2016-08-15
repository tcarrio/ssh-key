Table of Contents:

1. [Checking for existings keys](#checking-for-existing-ssh-keys)
2. [Generating a new SSH key](#generating-a-new-ssh-key)
3. [Adding your SSH key to the ssh-agent](#adding-your-ssh-key-to-the-ssh-agent)

Checking for existing SSH keys
------------------------------

Before you generate an SSH key, you can check to see if you have any existing SSH keys.

1. Open Git Bash.

2. Enter `ls -al ~/.ssh` to see if existing SSH keys are present:

  ```bash
  ls -al ~/.ssh
  # Lists the files in your .ssh directory, if they exist
  ```

3. Check the directory listing to see if you already have a public SSH key.

By default, the filenames of the public keys are one of the following:

* id_dsa.pub
* id_ecdsa.pub
* id_ed25519.pub
* id_rsa.pub

If you don't have an existing public and private key pair, or don't wish to use any that are available to connect to GitHub, then generate a new SSH key.
If you see an existing public and private key pair listed (for example id_rsa.pub and id_rsa) that you would like to use to connect to GitHub, you can add your SSH key to the ssh-agent.


After you've checked for existing SSH keys, you can generate a new SSH key to use for authentication, then add it to the ssh-agent.

Generating a new SSH key
-------------------------

1. Open Terminal.

2. Paste the text below, substituting in your GitHub email address.

  ```bash
  ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
  # Creates a new ssh key, using the provided email as a label
  Generating public/private rsa key pair.
  ```

3. When you're prompted to "Enter a file in which to save the key," press Enter. This accepts the default file location.

  ```bash
  Enter a file in which to save the key (/Users/you/.ssh/id_rsa): [Press enter]
  ```

4. At the prompt, type a secure passphrase. For more information, see "Working with SSH key passphrases".

  ```bash
  Enter passphrase (empty for no passphrase): [Type a passphrase]
  Enter same passphrase again: [Type passphrase again]
  ```

Adding your SSH key to the ssh-agent
------------------------------------

Before adding a new SSH key to the ssh-agent, you should have checked for existing SSH keys and generated a new SSH key.

1. Ensure ssh-agent is enabled:

  ```bash
  # start the ssh-agent in the background
  eval "$(ssh-agent -s)"
  Agent pid 59566
  ```

2. Add your SSH key to the ssh-agent. If you used an existing SSH key rather than generating a new SSH key, you'll need to replace id_rsa in the command with the name of your existing private key file.

  ```bash
  $ ssh-add ~/.ssh/id_rsa
  ```
  
  References: [Github: Generating an SSH key](https://help.github.com/articles/generating-an-ssh-key/)
