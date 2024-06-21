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
git submodule add https://github.com/alex-shpak/hugo-book themes/hugo-book

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