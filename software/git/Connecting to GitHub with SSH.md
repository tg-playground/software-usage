# Connecting to GitHub with SSH

## Checking for existing SSH keys

Before you generate an SSH key, you can check to see if you have any existing SSH keys.

1. Open Git Bash.

2. Enter `ls -al ~/.ssh` to see if existing SSH keys are present:

   ```shell
   $ ls -al ~/.ssh
   # Lists the files in your .ssh directory, if they exist
   ```

3. Check the directory listing to see if you already have a public SSH key. By default, the filenames of the public keys are one of the following:

   - *id_rsa.pub*
   - *id_ecdsa.pub*
   - *id_ed25519.pub*

If you don't have an existing public and private key pair, or don't wish to use any that are available to connect to GitHub, then **generate a new SSH key**.

If you see an existing public and private key pair listed (for example *id_rsa.pub* and *id_rsa*) that you would like to use to connect to GitHub, you can **add your SSH key to the ssh-agent**.

**Tip:** If you receive an error that *~/.ssh* doesn't exist, don't worry! We'll create it when we **generate a new SSH key**.

## Generating a new SSH key and adding it to the ssh-agent

After you've checked for existing SSH keys, you can generate a new SSH key to use for authentication, then add it to the ssh-agent.

### Generating a new SSH key

1. Open Git Bash.

2. Paste the text below, substituting in your GitHub email address.

   ```shell
   $ ssh-keygen -t ed25519 -C "your_email@example.com"
   ```

   **Note:** If you are using a legacy system that doesn't support the Ed25519 algorithm, use:

   ```shell
   $ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
   ```

   This creates a new ssh key, using the provided email as a label.

   ```shell
   > Generating public/private ed25519 key pair.
   ```

3. When you're prompted to "Enter a file in which to save the key," press Enter. This accepts the default file location.

   ```shell
   > Enter a file in which to save the key (/c/Users/you/.ssh/id_ed25519):[Press enter]
   ```

