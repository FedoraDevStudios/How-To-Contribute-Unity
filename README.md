# How-To-Contribute-Unity
Here is a step-by-step guide on how to contribute changes to the packages in the organization.

## Step 1
#### Requirements
##### Unity Version
Ensure you have the proper version of Unity installed via Unity Hub. The version can be found in the package's `package.json` file.

##### Git
Packages are built with Git and Git LFS for asset files. Pushing changes to the repo will require a similarly configured LFS. Additionally, this Unity [.gitignore](https://github.com/github/gitignore/blob/master/Unity.gitignore) file is required.

## Step 2
#### Get Local
##### Fork the Repo
Create a fork of the package on Github.

##### Create a Unity Project
I would recommend creating a new project specically for the modifications, however this can be pulled into an existing project as long as all dependencies are met. Ensure you follow any requirements present in the package's readme. Additionally, the project should have git initialized with the .gitignore linked above. As a final note, I always use .NET 4.x API Compatibility, so ensure this is the selected option in your project settings. This is not default.

##### Grab the Package Files
Once you have a project and all changes have been committed, add the remote to your forked repo. After the remote is added, you will need to add a subtree to the repo. This is probably the most important step to contributing. Run
```sh
git subtree add --prefix Assets/[package] [remote] upm
```

This will pull the package into your repo in the desired location. Note: if you get an error like
```
Working trees has modifications. Cannot add
```
then run
```sh
git reset --hard
```
I'm not entirely sure why this happens on a clean HEAD, but a hard reset seems to fix the issue.

> Important Note: Many packages will have dependencies that I don't have permission to redistribute. One big one is Odin Inspector. These dependencies must never be uploaded to a public repository and must be kept out of the package files.

## Step 3
#### Modify
##### Make Changes
This step is your favorite part. Make your changes. Note that the only changes that will ever make it to the public repo are things done within the package folder.

##### Commit
Just like any repo, commit your changes. The HEAD should be clean before continuing.

## Step 4
#### Push
Once your changes are finished, you can push the subtree to the forked remote. The command below will handle this.
```sh
git subtree push --prefix Assets/[package] [remote] upm
```

## Step 5
#### Pull
Submit a pull request back to the main repo. I will review from there. Keep in mind that I have high requirements to what I accept. Although I'm not an expert, I do expect the code to adhere to Uncle Bob's teachings of clean code. If this doesn't sound familiar to you, I would highly recommend watching the playlist [Clean Code - Uncle Bob](https://www.youtube.com/watch?v=7EmboKQH8lM&list=PLmmYSbUCWJ4x1GO839azG_BBw8rkh-zOj) on Youtube.
