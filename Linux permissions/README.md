# File permissions in Linux

## Project description
[Describe what you accomplish through Linux commands.]
## Checking file and directory details
In order to check the permissions of a file or directory in linux we must first list them using the `ls` command and also use the argument `l`, this argument will list the contents of the actual directory with their respective permissions. Finally to also list hidden files we append the argument `a`. We will end up typing the next command: 
`ls -la`

Here we have the output of such command on the directory `~/projects`

![code output](https://i.imgur.com/3TjmtOd.png)

## Permissions string description

From previous section command output I picked the hidden file `.project_x.txt` to explain its 10-character string describing its permissions:

![](https://i.imgur.com/4or1Rhn.png)

1. `-` This character tells if this output is describing a directory or a file, the two possible options are `d` for directories or `-` for a file, in this case we are refering to a file.
   
2. `r` This character tells the `user` permisions to read the file, the two possible options are `r` allowing the `user` to read or `-` not allowing the user to read.
   
3. `w` This character tells the `user` permisions to write the file, the two possible options are `w` allowing the `user` to write or `-` not allowing the user to write.

4. `-` This character tells the `user` permisions to execute the file in case it can be executed, the two possible options are `x` allowing the `user` to execute or `-` not allowing the user to execute.

5. `-` This character tells the `group` permisions to read the file, the two possible options are `r` allowing the `group` to read or `-` not allowing the group to read.
   
6. `w` This character tells the `group` permisions to write the file, the two possible options are `w` allowing the `group` to write or `-` not allowing the group to write.

7. `-` This character tells the `group` permisions to execute the file in case it can be executed, the two possible options are `x` allowing the `group` to execute or `-` not allowing the group to execute.
   
8. `-` This character tells `other` permisions to read the file, the two possible options are `r` allowing `other` to read or `-` not allowing other to read.
   
9. `-` This character tells `other` permisions to write the file, the two possible options are `w` allowing `other` to write or `-` not allowing other to write.

10. `-` This character tells `other` permisions to execute the file in case it can be executed, the two possible options are `x` allowing `other` to execute or `-` not allowing other to execute.

> NOTE: `other` refer to other users that have access to the system but are not the `user` and are not included in the `user` group. 


## Changing file permissions

The organization doesn't allow `other` to have write permissions to any file in the system, we can see when we checked file permissions on the `~/projects` directory that the file `project_k.txt` is not complying with this policy. We need to change this permission, in order to do it we use the command `chmod` that will need two arguments.

First argument will be the new permissions to be set or modified, in this case we are removing write permission to `other`, we use `o` to refer to `other`, then `-` to remove permissions and finally `w` to refer to the write permission we are removing. 

The second argument will be the file we are modifying, ending up with the command `chmod o-w project_k.txt`. 

## Changing file permissions on a hidden file

Previously we used the hidden file in the `~/projects` folder, this file was hidden because it needed to be archived, as it is an archived file it shouldn't have write permission, only read permission for `user` and `group`. We need to change this as right now it has write permission for both `user` and `group` and is missing read permission for `group`.

In order to do this we will use `chmod` command as done in previous section, again two arguments will be used: `chmod u=r,g=r .project_x.txt`.

This time the first argument is split in two parts separated by a comma, this is because we need to set more than a different permission at once, here I used the `=` operator to set all permissions I wanted with a single instruction, in this case only read permission was needed for both `user` and `group`, that is why only `r` was specified after `=`. 

In this case we are handling a hidden file, the second argument of the command specifies the file we need to modify and in this case we must add a dot before the name of the file to make sure we refer to the hidden file, the name of the file should look as `.project_x.txt`.

### Changing directory permissions

[Add content here.]

### Summary
[Add content here.]