4. At the prompt, type a secure passphrase. For more information, see ["Working with SSH key passphrases"](https://docs.github.com/en/articles/working-with-ssh-key-passphrases).

   ```shell
   > Enter passphrase (empty for no passphrase): [Type a passphrase]
   > Enter same passphrase again: [Type passphrase again]
   ```

### Working with SSH key passphrases

You can secure your SSH keys and configure an authentication agent so that you won't have to reenter your passphrase every time you use your SSH keys.

### Adding your SSH key to the ssh-agent

Before adding a new SSH key to the ssh-agent to manage your keys, you should have checked for existing SSH keys and generated a new SSH key.

If you have GitHub Desktop installed, you can use it to clone repositories and not deal with SSH keys.

1. Ensure the ssh-agent is running. You can use the "Auto-launching the ssh-agent" instructions in "[Working with SSH key passphrases](https://docs.github.com/en/articles/working-with-ssh-key-passphrases)", or start it manually:

   ```shell
   # start the ssh-agent in the background
   $ eval `ssh-agent -s`
   > Agent pid 59566
   ```

2. Add your SSH private key to the ssh-agent. If you created your key with a different name, or if you are adding an existing key that has a different name, replace *id_ed25519* in the command with the name of your private key file.

   ```shell
   $ ssh-add ~/.ssh/id_ed25519
   ```

### Auto-launching ssh-agent on Git for Windows

You can run `ssh-agent` automatically when you open bash or Git shell. Copy the following lines and paste them into your `~/.profile` or `~/.bashrc` file in Git shell:

```
vim ~/.profile
```

```bash
env=~/.ssh/agent.env

agent_load_env () { test -f "$env" && . "$env" >| /dev/null ; }

agent_start () {
    (umask 077; ssh-agent >| "$env")
    . "$env" >| /dev/null ; }

agent_load_env

# agent_run_state: 0=agent running w/ key; 1=agent w/o key; 2= agent not running
agent_run_state=$(ssh-add -l >| /dev/null 2>&1; echo $?)

if [ ! "$SSH_AUTH_SOCK" ] || [ $agent_run_state = 2 ]; then
    agent_start
    ssh-add
elif [ "$SSH_AUTH_SOCK" ] && [ $agent_run_state = 1 ]; then
    ssh-add
fi

unset env
```

If your private key is not stored in one of the default locations (like `~/.ssh/id_rsa`), you'll need to tell your SSH authentication agent where to find it. To add your key to ssh-agent, type `ssh-add ~/path/to/my_key`.

Now, when you first run Git Bash, you are prompted for your passphrase:

```shell
> Initializing new SSH agent...
> succeeded
> Enter passphrase for /c/Users/you/.ssh/id_rsa:
> Identity added: /c/Users/you/.ssh/id_rsa (/c/Users/you/.ssh/id_rsa)
> Welcome to Git (version 1.6.0.2-preview20080923)
>
> Run 'git help git' to display the help index.
> Run 'git help ' to display help for specific commands.
```

The `ssh-agent` process will continue to run until you log out, shut down your computer, or kill the process. 


## Adding a new SSH key to your GitHub account

To configure your GitHub account to use your new (or existing) SSH key, you'll also need to add it to your GitHub account.

After adding a new SSH key to your GitHub account, you can reconfigure any local repositories to use SSH. For more information, see "[Switching remote URLs from HTTPS to SSH](https://docs.github.com/en/articles/changing-a-remote-s-url/#switching-remote-urls-from-https-to-ssh)."

### Switching remote URLs from HTTPS to SSH

1. Open Git Bash.

2. Change the current working directory to your local project.

3. List your existing remotes in order to get the name of the remote you want to change.

   ```shell
   $ git remote -v
   > origin  https://github.com/USERNAME/REPOSITORY.git (fetch)
   > origin  https://github.com/USERNAME/REPOSITORY.git (push)
   ```

4. Change your remote's URL from HTTPS to SSH with the `git remote set-url` command.

   ```shell
   $ git remote set-url origin git@github.com:USERNAME/REPOSITORY.git
   ```

5. Verify that the remote URL has changed.

   ```shell
   $ git remote -v
   # Verify new remote URL
   > origin  git@github.com:USERNAME/REPOSITORY.git (fetch)
   > origin  git@github.com:USERNAME/REPOSITORY.git (push)
   ```

### Adding a new SSH key to your GitHub account

1. Copy the SSH public key to your clipboard.

If your SSH public key file has a different name than the example code, modify the filename to match your current setup. When copying your key, don't add any newlines or whitespace.

```shell
$ clip < ~/.ssh/id_ed25519.pub
# Copies the contents of the id_ed25519.pub file to your clipboard
```

2. In the upper-right corner of any page, click your profile photo, then click **Settings**.
3. In the user settings sidebar, click **SSH and GPG keys**.
4. Click **New SSH key** or **Add SSH key**.
5. In the "Title" field, add a descriptive label for the new key. For example, if you're using a personal Mac, you might call this key "Personal MacBook Air".
6. Paste your key into the "Key" field.
7. Click **Add SSH key**.
8. If prompted, confirm your GitHub password.

## Testing your SSH connection

After you've set up your SSH key and added it to your GitHub account, you can test your connection.

1. Open Git Bash
2. Enter the following

```
$ ssh -T git@github.com
# Attempts to ssh to GitHub
```

You may see a warning like this:

```shell
> The authenticity of host 'github.com (IP ADDRESS)' can't be established.
> RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
> Are you sure you want to continue connecting (yes/no)?
```

3. Verify that the fingerprint in the message you see matches [GitHub's RSA public key fingerprint](https://docs.github.com/en/github/authenticating-to-github/githubs-ssh-key-fingerprints). If it does, then type `yes`:

```shell
> Hi username! You've successfully authenticated, but GitHub does not
> provide shell access.
```

4. Verify that the resulting message contains your username. If you receive a "permission denied" message, see ["Error: Permission denied (publickey)"](https://docs.github.com/en/articles/error-permission-denied-publickey).

## References

[Connecting to GitHub with SSH - GitHub Docs](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh)