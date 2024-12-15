# Configuring nvm at ```/usr/local/nvm``` to access multiple users in Ubuntu
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
