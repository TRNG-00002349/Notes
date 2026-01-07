## Unit

# Git Fundamentals

## Links

* [Required Questions](#required-questions)
* [Preferred Questions](#preferred-questions)
* [Stretch Questions](#stretch-questions)

## Required Questions

[Back to top](#unit)

* What is version control? What makes git different from other version control software?
  * Keywords, concepts, or topics that should be in the response:
    * Git is distributed version control system
    * Allows tracking changes, viewing past changes, reverting to old versions, etc
    * Git does not rely on "single point of truth", you can add many different codebase locations and keep them in sync
    * Git tracks units of work in "commits" that are linked to each other
    * Older centralized version control include subversion (`svn`)
  * Possible follow-up questions
    * Why should we use git instead of saving multiple copies of the code?

* How is git different from GitHub or BitBucket?
  * Keywords, concepts, or topics that should be in the response:
    * git is a decentralized version control tool.
    * GitHub, BitBucket, etc. are cloud services to work with git for remote file storage.

* What is a commit?
  * Keywords, concepts, or topics that should be in the response:
    * A unit of work, records the current state of the codebase in git

* What is the git workflow for contributing code to a central repository?
  * Keywords, concepts, or topics that should be in the response:
    1. Clone the repository `git clone <url>`
    2. Pull any updates from central repo `git pull`
    3. Make changes to codebase
    4. Stage the changes `git add <files>`
    5. Make a commit `git commit -m my commit message`
    6. Push to the central repo `git push`
  * Possible follow-up questions
    * What order should you run these git commands?
    * Are you missing any steps? What must you do before you commit or push your changes?

## Preferred Questions

[Back to top](#unit)

* What does the command `git init` do?
  * Keywords, concepts, or topics that should be in the response:
    * Creates `.git` hidden folder to track refs, commits, and objects internally
    * Initializes current directory as a git project to be tracked; required before committing, unless project was already cloned

* How would you prevent a file from being tracked by git?
  * Keywords, concepts, or topics that should be in the response:
    * Add the filepath to a file called `.gitignore`

## Stretch Questions

[Back to top](#unit)

* What is a branch? What are some common branching strategies?
  * Keywords, concepts, or topics that should be in the response:
    * A branch is a separate path of changes made to the codebase
    * Typically you'll have a main or master branch from which production deployments are made, a dev branch for changes in progress, and feature branches that branch from dev for features being worked on
  * Possible follow-up questions
    * How to create a new branch?
      * `git checkout -b mynewbranch` OR `git branch mynewbranch && git checkout mynewbranch`

* What is a GitHub pull request?
  * Keywords, concepts, or topics that should be in the response:
    * A request to merge changes made in the code from one branch into another
    * Usually this is where code reviews take place and feedback is given on the code
    * Any changes can be made here before code is merged
