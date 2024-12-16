
## Create new user
1. Create the dev User
You can create the user dev by running the following command in the terminal:
```sh
sudo adduser dev
```
2. Ensure the User Does Not Have sudo Privileges
By default, the user dev will not have sudo privileges unless you explicitly add them to the sudo or admin group. So you can ensure that the user is not in the sudo group by running the following:
```sh
sudo deluser dev sudo
```
3. Allow the dev User to Access Root-Level Packages
Check permissions for directories like /usr, /lib, and /bin:
```sh
ls -ld /usr /lib /bin
```
The output should show that these directories have at least r-x (read and execute) permissions for others. If not, you can change the permissions:
```sh
sudo chmod o+rx /usr /lib /bin
```
4. Verifying Access
To verify that the dev user has access to these packages and can use them, you can log in as the dev user:
```sh
su - dev
```
Try running a command that should be accessible system-wide, such as checking installed packages:
```sh
which python3
```

## Configuring nvm at ```/usr/local/nvm``` to access multiple users in Ubuntu
Move ```nvm``` to ```/usr/local/nvm```
If you prefer not to reinstall ```nvm``` from scratch, you can move the existing ```nvm``` installation from ```/home/rakesh/.nvm``` to ```/usr/local/nvm``` and update the necessary configuration files.
1. Move ```nvm``` Directory to ```/usr/local/nvm```
```sh
sudo mv /home/rakesh/.nvm /usr/local/nvm
```
2. Update Configuration Files
Update the global shell configuration file (like ```/etc/bash.bashrc``` or ```/etc/zsh/zshrc```) to point to ```/usr/local/nvm```:
```sh
sudo nano /etc/bash.bashrc  # or /etc/zsh/zshrc for zsh
```
Add the following lines:
```sh
export NVM_DIR="/usr/local/nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```
3. Adjust Permissions
Make sure that the ```dev``` user(non-root) has the proper permissions to access ```/usr/local/nvm```:
4. Verify
After this, verify that ```nvm``` and ```node``` are accessible from any user:
```sh
node -v
```
5. Edit ```.bashrc``` file
```sh
nano ~/.bashrc
```
```sh
#python3.11
alias python3='/usr/local/bin/python3.11'
#alias node='/usr/local/nvm/versions/node/v18.20.5/bin/node'
export NODE_HOME='/usr/local/nvm/versions/node/v18.20.5'
export NPM_HOME='$NODE_HOME'
export PATH="$NODE_HOME/bin:$PATH"
```
7. Refresh ```.bashrc```
```sh
source ~/.bashrc
```

## Configure docker to access multiple users in Ubuntu
1. Create the docker group (if it doesn't already exist): In most systems, the docker group is created automatically during Docker installation. However, if it doesn't exist, you can create it manually:
```sh
sudo groupadd docker
```
2. Add the user (dev) to the docker group: Add the dev user to the docker group using the following command:
```sh
sudo usermod -aG docker dev # dev is non-root user
```
3. Log out and log back in: After adding the user to the Docker group, the user needs to log out and log back in for the group changes to take effect. Alternatively, you can run the following command to refresh the group membership without logging out:
```sh
newgrp docker
```
