### Lab 5: intro to GitHub

We will be following the tutorial here: https://product.hubspot.com/blog/git-and-github-tutorial-for-beginners. This tutorial is very good, and there is no sense in recreating the wheel. Instead, I will just be asking for a few screenshots along the way. 

One major note here, do all of this through Opuntia instead of your computer. This also means you do not have to install git--it is already installed there. Another side effect of this is that you will have to continually type your GitHub username and password--this is related to permissions and security on Ron.

A final note before beginning. Password support is deprecated using `git`. Please follow these instructions to produce a token to use in place of a password:

```
Log into GitHub with your username and password
Navigate to your GitHub account settings
Scroll down and click ‘Developer settings’ in the list of links to the left
Click the Personal access tokens link
Click the ‘Generate new token’ button
Add a ‘Note’ to describe the tokens usage
Set an expiration date for the GitHub personal access token
Select the appropriate authentication scope
Click the ‘Generate token’ button
```

1. What is the full path to the location of git on Opuntia?
2. Post a screenshot of your newly minted GitHub account (if you already had one for some other purpose that is obviously fine, but still post a screenshot).
3. Post a screenshot of your newly initiated repo (the first one via the command line).
4. Post a screenshot of your first commit.
5. Post a screenshot of your newly initiated repo (the second one you did via the GitHub website). Hint: the green new repo button seems to be in the top left of the main GitHub page now.

Step 5 note: The command `git checkout -b <my branch name>` can be used to either 1) create a new branch (as you used it) or 2) to switch to that branch and examine it via `git checkout <my branch name>`.

Step 6 hint: you can copy the code you need via the button to the right of **..or push an existing repository from the command line**

Before Step 7: Add a new file to the second branch (the one you manually created) before you push your new branch. You will have to then `add` and `commit` this file before pushing it. Review the stuff you've already done to remember how to do this!

6. Post a screenshot of your submitted Pull Request.
7. Post a screenshot of your git log.
