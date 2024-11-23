# Migrate from GitLab to Azure Repos
1. Create a new repository in Azure with a  similar GitLab project name

2. Clone GitLab repository locally using the command
```sh
git clone --mirror <url-of-gitlab-repository>
```

3. Change to the project directory
```sh
cd <repository-name>
```

4. Add the new Azure repository as a remote repository
```sh
git remote add azure <azure-repo-url>
```
> Note: need to add azure repo url. "azure" is the remote name/label assigned to identify Azure repos

5. Push the local repository to Azure repos using below commands
```sh
git push --all azure
git push --tags azure
```
or you can use `--mirror` that pushes all branches
```sh
git push --mirror azure
```
6. Verify the Azure repository through console

## For Developers

1. Clone the Azure project repository
```sh
git clone <azure-repo-url>
```

2. Check the remote URL
```sh
git remote -v
```
or you can add remote URL. This command adds a new remote with the URL specified 
```sh
git remote add origin <azure-repo-url>
```
or set the URL using
```sh
git remote set-url origin <azure-repo-url>
```

4. Now do changes to the code and push to Azure repos
```sh
git add .
git commit -m "Your commit message"
git push origin <branch-name>
```

5. Pull the latest code
```sh
git pull origin <branch-name>
```	
Eg: git pull origin main