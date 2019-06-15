### [HOME](https://krishna-waidande.github.io/)

##  To clone remote repository to our local folder
```git clone remote_repo_url```


For example :-
```git clone https://github.com/krishna-waidande/TestGit.git```

## To check branch name
```git branch```

## To add file to git.

```git add file name```

## To push data to master branch.

```git push```

## To push data to specific branch.

```git push origin branch_name```

## To check difference between remote master branch and our working branch.

```git diff```

## Gives all info about commits.

```git log```

## To clone a specific branch in local folder.

```git clone -b branch_name url_remote_master_branch```

For example : 


```git clone -b K_ADD_api https://github.com/krishna-waidande/krishagni-crm.git```

## Create new branch

```git checkout -b newbranchname```

## Delete branch
 
 From Local : ```git branch -d branch_name```


From remote : ```git push origin --delete branch_name```

## Rename your local branch.

If you are on the branch you want to rename

```git branch -m new-name```


If you are on a different branch:


```git branch -m old-name new-name```


## Delete the old-name remote branch and push the new-name local branch.


```git push origin :old-name new-name```


## Reset the upstream branch for the new-name local branch. Switch to the branch and then:


```git push origin -u new-name```

## Merging our code to master branch 
First come on  master branch 

```git merge```

after merge push that to master
git merge K_Add_Feature -m "merging file"
