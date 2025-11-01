# Git-branching-strategy
#how comnies use branching in real projects
✅ Step 1: Create Project Folder & Init Git

Commands:

mkdir shopping-app
cd shopping-app
git init
echo "# Shopping App Project" > README.md
git add .
git commit -m "Initial commit"


📌 Result: Project initialize done

✅ Step 2: Create develop Branch
git checkout -b develop
git push origin main
git push origin develop
git commit -m "Created develop branch"


📌 Now have:

main → Production

develop → Future features

✅ Step 3: Create Feature Branch

Feature: Add login system

git checkout develop
git checkout -b feature/login


Add file:

echo "Login feature code here" > login.txt
git add login.txt
git commit -m "feat: add login module"


Push branch:

git push -u origin feature/login


📌 Developer is coding on login feature

✅ Step 4: Merge Feature → develop (PR scenario)

Simulating PR merge:

git checkout develop
git merge --no-ff feature/login -m "Merge login feature"


Delete branch:

git branch -d feature/login
git push origin --delete feature/login


📌 Login feature completed & merged

✅ Step 5: Create Release Branch
git checkout develop
git checkout -b release/1.0
echo "Release notes v1.0" > RELEASE.md
git add .
git commit -m "chore: prepare release v1.0"
git push origin release/1.0


📌 QA team testing here

✅ Step 6: Merge Release → main & Tag
git checkout main
git merge --no-ff release/1.0 -m "Release v1.0"
git tag -a v1.0 -m "Version 1.0"
git push origin main --tags

✅ Step 7: Merge Release back → develop
git checkout develop
git merge --no-ff release/1.0 -m "Sync release changes"
git push origin develop


Cleanup:

git branch -d release/1.0
git push origin --delete release/1.0


📌 Production Released 🚀

🆘 Hotfix Example

Bug found in production

git checkout main
git checkout -b hotfix/login-bug
echo "Fix Login Bug" > fix.txt
git add fix.txt
git commit -m "fix: login failure issue"


Merge fix to main & tag:

git checkout main
git merge --no-ff hotfix/login-bug
git tag -a v1.0.1 -m "Hotfix v1.0.1"
git push origin main --tags


Merge fix back to develop:

git checkout develop
git merge --no-ff hotfix/login-bug
git push origin develop


Cleanup:

git branch -d hotfix/login-bug
git push origin --delete hotfix/login-bug


✅ Hotfix done successfully

🏁 Final Folder Structure
shopping-app/
 ├─ README.md
 ├─ login.txt
 ├─ RELEASE.md


✅ You now saw real-world Git flow hands-on!
