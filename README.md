# HGV Learning Git
**Git** is a very widely used Software that when combined with **GitHub** is one of, if not the most used Software in Software Development. This Guide will explain how to use both Git and GitHub in the context of the HGV Project and its GitHub Organization and will be **split into 2 parts**. The 1st half will explain what Git and GitHub are and why we use it while the 2nd half will just guide you on how to use these tools with a step by step guide on how to use the basic function of Git using either the Terminal or VScode.

## What is Git?
If you ever used Google Docs, on the top right you can find a clock icon which will open version history. This feature lets you go back to older versions as well see who wrote what parts. **Git is this version history in Google Docs** but for code and other files. The most basic use of Git is to Commit Files to a Repository (Which is just a place that stores changes made to the file), then whenever you have to go back to a change you can revert to it or just copy what you need. This allows protection on code making it harder to lose code as you can always go back and also branch off your code into different features and help focus your code. Git is pre-installed on almost every computer and is used in every major tech company. The only major downside of Git is sharing the code as it’s only stored on your machine but that's where GitHub comes in.
### What is GitHub?
GitHub is an online service which is the **equivalent of Google Drive for Code**. Its the location where many programmers upload their code and projects to store and share with other people. It works by uploading your local git project onto the web and allows other users to download it, edit it, then reupload it for you to add to your code. It also has a feature called a pull request which allows people to write code and submit it without editing the main file until someone approves it. There are plenty of tools and features in these 2 programs that I can't cover here but this guide will give you the basics of what you need to know to start using Git for HGV.

## HGV Workflow
For the HGV, all the code is stored onto a GitHub Organization which is just a way to store repositories that are related to one overall project. Currently there are **4 main repositories** that stored Arduino Code, Website Code, Middleware Config, and any Code used for Debugging. Each one should be worked on the same way with the same workflow. In each of the repositories, the code is split into 3 Types of Branches.
### Feature Branch
The 1st Type of branch is **Feature Branch**. These branches aren't already made but are created by the **programmer when testing or creating a new feature.** these branches will have many issues and bugs to begin with but when the program is finish and working, you can do a pull request and merge all the changes made into the 2nd Branch, Dev Branch.
### Dev Branch
The **Dev Branch** is the 2nd branch and is where most of the development takes place. all Feature Branches start from this Branch before splitting off and then later merging back with it. The reason we don't just work from the Dev Branch is so that 2 people are able to work on the same code and not create conflicts with each other. This means you **should almost never directly edit the Dev Branch** but make a Feature Branch to merge into it instead. when a major amount of work has been done to Dev branch, and it all is working without error it can be merged into the final branch which is main branch.
### Main Branch
**Main Branch** is the final branch that stores 100% working code and shouldn't have any half finish parts in it. The idea is that if we want to test code with a new set of hardware, we will use code from main branch as we know it will work without any error. The only thing that can edit main is by merging Dev Branch into it but unlike dev where you can make any merge whenever you finish working on your Feature Branch, merging into **Main requires someone to look over the code before letting the merge happen.**
## How to Use Git
First Before we Use Git, we need to download it and then download other GUI or Tools we want to use. In this Guide we will be using just **Base Git** and then **VScode**, but you are free to use any Git GUI you Like.
### Needed Software
#### Git
Is a Terminal Program that lets you use Git via the Terminal and should be auto installed on almost every PC. However, if you want to make sure you have it installed or up to date follow these steps based on your OS

