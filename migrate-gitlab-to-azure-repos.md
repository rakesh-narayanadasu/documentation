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

7. Update Remote URLs in Local Clones (Because it contains both GitLab and Azure repo url)
This command changes/updates the URL of an existing remote
```sh
git remote set-url origin <azure-repo-url>
```
This command adds a new remote named azure with the URL specified 
```sh
git remote add azure <azure-repo-url>
```

8. Check the remote URL
```sh
git remote -v
```

9. Pull the latest code
```sh
git pull origin <branch-name>
```	
Eg: git pull origin main

9. Now do changes to the code and push to Azure repos
```sh
git add .
git commit -m "Your commit message"
git push origin <branch-name>
```
