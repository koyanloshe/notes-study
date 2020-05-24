# Git extras

$ git log --oneline --decorate --graph --all -30
 
To get a formatted log output.
 
$ git config --global alias.sla 'log --oneline --decorate --graph --all'
 
$ git sla
 
----------
 
$ git log --pretty=format:'%h - %an [%ar] %s'
 
--------
 
$ git log -E -i --grep 'cach(e|ing)'
 
--------
 
$git commit --amend
 
--------
 
git status --short
 
Git
 
Branch
Changes you make on a branch donÕt affect the maste r branch.
Branch name should be verbose
Ê
Commits
Writing clear messages makes it easier for others to follow and to provide feedback
Ê
Pull Request
@mention system you can ask for feedback from specific people or teams
Fork and Pull model - pull requests notify the project maintainers about changers.
Shared Repo Model - Pull requests help start code review and conversation about proposed changes before merging to master
Ê
Deploy
On review of pull request the branch passes your tests and can be deployed on prod.
If branch causes and issue you can roll it back.
Ê
Merge
Once verified on Prod, merge the code into the master branch.
Once merged Pull requests preserve a record of historical changes to code with searchable history and lets anyone go back in time.
 
**## Gitlab
**
_https://www.vultr.com/docs/install-gitlab-ce-on-centos_

