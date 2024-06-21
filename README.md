# Barry-the-nerd.github.io

1. Create new site  

Github workflow expects the hugo site is at the root of the repo.  Please create hugo site by running the following command at the root of the repo.  As a git repo contains some hidden files and folders, please use --force parameter.     
```
hugo new site . --force
```
This is the expected folder structure.  
```
<your repo directory>/
├── archetypes/
├── content/
├── layouts/
├── static/
├── ...
├── hugo.toml
└── .github/
    └── workflows/
        └── deploy.yml
```


2. Setup book theme
```
# if you want to get it as a git submodule (refer to Use git clone or git submodule section below)
git submodule add https://github.com/alex-shpak/hugo-book themes/hugo-book

# if you want to clone it (refer to Use git clone or git submodule section below)
git clone https://github.com/alex-shpak/hugo-book themes/hugo-book

## Add theme setting to hugo.toml
echo "theme = 'hugo-book'" >> hugo.toml

## (Optional) Remove git settings if you don't need this to be a git submodule 
rm -rf .git/modules/themes/hugo-book
rm -rf themes/hugo-book/.git
rm -rf themes/hugo-book/.github

## (Optional) Copy sample data
cp -R themes/hugo-book/exampleSite/content.en/* ./content
```

3. Start server
```
hugo server --minify
```

4. push to github


https://gohugo.io/hosting-and-deployment/hosting-on-github/  

Base URL is set in workflow yml using "${{ steps.pages.outputs.base_url }}"  

**Reference**:
https://gohugo.io/documentation/

## Use git clone or git submodule

Here’s a comparison between `git clone` and `git submodule`:

| Aspect                   | `git clone`                                     | `git submodule`                                           |
|--------------------------|-------------------------------------------------|-----------------------------------------------------------|
| Basic Use                | Copies a repository into a new directory.       | Links an external repository inside another repository.   |
| Usage Command            | `git clone <repo_url>`                          | `git submodule add <repo_url> <path>`                     |
| Separate Repositories    | Maintains separate, standalone repositories.    | Integrates external repositories into a parent repository.|
| Version Tracking         | Tracks the entire history of the cloned repo.   | Tracks a specific commit of the submodule.                |
| Updates                  | Use `git pull` to update.                       | Use `git submodule update` to update to a new commit.     |
| Initial Setup            | Simple and straightforward.                     | Requires initialization and updates using specific commands. |
| Dependency Management    | No direct dependency management.                | Manages dependencies via submodules.                      |
| Workflow Complexity      | Simple workflow.                                | Adds complexity to workflow.                              |
| Nested Repos             | Creates separate repos; no nesting.             | Allows nested repos within the parent repo.               |

### When to Use
- **`git clone`**: Use when you need a full, standalone copy of a repository.
- **`git submodule`**: Use when you need to include an external repository as a part of a larger project, while maintaining its own versioning.

### Commands Summary
- **Clone**:
  ```sh
  git clone <repo_url>
  ```

- **Submodule**:
  ```sh
  git submodule add <repo_url> <path>
  git submodule update --init --recursive
  git submodule foreach git pull origin main
  ```

Choose based on your project requirements and workflow preferences.