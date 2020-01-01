# Setup connection with Github with SSH key (Linux based)


## Configure ssh keys in local
- Check existing ssh keys in system
    ```
    ls -al ~/.ssh
    ```
- If key not present, generate using following steps
    ```
    ssh-keygen -t rsa -b 4096 -C "your_email@example.com"  # gerenate SSH key using emailid as label
    ```
- When prompted to provide file location to save, provide like below

    ```
    /home/username/.ssh/proj_id_rsa
    ```
- When prompted for passphrase, provide one & remember for future reference. You can update it later with below command.

  [https://help.github.com/en/github/authenticating-to-github/working-with-ssh-key-passphrases](https://help.github.com/en/github/authenticating-to-github/working-with-ssh-key-passphrases)
    ```
    ssh-keygen -p
    ```
- The above results 2 files, proj_id_rsa (private key) & proj_id_rsa.pub (public key)
- Add the new SSH key to the ssh-agent to manage your keys
    ```
    eval "$(ssh-agent -s)"  # Start the ssh-agent in the background.
    ssh-add ~/.ssh/proj_id_rsa  # Add SSH private key to the ssh-agent
    ```
- In github.com > Profile > SSH and GPG keys > New SSH key. Add title text & copy the content of public key file which starts like "ssh-rsa AAAAB3..." and ends with the used emailid.

## Clone repository in local
- When using SSH login, don’t use "https" url in github.com repository page to clone the repository. Instead, use "SSH" version.
    ```
    git clone git@github.com:USERNAME/REPOSITORY.git
    ```

- If repository already added with "https", reconfigure remote url to SSH version
    ```
    git remote -v  # check current url(s)
    git remote set-url origin git@github.com:USERNAME/REPOSITORY.git  # update url to SSH version
    git remote -v  # verify change
    ```

- Setup git local credentials
    ```
    git config --global user.email "you@example.com"
    git config --global user.name "github-username"

    ```
- Afterwards, git commands will not prompt for username/password & take credentials from ssh keys of the system
- References

    [https://help.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account](https://help.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account)
    [https://help.github.com/en/github/using-git/which-remote-url-should-i-use](https://help.github.com/en/github/using-git/which-remote-url-should-i-use)
    [https://www.ssh.com/ssh/passphrase](https://www.ssh.com/ssh/passphrase)
    [https://stackoverflow.com/questions/21095054/ssh-key-still-asking-for-password-and-passphrase](https://stackoverflow.com/questions/21095054/ssh-key-still-asking-for-password-and-passphrase)
