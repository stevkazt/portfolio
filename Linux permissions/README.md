# File permissions in Linux

This activity aims to give an overview of my abilities with the Linux environment, most specifically managing permissions all around the system. It is worth adding this is just one of the abilities I have developed through years using Linux and some extra tricks I learned with the Google Cybersecurity certification.

## Project description

The general scenario for this activity describes the `~/projects` folder of `researcher` user that needs to have its permissions updated to comply with different security and company policies. Throughout the activity, I will be checking file and folder permissions in this directory and then modifying them, explaining the reason for these modifications and giving some extra details.

## Checking file and directory details

To check the permissions of a file or directory in Linux we must first list them using the `ls` command and also use the argument `l`, this argument will list the contents of the actual directory with their respective permissions. Finally, to also list hidden files we append the argument `a`. We will end up typing the next command: 
`ls -la`

Here we have the output of such a command on the directory `~/projects`

![code output](https://i.imgur.com/3TjmtOd.png)

## Permissions string description
From the previous section command output, I picked the hidden file `.project_x.txt` to explain its 10-character string describing its permissions:

![](https://i.imgur.com/4or1Rhn.png)

1. `-` This character tells if this output is describing a directory or a file, the two possible options are `d` for directories or `-` for a file, in this case, we are referring to a file.
   
2. `r` This character tells the `user` permissions to read the file, the two possible options are `r` allowing the `user` to read or `-` not allowing the user to read.
   
3. `w` This character tells the `user` permissions to write the file, the two possible options are `w` allowing the `user` to write or `-` not allowing the user to write.

4. `-` This character tells the `user` permissions to execute the file in case it can be executed, the two possible options are `x` allowing the `user` to execute or `-` not allowing the user to execute.

5. `-` This character tells the `group` permission to read the file, the two possible options are `r` allowing the `group` to read or `-` not allowing the group to read.
   
6. `w` This character tells the `group` permissions to write the file, the two possible options are `w` allowing the `group` to write or `-` not allowing the group to write.

7. `-` This character tells the `group` permission to execute the file in case it can be executed, the two possible options are `x` allowing the `group` to execute or `-` not allowing the group to execute.
   
8. `-` This character tells `other` permission to read the file, the two possible options are `r` allowing `other` to read or `-` not allowing others to read.
   
9. `-` This character tells `other` permissions to write the file, the two possible options are `w` allowing `other` to write or `-` not allowing other to write.

10. `-` This character tells `other` permissions to execute the file in case it can be executed, the two possible options are `x` allowing `other` to execute or `-` not allowing other to execute.

> NOTE: `other` refer to other users that have access to the system but are not the `user` and are not included in the `user` group. 


## Changing file permissions

![](https://i.imgur.com/MptBCc1.png)

The organization doesn't allow `other` to have write permissions to any file in the system, we can see when we checked file permissions on the `~/projects` directory that the file `project_k.txt` is not complying with this policy. We need to change this permission, to do it we use the command `chmod` which will need two arguments.

The first argument will be the new permissions to be set or modified, in this case, we are removing write permission to `other`, we use `o` to refer to `other`, then `-` to remove permissions and finally `w` to refer to the write permission we are removing. 

The second argument will be the file we are modifying, ending up with the command `chmod o-w project_k.txt`. 

## Changing file permissions on a hidden file

![](https://i.imgur.com/E2Nd2f3.png)

Previously we used the hidden file in the `~/projects` folder, this file was hidden because it needed to be archived, as it is an archived file it shouldn't have write permission, only read permission for `user` and `group`. We need to change this as right now it has write permission for both `user` and `group` and is missing read permission for `group`.

To do this we will use `chmod` command as done in the previous section, again two arguments will be used: `chmod u=r,g=r .project_x.txt`.

This time the first argument is split into two parts separated by a comma, this is because we need to set more than a different permission at once, here I used the `=` operator to set all permissions I wanted with a single instruction, in this case only read permission was needed for both `user` and `group`, that is why only `r` was specified after `=`. 

In this case, we are handling a hidden file, the second argument of the command specifies the file we need to modify and in this case, we must add a dot before the name of the file to make sure we refer to the hidden file, the name of the file should look as `.project_x.txt`.

### Changing directory permissions

![](https://i.imgur.com/S3NyzQn.png)

The `drafts` folder should only be accessible to the researcher who owns it as it is the only one who should be working on it.

In the case of folders we find that execute permission is used, this is because executing means opening such a directory, in this case, the group has permission to open it, and we are going to remove that permission.

As we have been doing before with files, the command remains the same, `chmod` with two arguments, This time we are going to remove `x` permission to the `group`, we would have this command: `chmod g-x drafts`.

### Summary

I have made changes to files and directories inside `~/projects` folder, including adding missing permissions, removing wrong permissions, also handling this permission to hidden files and directories. 

I have explained all these changes and the most used commands to do this, these being `chmod` to change these permissions and `ls`` to list files and folders to keep checking my changes.

These commands come together with arguments needed to achieve our objectives when managing permission or moving through Linux. 

`chmod` must always be accompanied by two arguments, the permissions to change, and the file or directory to work on. `ls` must list files and folders with no arguments but we needed a couple to list permissions and see hidden files.