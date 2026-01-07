## Unit

# Git Advanced

## Links

* [Required Questions](#required-questions)
* [Preferred Questions](#preferred-questions)
* [Stretch Questions](#stretch-questions)

## Required Questions

[Back to top](#unit)

* What is a branch? What are some common branching strategies?
  * Keywords, concepts, or topics that should be in the response:
    * A branch is a separate path of changes made to the codebase
    * Typically you'll have a main or master branch from which production deployments are made, a dev branch for changes in progress, and feature branches that branch from dev for features being worked on
  * Possible follow-up questions
    * How to create a new branch?
      * `git checkout -b mynewbranch` OR `git branch mynewbranch && git checkout mynewbranch`

* Describe a branch policy, and how it benefits your project.
  * Keywords, concepts, or topics that should be in the response:
    * A branch policy is a set of rules that regulates the ways a git repository can be interacted with.
    * Common policies include setting a minimum number of reviewers for a pull request, or restricting which branches can be contributed to directly without review.
    * Branch policies are generally based on the pattern of branch name.

## Preferred Questions

[Back to top](#unit)

* Describe the differences between rebase, fast-forward, and squash options when merging.
  * Keywords, concepts, or topics that should be in the response:
    * Fast-forward results in a linear commit history, making it look as if the changes on the feature branch were developed directly on the target branch. There's no explicit record of when the merge happened.
    * Rebase also results in a linear commit history, but unlike a fast-forward merge, it achieves this by creating new commits that represent the changes from the original branch applied to the new base. The original commits are no longer part of the branch's history.
    * Squash will have a linear history with a single commit representing all the changes from the merged branch. The detailed commit history of the feature branch is not preserved in the target branch's history.

* What is a pull request/merge request?
  * Keywords, concepts, or topics that should be in the response:
    * A request to merge changes made in the code from one branch into another
    * Usually this is where code reviews take place and feedback is given on the code
    * Any changes can be made here before code is merged

* How would you go back in your commit history if you make a mistake?
  * Keywords, concepts, or topics that should be in the response:
    * `git checkout <commit hash>`
    * `git revert` to undo the last commit

## Stretch Questions

[Back to top](#unit)

* Describe the result of forking a repo, and how it differs from cloning.
  * Keywords, concepts, or topics that should be in the response:
    * Forking a repo creates a copy of the original repository in the chosen organization.
    * Cloning establishes a local copy of the remote repository. Forking creates a new remote copy of the remote repo, that references the original remote repo.
