# Testing out Github Actions

This purposefully small project, which consists basically of just 2 files (main and main_test.py), is meant to demonstrate a possible and frequently used workflow of Github Actions. 

### Branch Protection

- after pushing the code to Github, i protect the main branch so that no one is able to push directly to main/master branch (except for myself in this example).\
Instead you would have to create a pull request, if you want to contribute. This is considered best practice, especially if you are working in a team with multiple people. So you'd make sure that no one can accidently push to the main branch, which has to be always fully functioning, thats why the code (of your feature branch) first has to pass all the tests, then you want to have your pull request approved, and finally you are able to merge it into main.
- Watch the branch protection rules in github. Go to: Settings -> Branches
- Add a protection rule and make sure the appropriate checkmarks are set for the main branch (in my case: require a pull request before merging and require approvals, require status checks to pass before merging and require branches to be up to date before merging -> save changes)

### Creating the workflow

Now i ll try to demonstrate what happens if you submit a pull request and merge onto the main branch:
- first create '.github/workflows' folder in the root folder
- then create a .yml file (in which you define all the scripts, commands,etc that you want to be executed)
- lets call it sth descriptive like: "flask_test.yml"..
- ..for detailed information about all options of that yml workflow file visit:\
<b>https:://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows</b>

- Note: in VSCode you can utilize the extension "GitHub Actions" (it'll connect to Github actions and hence it can show you the status of any of your actions that run)
- make a git add/commit & push directly to the main branch (as said: typically you shouldnt be able to do this but since you are the admin you can) in order to have the newly created yml workflow file added

###  Testing the workflow: 

- first make sure you are up to date with the main branch 
> git pull origin main
- then create a new branch for the change
> git checkout -b change
- make a simple change (like adding/removing a comment somewhere in the code) 
- push the new branch with the changes to github
> git push origin change 
- in Github open / create the pull request\
=> and it should automatically run the tests.\
=> click the "details" button on the right and watch the runners working on the steps you defined in the yml file\
=> If they were successful you should get a green checkmark and you ll be able to submit. 
