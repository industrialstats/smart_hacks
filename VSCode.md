# VSCode
1. **Files and Folders**   
   Exclude files of  subdirectory (`subdir1`) from 
   1. display add `/**/subdir1` to `files.exclude` in `File->Preference->Settings` . More info in [SO-Link](https://stackoverflow.com/a/33277809/1652217)
   2. watching add `/**/subdir1` to `files.watcherExclude` in `File->Preference->Settings`. More info in [VSC-Link](https://code.visualstudio.com/docs/setup/linux#_visual-studio-code-is-unable-to-watch-for-file-changes-in-this-large-workspace-error-enospc)

2. **Remote Environment**
   1. To avoid disruption due to `ssh` timeout error,  set `terminal.integrated.inheritEnv` to `true`. More info in [git-link](https://github.com/microsoft/vscode-remote-release/issues/1721)
   
       