README
======

A git post-commit script to link commits to Asana tickets.

### Magical setup:
`% cd workspace`

`% bash <(curl https://raw.githubusercontent.com/Spaceman-Labs/asana-post-commit/master/setup.sh)`

### Manual setup:
Copy the post-commit file to your repo's root `.git/hooks` directory. It's probably not a great idea to actually clone the repo into the internals of your repo. I don't know that it will break anything, but I don't guarantee it won't.

Then run the following commands:

`% git config --global user.asana-token "MY_ASANA_PERSONAL_ACCESS_TOKEN" (http://app.asana.com/-/account_api)`

`% git config --global user.display-branch-name-in-comment "true/false" # (This is config is optional, defaults to true)`

Then chmod your hooks folder and post-commit hook file:
`% chmod 755 .git/hooks && chmod ogu+rx .git/hooks/post-commit`

Now in your commits, you can write messages like "Tweaked the widget; fixed #1, #2, and #3; references #4 and #5; oh yeah, and closes #6" and the right thing will happen. Alternatively you can
use the full Asana ticket URL (e.g. https://app.asana.com/0/123456789012345/098765432109876)

As another alternative, if the branch name ends with '#' followed by the task id then a comment will also be added to the task. Example for branch name with task id 1: `myBranch#1`
