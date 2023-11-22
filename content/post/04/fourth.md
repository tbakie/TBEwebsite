---
title: "How To Deploy Website In Github"
date: "2023-11-07T11:02:08-07:00"
author: " Efesoy "
draft: false
categories: ["Github", "Website"]
cover:
    image: post/04/4.png

---
  # Deploying ⚙️
 Creating a website on GitHub is an effective and professional way to present your projects and interests to a global audience. Utilizing GitHub Pages, you can host your site directly from a GitHub repository, offering a no-cost solution with the robust infrastructure of GitHub. This approach is not only economical but also integrates seamlessly with your development workflow.

 ⚙️By automating the deployment process, GitHub Actions offers another degree of efficiency. GitHub Actions may automatically build and deploy your site whenever you make improvements to your repository, ensuring that it always represents your most recent work. This automatic pipeline is essential for keeping a dynamic, up-to-date online presence.

 ## Steps to Deploy Your Website on GitHub:
- ⚙️Create a Repository: Start by creating a new repository on GitHub for your website.
- ⚙️Add Your Website Code: Upload your website's HTML, CSS, and JavaScript files to the repository.
- ⚙️Set Up GitHub Actions: Configure GitHub Actions to automate your deployment process. This involves creating a workflow file in your repository.
- ⚙️Write the Workflow File: In the '.github/workflows' directory, create a new file (e.g., 'deploy.yml') and define the deployment steps. Here's an example workflow for a Hugo-based site:
```css
name: Publish to GH Pages
on:
  push:
    branches:
      - main
  pull_request:

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout source
        uses: actions/checkout@v3
        with:
          submodules: true

      - name: Checkout destination
        uses: actions/checkout@v3
        if: github.ref == 'refs/heads/main'
        with:
          ref: gh-pages
          path: built-site

      - name: Setup Hugo
        run: |
          curl -L -o /tmp/hugo.tar.gz 'https://github.com/gohugoio/hugo/releases/download/v0.110.0/hugo_extended_0.110.0_linux-amd64.tar.gz'
          tar -C ${RUNNER_TEMP} -zxvf /tmp/hugo.tar.gz hugo          
      - name: Build
        run: ${RUNNER_TEMP}/hugo

      - name: Deploy
        if: github.ref == 'refs/heads/main'
        run: |
          cp -R public/* ${GITHUB_WORKSPACE}/built-site/
          cd ${GITHUB_WORKSPACE}/built-site
          git add .
          git config user.name 'tbakie'
          git config user.email 'tbakiefesoy03@gmail.com'
          git commit -m 'Updated site'
          git push
```
- ⚙️Enable GitHub Pages: Go to your repository settings, find the GitHub Pages section, and select the branch you want to deploy (typically 'gh-pages' or 'main').
- ⚙️Access Your Live Site: Once GitHub Actions completes the deployment, your site will be live at https://{username}.github.io/{repository}.

⚙️**Remember**, your website's visibility and success depend on how effectively you manage and update its content. Happy coding!

⚙️This method is particularly advantageous for static websites, personal or professional blogs, portfolio sites showcasing your work, and documentation for projects or software. It simplifies the process of keeping your content fresh and aligned with your ongoing projects or evolving portfolio, making it an excellent choice for developers, creatives, and professionals looking to establish a strong online presence.
