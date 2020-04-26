# Misc
Miscellaneous Code, see https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet for a Github markdown cheatsheet 

# UbuntuSetup.txt
Script and information for setting up a new Ubuntu install and some desired programs. Use in combination with readme at https://github.com/BraunPenguin/InstanceSegmentation-Detectron2 for Instance Segmentation.

# ChromeDarkTheme
Simply Dark Chrome Theme

Add to chrome by downloading, going to chrome://extensions, enable developer mode, then drag and drop the .crx file into chrome. Instructions source: https://blog.hunter.io/how-to-install-a-chrome-extension-without-using-the-chrome-web-store-31902c780034

# Green With Envy
Nvidia graphics monitor and overclocking utility for Ubuntu from https://gitlab.com/leinardi/gwe. See UbuntuSetup.txt for installation/use info.

# Setting up Github with MATLAB
Combines information from MATLAB's docs (https://www.mathworks.com/help/matlab/matlab_prog/set-up-git-source-control.html) and this post (https://medium.com/rkttu/set-up-ssh-key-and-git-integration-in-windows-10-native-way-c9b94952dd2c)

### Install git
Download and install git from https://gitforwindows.org/ and choose the following options:
- Choose Notepadd++ as default editor (not required)
- Choose Git from the command line and also from 3rd-party software
- Choose Use the OpenSSL library
- Choose Checkout as-is, commit as-is to avoid converting line endings in files
- Choose Use Windows' default console window
- Enable file system caching and Git Credential Manager, but not symbolic links

### Install cygwin
Download and install cygwin from https://www.cygwin.com/

Start MATLAB as administrator, then in the MATLAB Command Window, type:
```edit(fullfile(matlabroot,"toolbox","local","librarypath.txt"))```

Add the Cygwin bin folder location to the end of librarypath.txt, for example ```C:\cygwin64\bin```.

### Setup ssh credentials
Set the $HOME environmental variable by:
- In the Start Search box, search for and select "advanced system settings".
- In the Advanced tab, click Environment Variables.
- In the User Variables section, click New. Create the HOME environment variable and specify its value. Choose C:\Users\<yourusername> unless you have good reason otherwise

Open a powershell window as admin

Enable the ssh-agent service to avoid asking for SSH key password everytime:
```
$SSHAgentSvc = Get-Service -Name ‘ssh-agent’
Set-Service -Name $SSHAgentSvc.Name -StartupType Automatic
Start-Service -Name $SSHAgentSvc.Name
```

Close powershell, and reopen as regular user (no longer admin)

Create a new ssh key via:
```
ssh-keygen
```
The default location should be ```$HOME/.ssh/id_rsa```, hit enter, if you don't want a password, continue hitting enter until the key is generated.

Add key pair to the ssh-agent service via:
```
ssh-add
```

Register the key on Github
In the powershell window still, copy the key to your clipboard via:
```
Get-Content -Path $HOME\.ssh\id_rsa.pub | Set-Clipboard
```
Then navigate to https://github.com/settings/ssh/new and paste the key in the key field.


Restart your computer and everything should be set. Information on how to use the MATLAB git interface here: https://www.mathworks.com/help/matlab/source-control.html
