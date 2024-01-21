# helloworld_ghpages
Easy onboarding tutorial to get a Github page, for react app.
No need to clone this repo. Instructions below is how to get started from scratch.

## Onboarding to a new app

1. On the Github UI, create a new git repo, e.g. ***helloworld_ghpages***. 
2. On your computer, install npm and npx tools if you have not already.  
3. Clone the git repo locally, and navigate to your project's directory. 
```
git clone [SSH_LINK_FROM_GITHUB]
cd my-website
```
4. Run the following to initialize your React App:
```
npx create-react-app ./
```
5. Inside the project root directory, create a directories `.github/workflows/`, and then inside that directory create an empty file `gh-pages.yml`. So the path of the file should look like `helloworld_ghpages`.github/workflows/gh-pages.yml`.
```
mkdir -p ./.github/workflows/
touch ./.github/workflows/gh-pages.yml
```
6. In the new file `gh-pages.yml`, copy and paste the following code into it:
```
name: Deploy to GitHub Pages
on: [push]
permissions:
  contents: write
jobs:
  build-deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v3
      - name: Install dependencies
        run: npm install
      - name: Build website
        run: npm run build
      - name: Deploy to GitHub Pages
        uses: JamesIves/github-pages-deploy-action@v4
        with:
          token: ${{ secrets.GITHUB_TOKEN }}
          branch: gh-pages
          folder: build

```
7. In the project root directory, in the file `package.json`, under the line with `name`, add a line for `homepage`, like below. Note: replace *YOURGITHUBUSERNAME* and *YOURPROJECTNAME* with your Github username and your project name respectively, e.g. for me it is *liu00david* and *helloworld_ghpages*. See this repo's package.json for example.
```
  "homepage": "https://YOURGITHUBUSERNAME.github.io/YOURPROJECTNAME",
```
8. Git add and commit your changes:
```
git add .
git commit -m "adding gh-pages yaml file"
git push
```
9. Go to the Github UI and see your latest changes to your files.
10. Go to **Settings**, then on the left sidebar go to **Pages**. In the dropdown menu for **Source**, select **Deploy from a branch**, then **gh-pages**. Click **Save**.
11. Near the top-middle of the page, click on **Actions**. See the page actions jobs that are running (should show yellow dots).
12. Once the jobs complete (are green), visit your website on Github pages, which should be at `https://YOURGITHUBUSERNAME.github.io/YOURPROJECTNAME`.
    
