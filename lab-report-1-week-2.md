# Installing VScode

In order to download vscode, go to [this website](https://code.visualstudio.com/download). 

After downloading, you should see this image:
![Image](VSCodeScreenshot.png)
From there you can start coding. 

# Remotely Connecting

To connect to any server using ssh you must type in your command line `ssh username@hostname`. For this course, you would type `ssh cs15lsp22---@ieng6.ucsd.edu`, and then input your password. This is what it should look like when connected:
![Image](remoteConnectionScreenshot.png)

The password input is tedious but there is a shortcut we will go over later. 

# Trying Some Commands
Some of the most useful commands are:
* cat \_file\_ (prints content of a file)
* cd \_directory\_ (allows you to change directory)
* ls \_optional directory\_ (allows you to list content of current dir or specified)
    * Useful command is ls -alF, it displays **a**ll files, prints them in **l**ong form, and **F**ormats them.
* cp \_source\_ \_destination\_ (copies a file to specified destination. Using -r you can copy entire directories.)
* rm \_file to remove\_ (removes specifid file)
    * if you want to remove an empty directory, include -r
    * if you want to remove a nonempty directory, include -rf

# Moving Files with `SCP`
