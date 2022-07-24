# Git guide

Git is a version control system (VCS). VCS is the practice of tracking
and managing changes to the software code.

Benefit:

- Managing all the source code changes
- Tracking all code changes
- Enabling multiple developers to work on the same project simultaneously

## Sourcetree installation (recommendation for a simple UI)

- Step 1: Access [https://www.sourcetreeapp.com/](https://www.sourcetreeapp.com/)
- Step 2: Download source tree follow OS (Windows/macOS)
- Step 3: Install source tree
- Step 4: Restart the PC and use the console to check with command:
  > git version
- Step 5: On the **Remote** tab, need to **Add an account** with **Github** Host, **SSH** Preferred Protocol

## Github installation

- Step 1: Access [https://desktop.github.com/](https://desktop.github.com/)
- Step 2: Download github desktop follow OS (Windows/macOS)
- Step 3: Install github desktop
- Step 4: Restart the PC and use the console to check with command:
  > git version

## Git set up guides
 1. Generate SSH keys:
 * Step 1: Access [github](https://github.com/) and  with your github account
 * Step 2: On the header bar, right side click on the profile or dropdown button. Choose
  **Settings** and choose **SSH and GPC keys**
 * Step 3: Checking the existing ssh-key with command
   * Windows: Open with git-bash
     > ls -al ~/.ssh  
     \# Lists the files in your .ssh directory, if they exist
   * macOS:
     > ls -al ~/.ssh  
     \# Lists the files in your .ssh directory, if they exist
   * If there is existing ssh key forward on step 5.
* Step 4: If there is non-existing ssh key, create new ssh-key
  * Windows: Open with git-bash
    > ssh-keygen -t ed25519 -C "your_email@example.com"  
    
    **Note**: If you are using a legacy system that doesn't support the Ed25519
     algorithm, use:
    > ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
  * macOS:
    > ssh-keygen -t ed25519 -C "your_email@example.com"  
    
    **Note**: If you are using a legacy system that doesn't support the Ed25519
         algorithm, use:
    > ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
                                                                                                                                                                                     
    Command prompt steps:
    > Generating public/private ed25519 key pair.  
      Enter file in which to save the key (/c/Users/your_username/.ssh/id_ed25519):
       **[Press Enter]**  
      Enter passphrase (empty for no passphrase): **[Press Enter / Type a
      passphrase - Should enter for simple]**                                                                                                                                                                                                                                                                                                                                                                                                                                                          
      Enter same passphrase again: **[Press Enter / Type passphrase again]**
* Step 5: Start the ssh agent
  > eval "$(ssh-agent -s)"
* Step 6: Set up ssh config
  > open ~/.ssh/config  
  The file /Users/you/.ssh/config does not exist.
  
  **Note**: If the file doesn't exist, create the file.
  > touch ~/.ssh/config

  **Open** your ```~/.ssh/config``` 
  <pre>Host *  
      AddKeysToAgent yes  
      UseKeychain yes  
      IdentityFile ~/.ssh/id_ed25519</pre>
      
  **Note**: If you chose not to add a passphrase to your key, you should omit the ```UseKeychain``` line.
  
  **Note**: If you see an error like this
  > /Users/USER/.ssh/config: line 16: Bad configuration option: usekeychain
  
  add an additional config line to your Host * section:
  <pre>Host *
         IgnoreUnknown UseKeychain</pre>

* Step 7: Add ssh key into your machine agent
  > ssh-add -K ~/.ssh/id_ed25519
  
  **Note**: The ```-K``` option is Apple's standard version of ```ssh-add```, which stores
   the passphrase in your keychain for you when you add an SSH key to the ssh-agent. If 
   you chose not to add a passphrase to your key, run the command without the ```-K``` option. 
   
   If you don't have Apple's standard version installed, you may receive an error. For more 
   information on resolving this error, see ["Error: ssh-add: illegal option -- K."](https://docs.github.com/en/authentication/troubleshooting-ssh/error-ssh-add-illegal-option----k)

   In MacOS Monterey (12.0), the ```-K``` and ```-A``` flags are deprecated and have been replaced by 
   the ```--apple-use-keychain``` and ```--apple-load-keychain``` flags, respectively. 

* Step 8: Add public ssh key into your github account. Copy the content of file ```~/.ssh/id_ed25519.pub``` access [https://github.com/settings/keys](https://github.com/settings/keys) 
Click **New SSH Key**. Fill the title (e.g. 'Dell-PC-SSH-id_ed25519.pub').Fill the description with the content of .pub file.
* Step 9: Test the SSH success by the commit and push a new feature branch.

## Git definition by levels

 1. Repository
 2. Branch  
   2.1. The remote branch.
   2.2. The local branch.
   2.3. Naming branch.
 3. Commit
 4. Pull request

## Git command


## References

- [Atlassian](https://www.atlassian.com/git/tutorials/what-is-version-control)
- [Github Doc](https://docs.github.com/en)
 