---
title: "用 Github Actions 部屬 Hugo 網站"
date: 2020-09-02T00:15:01+08:00
draft: false
tags: ["Github Actions","Hugo","Blogs"]
---
## [Hugo](https://gohugo.io/)
> The world’s fastest framework for building websites  
> 
~~我也不知道是不是~~
## [GitHub Actions](https://github.com/features/actions)
> Automate your workflow
from idea to production  

   * CI/CD工具
### Step
1. 安裝 Hugo
   * [Windows(Chocolatey)](https://gohugo.io/getting-started/installing/#chocolatey-windows)
   * [Homebrew (Linux)](https://gohugo.io/getting-started/installing/#homebrew-linux)
  
  * 版本有分 **hugo-extended/hugo** 有些Theme會需要安裝hugo-extended  

2. 建立 WebSite
   * `hugo new site hugo_blog`
3. Init Commit
    ```bash
    cd hugo_blog
    git commit -m "init commit"
    ```
4. 建立 GitHub Actions  
   * [hugo-setup](https://github.com/marketplace/actions/hugo-setup)
   * 放在 `./github/workflows/main.yml`

        ```yml
        name: github pages

        on:
        push:
            branches:
            - master  # Set a branch to deploy

        jobs:
        deploy:
            runs-on: ubuntu-18.04
            steps:
            - uses: actions/checkout@v2
                with:
                submodules: true  # Fetch Hugo themes (true OR recursive)
                fetch-depth: 0    # Fetch all history for .GitInfo and .Lastmod

            - name: Setup Hugo
                uses: peaceiris/actions-hugo@v2
                with:
                hugo-version: 'latest'
                extended: true

            - name: Build
                run: hugo --minify

            - name: Deploy
                uses: peaceiris/actions-gh-pages@v3
                with:
                github_token: ${{ secrets.GITHUB_TOKEN }}
                publish_dir: ./public
        ```
5. 推上 GitHub  
   `<USERNAME>.github.io`  這個repo    
   或是置於其他的repo
   ![](https://guides.github.com/features/pages/repo-settings.png)
   ![](https://guides.github.com/features/pages/launch-theme-chooser.png)
   * 將Branch改為 **gh-pages**  
    > 因為上面的Github Actions 會把build完成的網站推到gh-pages這個分支  
    ![](https://i.imgur.com/73x9wu8.png)
* 從此以後 你每次推送上github的commit Github都會自動幫你輸出網頁到  
`https://<USERNAME>.github.io` 