- # Git 

### Basic Commands 

```shell
$ git init   			//initialize Local git repository

$ git add <file>		// Add file(s) to strage area
$ git add .				// Add all files

$ git status			// check status of working tree

$ git commit 			// commit changes 
$ git commit -m <message> -m <description> 
$ git commit -am <message>     //add and conmmit at the same time ,only works for modify files not for newly created files

$ git push 				// push to remote repository
$ git pull 				//pull lastest from remote repository
$ git clone 			//clone repository into a new directory

$ touch <file>			//create a file

$ git config --global user.name "Clairs-zx"
$ git config --global user.email "hdu_zhangxin@163.com"

$ git branch 			   // check branch
$ git checkout -b <branch>    //create a new branch and change to it
$ git merge <branch>
$ git branch -d <branch>      //delete a branch


// push a exsiting repository from the command line
$ git remote add origin <url>
$ git branch -M main  
$ git push -u origin main   //first 
$ git push                  //future

$ git diff <branch>        //check different between current branch and <branch>

$ git reset 			//Unstage
$ git reset HEAD~1     //Uncommit go back one commit furtuer

$ git log     			//check all commits
$ git reset <hash>		//go back to certain commit only unstage .
$ git reset --hard <hash> 
```

