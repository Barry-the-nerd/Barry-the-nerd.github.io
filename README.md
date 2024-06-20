# Barry-the-nerd.github.io


1. Create new site
```
hugo new site . --force
```

2. Setup book theme
```
git submodule add https://github.com/alex-shpak/hugo-book themes/hugo-book
rm -rf .git/modules/themes/hugo-book
rm -rf themes/hugo-book/.git themes/hugo-book/.github

echo "theme = 'hugo-book'" >> hugo.toml
```
**optional** : copy sample data
```
cp -R themes/hugo-book/exampleSite/content.en/* ./content
```

3. Start server
```
hugo server --minify
```

4. push to github


https://gohugo.io/hosting-and-deployment/hosting-on-github/