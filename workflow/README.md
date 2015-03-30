Workflow
========

A guide to the AgentBright development workflow.

Our roots: [How We Work - Big Binary](http://how-we-work.bigbinary.com/)

For specifics, see the list below:

* [Issues](/workflow/issues)
* [Styling](/workflow/styling)
* [Best Practices](/workflow/best-practices)
* [Testing](/workflow/testing)
* [Environments](/workflow/environments)


**For development, we use a version of the Github Flow pattern:**

1. For each issue/feature, create feature branch
2. Write code and commit
3. Open pull request
4. Upon approval, merge feature branch into the master

Feature Branches
----------------

* For each issue, create a feature branch
* The branch name should start with the Github issue number

  ```sh
  git checkout -b 1344-show-recurring-events-on-dashboard
  ```

Code
----

We prefer to follow the red-green-refactor pattern of TDD:

1. Write a failing test
2. Write the minimum amount of code to get the test to pass
3. Refactor the code to bring it inline with best practices

Commits
-------

Commits should be descriptive, and encapsulate logicals chunks
of the issue you are working on.

* The commit message should end with ` - #<issue number>`

  ```sh
  Add recurrings to events service - #1344
  ```

* The additional description should outline the work the additions
  or changes that you made.
* Use specificity of language and describe include the purpose or
  reasoning behind your code if it is not obvious.

Rebasing
--------

* If the branch becomes out of date with the master, rebase:

  ```sh
  git rebase origin/master
  
  # When the rebase is complete:
  git push -f origin 1344-show-recurring-events-on-dashboard
  ```

* Squash your commits into a few main self-contained commits:

  ```sh
  git rebase -i HEAD~5
  
  # When squashing is complete
  git push -f origin 1344-show-recurring-events-on-dashboard
  ```

Instapusher
-----------

We use Instapusher to deploy our feature branches to Heroku.

* All commits made to a pull request will automatically trigger
  Instapusher to run on that branch
* To manually trigger an Instapusher job, push to remote, then
  sit in your feature branch and run `instapusher`

Pull Requests
-------------

When you are ready for code review and testing, convert your
issue into a pull request

* Use hub to convert your issue to a pull request:

  ```sh
  hub pull-request -i 1344
  
  # replace '1344' with your issue number
  ```

* Ensure the tests pass on CircleCI
* Fix style corrections suggested by Hound
* Ensure that the Instapusher job is successful
* Assign the PR to the team member responsible for testing or
  code review
* Write a comment to the assignee to let them know that the
  PR is ready for their feedback

Code Review
-----------

Code review checks the following:

* Does the new feature work correctly?
* Is there appropriate test coverage?
* Was the implementation consistent with the requirements?
* Are there any requirements that need to be added or clarified?
* Does the code meet our style and best practices standards?
* Are there dependency, upstream or scaling concerns?

Code review can be touchy. Two things to remember:

1. Anyone who creates something and puts it in front of another is
   being vulnerable. As a reviewer, be critical, but be fair, civil,
   and do not be overly stingy with praise.
2. As the author, anyone who looks at your code and gives you feedback
   is giving you the opportunity to improve your craft. Questioning perfect
   code still gives you the chance to improve your ability to articulate your
   choices and your reasoning. Embrace the process.
   
Merging
-------

* When the issue has been approved, assign it to the team lead
* The team lead will merge it into the master branch, and push to staging,
  beta, or production environments if necessary.
