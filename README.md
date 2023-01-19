# Sample Python/Poetry project with conventional commits

This is an sample project that demonstrates how to use the conventional commits standards to simplify Python/Poetry versioning steps.

## Basic Tools

- Python
- Poetry
- Git
- Git MkVer


## Get Started

### 1. Install [Git CLI](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) and [Git-MkVer CLI](https://idc101.github.io/git-mkver/installation).
### 2. Install [Python](https://www.python.org/downloads/)
### 3. Install [Poetry](https://python-poetry.org/docs/)
### 3. Clone or initialize local git repository.


```bash
git clone git@github.com:alansferreira/git-mkver-with-poetry.git 
cd git-mkver-with-poetry
```
Or

```bash
mkdir git-mkver-with-poetry
git init
```
### 

### 2. Initialize the `.semver` file .

```bash
echo "0.0.0" > .semver
```
### 3. Well done, now you can just make yours commits following the **conventional commits** on your messages and use this commands bellow:

```bash
# Create an 'fix' commit
git commit -m "fix: this is an fix commit" --allow-empty

# Bumping new version
git mkver patch 
# Use Poetry to sync 'pyproject.toml' version with new '.semver' value
poetry version $(cat .semver)
# Commit Bumped files
git add .semver pyproject.toml
git commit -m "build: bumping to $(cat .semver)"
git mkver tag

# Push your(s) tag(s) to remote
git push --follow-tags
```

## Extras

> Will come instructions to attach git hooks to enforce conventional commits

<!-- ### Enforce check conventional commits with Git Hooks

Create `commitlint.config.js` file:
```js
module.exports = {
  extends: ['@commitlint/config-conventional']
}
```

Add **scripts** and **devDependencies** on `package.json` file:
```json
{
  "scripts": {
    "prepare": "husky install && husky add .husky/commit-msg 'npx commitlint --edit $1",
    ...
  },
  "devDependencies": {
    "@commitlint/cli": "^17.3.0",
    "@commitlint/config-conventional": "^17.3.0",
    "husky": "^8.0.2",
    ...
  }
}
```

Run **npm**  with any commands that pass in **prepare** script like **install** arg:

```bash
npm install
```

Well done! Now if you try run an `git commit -m "it's not an conventional message"` you will should receive this message:

```console
$ git commit -m "it's not an conventional message"

⧗   input: it's not an conv pattern message
✖   Please add rules to your `commitlint.config.js`
    - Getting started guide: https://commitlint.js.org/#/?id=getting-started
    - Example config: https://github.com/conventional-changelog/commitlint/blob/master/%40commitlint/config-conventional/index.js [empty-rules]

✖   found 1 problems, 0 warnings
ⓘ   Get help: https://github.com/conventional-changelog/commitlint/#what-is-commitlint

husky - commit-msg hook exited with code 1 (error)
``` -->
