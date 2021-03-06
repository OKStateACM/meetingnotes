### Get Git!

#### ACM Meeting Agenda — February 8, 2017

***

##### Announcements

- ACM Highlight – ["The Real Threat Is Machine Incompetence, Not Intelligence"](https://motherboard.vice.com/en_us/article/the-real-threat-is-machine-incompetence-not-intelligence) by Michael Byrne

- AI Workshop – this Saturday, February 11 from 1:00-4:00 in MSCS 203W

    - Work through introductory programs covering various aspects of artificial intelligence!

    - Bring a laptop!

***

##### Introduction to Git

###### Setup

- Create an account on [GitHub](https://www.github.com).

- Install Git

    - __Windows__: Install Git from [git-scm.com/download](https://www.git-scm.com/download). Make sure the installer also installs Git Bash.
    - __Linux__: Install the `git` package using your package manager of choice.
    - __Mac__: No worries - Git should already be installed!

###### What is Git?

In the [/r/cscareerquestions](https://www.reddit.com/r/cscareerquestions) subreddit's recent [survey](https://www.reddit.com/r/cscareerquestions/comments/5rvlig/meta_results_of_the_2016_subreddit_demographics/), Redditors were asked, among other things, which tools and technologies they used the most at work. The following word cloud reflects their responses:

![Word cloud of technologies used at work. "Git" is by far the most prominent.](https://i.imgur.com/N3tYmGF.png)
        <small>[Source](https://www.reddit.com/r/cscareerquestions/comments/5rvlig/meta_results_of_the_2016_subreddit_demographics/)</small>

As you can see, Git is very prominent.

Git is a tool for *version control* – maintaining the history of changes made to a file or directory.

###### Version Control Exercise

> "The quick brown fox jumped over the lazy dog."

1. Using pen and paper, copy down the above sentence.

2. Rewrite the above sentence, making a single change. This change can be adding a word, removing a word, or replacing a word.

3. Get with a couple of other people who have done the above two steps. Merge your changes together into one sentence.

4. Everyone in the group should copy this new sentence, and then make another change.

5. Merge everyone's changes together once more.

###### Reflecting on the Version Control Exercise

What problems did you encounter? Did two people change the same word? Did one person replace a word that another simply removed? How did you resolve those conflicts?

This exercise reflects the general workflow of using Git, or really any version control program.

![A branch diagram of the above exercise, demonstrating two branches created from the master. Ben's branch, in orange, changes "brown" to "green." Alex's branch, in blue, changes "fox" to "frog." Alex's branch is merged into Ben's branch, which is then merged into the master.](http://i.imgur.com/vP4ryBu.png)

The above diagram demonstrates this exercise with two people. The thick black line refers to the *master branch*, or the canonical current state of the code. If this were a big project like a web app, the master branch would be what gets shipped out to the users. Each change to the sentence is denoted by a circle. The first circle in the master branch here represents the initial state of the sentence: *"The quick brown fox jumped over the lazy dog."*

When we made our own copies of the master sentence for our own modifications, we made *branches.* Ben's branch, depicted in orange, shows any changes Ben's made – in this case, replacing "brown" with "green." Until Ben's branch gets merged into the master branch, the master branch doesn't have any of Ben's changes. Similarly, Alex's branch, in blue, diverges from the master. Alex changes "fox" to "frog." Alex's branch is now merged into Ben's branch. The combined changes make the sentence *"The quick green frog jumped over the lazy dog."* Ben and Alex are satisfied with their hard work, so they merge Ben's branch into the master branch. The master branch now reads *"The quick green frog jumped over the lazy dog."*

###### Repositories

Git deals with *repositories*, or *repos* for short. A repository is effectively a folder with Git superpowers enabled. This means it will track changes made to tracked files inside that directory.

###### Git Workflow and Commands

- Open up your terminal with Git installed. For Mac and Linux users, this should be your regular terminal. Windows users should open Git Bash.

    - Git not only wants to know *what* changes are made but also *who's* making them. Because of that, if this is your first time using Git, you'll need to give Git your name and email.

        - Give Git your name by using the `git config --global user.name "John Doe"` command.

        - Give Git your email address by using the `git config --global user.email "john.doe@okstate.edu"` command.

- Creating a Git repository

    - Navigate inside the folder you'd like to turn into a repository using the `cd` command ([refresher/introduction to `cd`](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/3/html/Step_by_Step_Guide/s1-navigating-cd.html)).

    - When inside the folder you'd like to turn into a repository, call `git init` – this turns your folder into a repo.

    - Alternatively, if you'd like to create a repository with a folder that doesn't yet exist – let's call this new folder `foldername` – you can call `git init foldername` to create a new folder called `foldername` which is also a repository.

- Calling `git status` inside a repository is a helpful way to check where you are in the Git workflow and to see which problems need to be corrected. Call it often.

![Three blocks are shown: "working directory," "staging area," and "repository." An arrow labeled "git add" connects the working directory to the staging area, and an arrow labeled "git commit" connects the staging area to the repository.](https://i.stack.imgur.com/naws3.png)

<small>[Source](http://stackoverflow.com/questions/3689838/difference-between-head-working-tree-index-in-git)</small>

- Staging and committing

    - Let's create some modifications for Git to track. Make sure you're in your repository. Create a new text file. It doesn't even need any content for now. A quick shortcut to create a blank file called something like `file.txt` using your Bash terminal is calling `touch file.txt`, which will create `file.txt` if it doesn't already exist.

    - Let's check on the status of our Git repository by calling `git status` – hopefully you'll get something like this:

    ```
    On branch master
    Untracked files:
    (use "git add <file>..." to include in what will be committed)

        file.txt

    nothing added to commit but untracked files present (use "git add" to track)
    ```

    - Git doesn't store every change made to a file ever. Instead, it stores snapshots of a file upon command. These snapshots are called *commits*. Additionally, making changes to a file isn't enough to make sure Git commits those changes. The `git status` check above shows us that our newly created `file.txt` is currently "untracked."

    - Call `git add file.txt` to "stage" it – in other words, to queue `file.txt`'s changes to be in the next snapshot, or *commit*, of the repository. In technical terms, this would mean that `file.txt` is now in the "staging area."

    - Call `git status` again. This time, you should get

    ```
    On branch master
    Changes to be committed:
    (use "git reset HEAD <file>..." to unstage)

        new file:   file.txt

    ```

    - The above message tells us that `file.txt`'s changes since its last commit (since it's a new file, it won't have a previous commit) will be snapshotted in the next commit.

    - To commit all staged files, call `git commit -m "A commit message should go here!"`. Commits have *commit messages*, or useful descriptions of the changes being snapshotted, so that later, people looking back at the version history can get a sense of which commit ties to which changes.

    - Upon committing, check the status again using `git status`. Your status should now read

    ```
    On branch master
    nothing to commit, working tree clean
    ```

    - Staging each file individually would be tedious, so Git provides several shortcuts. You can call `git add .` which adds all modified files to the staging area. Alternatively, you could call `git commit -am "Commit message here"` which will both add all modified files to the staging area and commit them with one command.

    - It's a good practice to commit every time you've added a working feature.

- Branching

    - In our pen/paper exercise, we demonstrated branching. Everyone had their own clean copy – or *branch* – of the "code" to edit individually.

    - In an enterprise-scale application, the *master branch* is usually what gets shipped out to clients or users. It's a really bad idea to make changes directly to the master branch, because one developer's changes could make the code refuse to compile or break other developers' code. Because of this, it's a best practice to open a new branch to build a new feature in.

    - To create a branch of your repository called `branchname`, make sure you're in your repo and call the `git branch branchname` command.

    - As always, run a `git status` check:

    ```
    On branch master
    nothing to commit, working tree clean
    ```

    - Even though we created the branch `branchname`, we're still in branch `master`. to switch over to `branchname`, call the `git checkout branchname` command.

    - Make a change to your text file, and commit that change.

    - To make sure that the master branch isn't getting those changes, call `git checkout master` and open your text file. It should be unchanged.

    - We're satisfied with the changes we've made in our `branchname` branch, so let's merge `branchname` into `master`. Call `git checkout branchname` to get back into the `branchname` branch, and then call call `git merge master` to merge `branchname` into `master`.

    - Because there haven't been any conflicting changes to `master`, this merge is easy. However, if conflicting changes have been made, you'll have a *merge conflict*, and Bash will take you to a text editor to determine whose changes should stay and whose should go.

##### Remote Repositories and GitHub

Thus far, your repo has only been a *local repository*, meaning it exists only on your machine. However, we've referred to modifying a repository with other people! To do this, you need a *remote repository* – a Git repository hosted on some public server. This is the service that [GitHub](https://www.github.com) provides for us. So how do we get repositories on GitHub? It depends on whether we want a fresh repository or to upload a preexisting repository.

###### Creating a *fresh* repository on GitHub

1. After logging in to your GitHub account, click the green "New repository" button on the right.

2. Give this repository a name and, because we __aren't__ uploading any preexisting repositories, __click__ the checkbox to initialize this GitHub repository with a README. Click the "Create repository" button.

3. You can use GitHub's online interface to make changes, but you'll probably prefer to make changes locally. To create a local version of the repository to make changes to, you'll need to *clone* the repository. Navigate into your repository on GitHub, and click the green "Clone or download" button. Copy that link that starts with `git@github.com:` and ends with `.git`.

4. In your Bash terminal, navigate to the folder where you'd like to keep your local version of the repository and call the `git clone "git@github.com:YourGitHubUsername/yourGitHubRepo.git"` command, substituting the link in quotes with the repository link you just copied.

###### Getting a Preexisting Repository onto GitHub

1. After logging in to your GitHub account, click the green "New repository" button on the right.

2. Give this repository a name and, because we __are__ uploading any preexisting repositories, leave the checkbox to initialize this GitHub repository with a README __unchecked__. Click the "Create repository" button.

3. On the next page, copy the link that starts with `git@github.com:` and ends with `.git`.

4. Navigate into your repository in Bash and call the `git remote add origin "git@github.com:YourGitHubUsername/yourGitHubRepo.git"` command, substituting the link in quotes with the repository link you just copied. This connects your local repository to the repository hosted on GitHub.

5. *Push* your preexisting files (which should already have been committed) to GitHub by calling `git push origin master` – this sends any commits that have been made locally to the `origin` server, `master` branch.

###### Pushing and Pulling

![Two monkeys are shown with local versions of a remote repository. They both say "I edit this!" in reference to their own local repository. Both local repositories have an arrow labeled "Push" directed to the remote repository and an arrow labeled "Pull" directed from the remote repository. ](https://backlogtool.com/git-guide/en/img/post/intro/capture_intro1_2_2.png)

Now that you have a local version of a remote repository, it's time to make some changes! Modify a file in your local repository. Then add it to the stage area and then commit it. For the time being, this commit only stays in the local repository. If we visit the repo on GitHub, we wouldn't see any changes. To push our local commits to the remote repository, `git push origin master` in the local repository.

- To push to someone else's GitHub repository, we need to be a member of their repo. Have them visit their repo on GitHub, click "Settings," then go to "Collaborators." Then have them add your GitHub username. You'll receive an email that you'll have to accept.

Our local repository is not automatically updated whenever changes are made to the remote repository. To update our local repository with changes to the remote repo, call the `git pull` command.
