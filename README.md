![git-flow](https://raw.githubusercontent.com/tatoanhn02/Git-flow/main/workflows.drawio%20v2.png)
Flow git

There are six branch types:

- Master(main)
- Release
- Hotfix
- Develop
- Feature
- Fix

The code management process after each sprint typically looks like this:

- The code for new feature at: `feature/xxx`
- After the code for the feature is done, it will be merged into the develop
- If there are any code change to fix the bugs, it will be created from fix/xxx branch and merged into develop
- After each sprint will create a release branch for the previous sprint, ex: release/1.0.1, release/1.0.2...
- After REG is done, mean that the code in release branch is test to done, the code in release branch will merged into master
- If there are any bugs in production env that need to be fixed, it will be created from `hotfix/xxx` and merged into master

---

This project is still under development. Feedback and suggestions are very welcome