To check if you already have Git on your system run this into your Terminal
``` bash
git --version
```
If you get a version number back that means it is installed. If it isn't then try to install it
##### How to Install
###### Windows
Install the Git setup here
https://git-scm.com/downloads/win
###### Mac
Uses this Mac guide and use what tool that works the best for you (if you don't know any of them just use the binary)
https://git-scm.com/downloads/mac
###### Ubuntu/Debian/REMS PC
work for Linux system that has the apt package installer Like Ubuntu or Debian
``` bash
sudo apt install git-all
```

#### VScode
A coding IDE that has inbuilt Git usage and can be used for both the writing of code and the use of Git.
##### How to Install
For every OS you can download it via the official website by clicking the big blue button for you OS
https://code.visualstudio.com/download
but for Linux there are a few extra step that you might have to take so I would suggest reading this if you plan to install this
https://code.visualstudio.com/docs/setup/linux#_install-vs-code-on-linux

## The Git & GitHub Tutorial
This tutorial will be split into 2 parts with each one having the same content but using the 2 different tools listed above. I would recommend looking at both of them to see which one you like to use the most or you can use a separate way not listed on tutorial if you wish.
### Basic Git
Here we will only be using a Terminal and a Browser to Access GitHub
1. To get started with the basic Git program, you start by opening a Terminal page and changing your directory to wherever you want to store your GitHub Projects. 
- For this tutorial we will presume you have a folder made in your home directory called "GitHub" made by running this command in Linux:
``` bash
mkdir GitHub
```
2. Then running this command to change your directory into that folder
``` bash
cd Github
```
- If you don't feel comfortable using these command you can swap to using a different tool or learning more by understand Basic Linux Terminal Commands, links found at the bottom of the guide

#### Downloading Files
3. To get started with this tutorial, we want to download the project folder found on the HGV GitHub page. to start we need to go onto GitHub in a browser and navigate to this link here:  
https://github.com/Heather-Glen-Village/HGV-Learning-Git

4. From the page you want to click on the **Big Green Code** button which will show a drop down with a link but make sure the **HTTPS option is selected** before copying it.
![Pasted image 20250323133233](https://github.com/user-attachments/assets/31014dba-0d82-4e10-90cc-cf234543805b)


5. With the link copied, go back to your Terminal and copy the command below. this will download all the code from GitHub onto your Computer 
```bash
git clone https://your.copy.link.here.com
```
(make sure you change your directory to the downloaded repository)
``` bash
cd <Name of Folder>
```
#### Swapping Branch
Currently we only have the main branch downloaded which would be fine if we want to use the code but if we want to edit the code, we will want to be on the Feature Branch.

6. Check all, already made branches on GitHub by running: 
```bash
git branch -a
```
- -a mean show all
This will output something like this:
``` bash
* main
  remotes/origin/dev
  remotes/origin/main
```
This shows all branch that are made, with the ones with remotes/ being ones from GitHub and the one with the * being the one we are currently using. 

7. To start working we want to create a a new branch where you will work on all your changes. This new branch would be based on the dev branch already on GitHub. for the Name of the Branch, it should normally be made for the feature you're working on but for this Tutorial your name will work fine. 
- To Create a Branch run this command with the <> replace with the name
```bash
git switch -c <Your-Branch-Name> origin/dev
```
- -c mean creates
- Your-Branch-Name is the name of the branch
-  origin/dev is the branch we are basing it off of.  

(you can also use this command to swap to any other local branch like main)
```bash
git switch main
```

8. Finally, before we can start working on your code you want to upload this new branch to GitHub for others to see/work on with different computers. This can be done by pushing your new branch onto the repository
```bash
git push -u origin <Your-Branch-Name>
```
- -u tells Git to Link the GitHub Branch with this one
- Origin tells it to put the Branch on GitHub

Now if you check the GitHub on the left side the page there is a button to swap Branches and your should now be listed.
#### Finally Coding
Now with all of this setup done you can get to coding or in this case making an edit to a test python file. In the Repo there is a python file called Practice.py. 

9. In this file there are Instructions for you to follow but basically you need to add something to this file that proves you made an edit to it. If you don't know any python that fine, just write a simple command such as:
```python
print("My-Name")
```
#### Saving and Uploading your Code
When you are done adding what you to the Python file, you save it but that doesn't save it to Git. 

10. For Git we need to check what files need to be save by running to show all un stage and stage file in Git.
```bash
git status
```

11. To add a file to be committed you want to run this command
```bash
git add <filename>
```
(you can also run this command to save a changed/new files)
```bash
git add .
```
12. Then to take these staged files and save them you want to run this command with a message explaining what changes you have made
```bash
git commit -m "<Change-Message-Goes-Here>"
```
13. This will save all change you made so far locally but we also want to update the code on GitHub and that can be done by running:
```bash
git push
```
#### Merging Branches Together
This step is only done when you are fully done using the branch you created due to the feature being completed. When a branch is done it can first be merge onto the dev branch and after a while, we have 100% clean working code, we merge dev into main.

14. To start this, go onto GitHub and the Branches Page. There should be a Notification saying there has been a recent push and asking if you want to make a pull request. You want to click that green pull request button to enter the pull request page
![Pasted image 20250323143545](https://github.com/user-attachments/assets/e190b8a8-78cb-4d41-9b04-a6cb704e1d08)

15. On this page you will document the changes you have made and tell GitHub to merge your branch into dev first. You can also fill out the labels and people you want to look at as well as the people that worked on the branch
![Pasted image 20250323143957](https://github.com/user-attachments/assets/4ec2e8a2-bd5f-4a9b-a982-afdbc356ee0c)

16. When your done filling it out you can click the create pull request and if nothing goes wrong, on the next page you can merge the request yourself.

17. After both branch have merge you can remove your old branch on GitHub by Clicking the Delete Branch Button on GitHub and running this command locally
```bash
git branch -d <Name-of-Branch>
```
- -d mean delete
(You can't be on the Branch you are delete so make sure to swap off it)

18. Later when more features have been added you will do the same thing from dev to main but their will have been a review from someone before being added to main.
#### Extra Things to Know
While not needed for this guide here a few extra commands you should know while working with Git
##### git pull & git fetch
Both of these commands do very similar stuff which is to update your local file with any changes made using a different device and were uploaded to GitHub. For example, if another co-op student downloaded your branch and made some edits you can run:
```bash
git fetch
```
To let Git check if any changes has been made and then 
```bash
git pull
```
To download any changed made as long as you don't have non saved files and they don't your conflict
##### Going back to Older Commits
There are a few ways to do this but the way I would recommend is first find the commit you wish to go back to on GitHub by clicking the commits button on the page

![Pasted image 20250323145311](https://github.com/user-attachments/assets/7f5a2a56-71a6-476e-aa31-f8fc64563edb)

From here there is a list of all commits made, and each have a hash related to them (They look like this 62c4319). When you find the commit, you want to go back to copy its hash then in the Terminal you can either make a new branch with that old code with this:
```bash
git checkout <hash>
git chechout -b <name>
```
- -b Create Branch
Or you can turn the current branch that you have back in time using this command 
```bash
git revert <hash>
```
This will most likely cause some merge conflict that you need to solve.
##### Merge Conflicts
- Happens when you try to do a git pull or when merging your branch into dev/main where the files have one line of code in one branch but another in a different branch. 
- Normally Git can handle most of these issues but sometimes they show up while working. You know when you’re dealing with a merge issue when the Terminal tells you a conflict has occurred. 
- When this happens, you want to go into this file and see where the issue is. Normally Git will add some Indicators to the file to help you Locate it. When you have found the issue, without any kind of code editor or extension you will just have to manually delete what you don’t want then when you are done just run a basic:
```bash
git add <name of file>
git commit -m "<Merge Comment>"
``` 
And the merge conflict will be solve. If you Accidentally caused a merge conflict and don't want to deal with it or know how do just remember you can run This command to undo the merge
```bash
git merge --abort 
```


### VS Code
With VS Code there are many things that now can be done with its GUI but there also plenty that will need the use of a terminal which we can use the In-built on to help with.
1. To get started with the VScode, you start by opening it and changing your directory change to wherever you want to storage your GitHub Projects. 
- For this Tutorial we presume you have a folder made in your home directory called "GitHub" made by pressing this to open file explorer and let you create a new folder
```
Ctrl+k+o
```
#### Downloading Files
2. To get started with this tutorial, we want to download the project folder found on the HGV GitHub page. to start we need to go onto GitHub in a browser and navigate to this link here:  
https://github.com/Heather-Glen-Village/HGV-Learning-Git

3. From the page you want to click on the **Big Green Code** button which will show a drop down with a link but make sure the **HTTPS option is selected** before copying it.
![Pasted image 20250323133233](https://github.com/user-attachments/assets/ce9c8854-832e-42bd-a853-6e2d4f4083c2)

4. With the link copied, go back to your VScode, open your In-Built Terminal via the Terminal Tab on the top or with this Key combo:
![Pasted image 20250323152516](https://github.com/user-attachments/assets/0466b50a-d38e-44b1-9bfc-17ea7cc5c8cf)
```
Ctrl+Shift+`
```
5.  Copy the command below. This will download all the code from GitHub onto your Computer 
```bash
git clone https://your.copy.link.here.com
```
#### Swapping Branch
Currently we only have the main branch downloaded which would be fine if we want to use the code but if we want to edit the code, we will want to be on the Feature Branch.

6. First to See all the Branches go to the **bottom left** of the app and click on the Branch Icon
![Pasted image 20250323152743](https://github.com/user-attachments/assets/7c4db68b-3497-4779-a19a-0ac540ed7c65)
- This shows all branches that are made with the ones with origin in first being ones from GitHub and the one being display next to the icon being the one we are on.
7. To start working we want to create a a new branch where you will work on all your changes. This new branch would be based on the dev branch already on GitHub. For the name of the Branch, it should normally be made for the feature your working on but for this Tutorial your name will work fine. 
![Pasted image 20250323152934](https://github.com/user-attachments/assets/eb820ca9-e900-4759-a84d-6a89ebec928a)
![Pasted image 20250323153126](https://github.com/user-attachments/assets/d072c18d-8a44-4774-839e-b464cd2cbbdc)
![Pasted image 20250323153121](https://github.com/user-attachments/assets/df05683e-a48a-4166-8730-bf5bd9bf57e5)

8. Finally, before we can start working on your code you want to upload this new branch to GitHub for others to see/you to work on with different computers. This can be done by going to the Git Tab on the left and pressing the publish branch button
![Pasted image 20250323153333](https://github.com/user-attachments/assets/b30156e3-b644-4a0a-8b1b-7e5a7b745dfd)

Now if you check the GitHub on the left side the page there is a button to swap Branches and your should now be listed.
#### Finally Coding
Now with all of this setup done you can get to coding or in this case making an edit to a test python file. In the Repo there is a python file called Practice.py. 

9. In this file there are Instructions for you to follow but basically you need to add something to this file that proves you made an edit to it. If you don't know any python that fine, just write a simple command such as:
```python
print("My-Name")
```

#### Saving and Uploading your Code
When you are done adding what you to the Python file, you save it but that doesn't save it to Git. 

10. For Git we need to check what files need to be save by running to show all un staged and staged file in Git which can be found listed on the Git Tab on the left
![Pasted image 20250323153537](https://github.com/user-attachments/assets/f309187e-40ce-4dd2-9f3b-5fa9766ed4d0)

11. To add a file to be save you want to click the stage changes button next to the file or the stage all changes button next to the changes tab

12. Then to take these staged files and save them you want to write a message explaining what changes you have made then press the Commit Button

![Pasted image 20250323153721](https://github.com/user-attachments/assets/89fe9305-7d8a-43d0-919f-a531e898f2bd)

13. This will save all change you made so far locally but we also want to update the code on GitHub and that can be done by pressing the Push Button where the Commit one used to be
![Pasted image 20250323153820](https://github.com/user-attachments/assets/0a90fcd0-1289-47ac-8d2c-492d40cd2fe8)
#### Merging Branches Together
This step is only done when you are fully done using the branch you created due to the feature being completed. When a branch is done it can first be merge onto the dev branch and after a while, we have 100% clean working code, we merge dev into main.

14. To start this, go onto GitHub and the Branches Page. There should be a Notification saying there has been a recent push and asking if you want to make a pull request. You want to click that green pull request button to enter the pull request page
![Pasted image 20250323143545](https://github.com/user-attachments/assets/e207e2ac-b195-4f4f-b2a5-1949579348fe)

15. On this page you will document the changes you have made and tell GitHub to merge your branch into dev first. You can also fill out the labels and people you want to look at as well as the people that worked on the branch
![Pasted image 20250323143957](https://github.com/user-attachments/assets/efc75358-99a6-4b8e-a6ee-cf78cfd70057)

16. When your done filling it out you can click the create pull request and if nothing goes wrong, on the next page you can merge the request yourself.

17.  After both branch have merge you can remove your old branch on GitHub by Clicking the Delete Branch Button on GitHub and running this command locally
```bash
git branch -d <Name-of-Branch>
```
(You can't be on the Branch you are delete so make sure to swap off it)

18. Later when more features have been added you will do the same thing from dev to main but their will have been a review from someone before being added to main.
#### Extra Things to Know
While not needed for this guide here a few extra commands you should know while working with Git
##### git pull & git fetch
Both of these commands do very similar stuff which is to update your local file with any changes made using a different device and were uploaded to GitHub. Luckily VS Code makes this really easy for us running git fetch every few minutes and replacing the Push/Commit Button with a Pull Button when a change has been made on GitHub. 
![Pasted image 20250323154334](https://github.com/user-attachments/assets/5daf16b9-1a01-4a0d-8125-6c45d685196b)
This will download any changed made as long as you don't have non saved files and they don't Your conflict. Sometimes the button won't show up after a change in that case run this command in the terminal to fix it
```bash
git fetch
```
##### Going back to Older Commits
There are a few ways to do this but the way I would recommend is first find the commit you wish to go back to on via looking at the graph found on VS code. you can click on different part to see that changes that were made
![Pasted image 20250323154555](https://github.com/user-attachments/assets/fa7b3643-4167-4bfb-b24b-5a2d18ed085c)
from here there is a list of all commits made and each have a hash related to them (They look like this 62c4319).  you can turn the current branch that you have back in time using this command 
```bash
git revert <hash>
```
This will most likely cause some Merge conflict that you need to solve.

You can also just click on the create new Branch button which will Make a new Branch with the code from that Commit
![Pasted image 20250323154724](https://github.com/user-attachments/assets/e55ee7e3-cf1d-47a6-92f5-ceead389ef00)
##### Merge Conflicts
- Happens when you try to do a git pull or when merging your branch into dev/main where the files have one line of code in one branch but another in a different branch. 
- Normally Git can handle most of these issues but sometimes they show up while working. You know when you’re dealing with a merge issue when the Terminal tells you a conflict has occurred. 
- When you have found the issue VS code will give you some option to pick from being keep the Current, Accept Incoming Change, Accept Both Changes. Pick whatever would work the best and when your done just stage the files and commit it back to GitHub
![Pasted image 20250323154921](https://github.com/user-attachments/assets/ba5570d2-b797-40b2-9451-637e64ec776f)
 If you Accidentally caused a merge conflict and don't want to deal with it or know how do just remember you can run This command to undo the merge
```bash
git merge --abort 
```

## Extra Sources
Unfortunately this guide can't cover everything and a written guide may not work for most people, Luckily there are plenty of video with guide like this to follow and learn from. Here a few I would recommend watching if you don't understand some of the basic or want to learn more about some parts like Merges or Branching.
### Basic of Git
- Fireship, Basic of Git and GitHub (12:18) https://www.youtube.com/watch?v=HkdAHXoRtos
- Kevin Stratvert, Git and GitHub for Beginners (46:18) https://www.youtube.com/watch?v=tRZGeaHPoaw
- VScode, Using Git with VScode (6:55) https://www.youtube.com/watch?v=i_23KUAEtUM

### Advanced Git
- Ihatetomatoes, How to Resolve Merge Conflicts (6:35) https://www.youtube.com/watch?v=xNVM5UxlFSA
- SuperSimpleDev, Git Branching and Merging (54:27) https://www.youtube.com/watch?v=Q1kHG842HoI
### Other
- SavvyNik, Basic Linux Terminal (7:33) https://www.youtube.com/watch?v=jgcXclSXnVo
