# setup-ssh-keys
Notes/Documentation for setting up SSH keys on GitHub

## How To Setup a SSH Key on GitHub?

### Prerequisite:
 - You are using MacOS
 - You have "SSH" command available on command line

1. Check for existing SSH key on your local machine:
 - navigate to top level directory hierchy - `cd ~`
 - from there, go into - `cd .ssh`
 - all of your previosuly created SSH keys should live inside `.ssh` directory
 - if you see any files w/ names as `id_rsa` and `id_rsa.pub`, then you already have SSH key on your local machine, so you can move directly to step 3. Otherwise, follow step 2 to create an SSH key on your local machine

2. Create / Generate a new SSH key on your local machine
 - from top level directory hierachy, type - `ssh-keygen` to start creating a new SSH key
 - from there, 
 	- leave "Enter file in which to save the key" as is (/Users/[YOUR_USERNAME]/.ssh/id_rsa)
 	- skip through "Enter passphrase" by pressing enter
 - once you see a randomart image pop up on the terminal, that's it! Your SSH key has been generated
 - just to verify, go into the that `.ssh` directory and check if both `id_rsa` and `id_rsa.pub` files exist

3. Now, that you have SSH key generated, you need to let GitHub know about it, so it won't bother you for username and password on every clone or push to GitHub upstream
- log into your GitHub account
- go into "Settings" from top right dropdown of your profile
- select "SSH and GPG keys" from the "Personal settings" list on the left
- then, click on "New SSH key" button
- give a "Title" for the device you are setting SSH key for (i.e., "Personal Macbook Air")
- as for the value of "Key":
	- go back to the terminal and copy the public SSH key that you generated on step 2. From top level directory hierachy, type - `pbcopy < ~/.ssh/id_rsa.pub` (copies the public key to your clipboard) 
	- now, go back to GitHub and paste it the public key
- finally, click "Add SSH key"

4. Congrats! Now, every clone of a repository (through SSH) or a push of a new change should no longer require username or password to GitHub. GitHub knows your working device as a trusted source and created a tunnel for communication between your local machine and the GitHub server.

