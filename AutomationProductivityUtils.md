# Automation and Productivity
## Ubuntu
1. Update vscode in linux
    If installed using the .deb file do the following [SO-Link](https://askubuntu.com/a/1016764)
    ```sh
    sudo apt-get update
    sudo apt-get install code 
    ```
2. Check if a package is installed.
    1. `dpkg` is used to manage packages in ubuntu
    2.  To check if `mysql` is installed use following command [SO-Link](https://stackoverflow.com/a/27614713/1652217)  
   
        ```sh
        dpkg --get-selections | grep mysql 
        ```
3. Use `lightdm` display manager instead of `gdm`. For example, gdm fails to detect multiple screens when waked up or if there is a power trip. To change do the following  
    ```sh
        sudo apt-get install lightdm
        sudo dpkg-reconfigure lightdm
    ``` 
4. To make a secretkey `pem` have correct permissions. Use
    ```sh
        chmod 400 <path-to-file.pem>
    ```

## VSCode
1. Exclude files of  subdirectory (`subdir1`) from 
   1. display add `/**/subdir1` to `files.exclude` in `File->Preference->Settings` . More info in [SO-Link](https://stackoverflow.com/a/33277809/1652217)
   2. watching add `/**/subdir1` to `files.watcherExclude` in `File->Preference->Settings`. More info in [VSC-Link](https://code.visualstudio.com/docs/setup/linux#_visual-studio-code-is-unable-to-watch-for-file-changes-in-this-large-workspace-error-enospc)
