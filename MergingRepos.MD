# Merging github repos into a new repo
Based on https://stackoverflow.com/a/52933095 and https://gist.github.com/ajaegers/2a8d8cbf51e49bcb17d5

1. On github, [fork](https://help.github.com/en/github/getting-started-with-github/fork-a-repo) any repositories of interest owned by other people
2. [Create a new repository](https://help.github.com/en/github/creating-cloning-and-archiving-repositories/creating-a-new-repository) on Github, ie one named Combined. Don't include a README or LICENSE, these will likely throw merge warnings later.
3. Download the new repo:
```
git clone https://github.com/BraunMichael/Combined.git
cd Combined
```
4. Add a remote repository of interest that you have forked into your own github, ie one named externalRepo:
```
git remote add externalRepo https://github.com/BraunMichael/externalRepo.git
git remote -v
```
5. Fetch for all the files from the old repo so a new branch gets created:
```
git fetch externalRepo
git branch -a
```
6. In the master branch, do a merge to combine the old repo with the newly created one:
```
git merge remotes/externalRepo/master --allow-unrelated-histories
```
7. Remove reference to the externalRepo remote:
```
git remote rm externalRepo
```
8. (Optional) If you need to move files with git and keep file history, ie you have this structure:
   ```
     project-folder/
         .git
         wp-admin/
         wp-content/
         wp-includes/
        .htaccess
        ...
   ```
   But you want this structure:
   ```
     project-folder/
         .git
         public
              wp-admin/
              wp-content/
              wp-includes/
             .htaccess
             ...
   ```

   - Be sure you don't have files uncommitted, if not commit them before next step.

    `git status`


   - In project-directory create `public` subfolder

    `mkdir public`

   - Move files with `git mv` except `public` subfolder to avoid errors

     `for file in $(ls | grep -v 'public'); do git mv $file public; done;`

   - (Optional) Move specific files like .htaccess etc...

     `git mv .htaccess public/`
     
   - Commit changes

     `git commit -m 'Moved files to public/'`
9. Push everything to Github:
```
git push origin master
```
