# helloworld_ghpages
easy onboard tutorial for ghpages from react app

## Onboarding to a new app

1. On the Github UI, create a new git repo, e.g. ***my-website***. [How to create a new git repo].
2. On your computer terminal, make sure you have npm [How to install npm].
3. Git clone the project repo locally, and navigate to your project's directory, e.g. ***my-website***. [How to use git]
```
git clone [SSH_LINK_FROM_GITHUB]
cd my-website
```
4. Run the following to initialize your React App:
```
npx create-react-app ./
```
5. Create a directory '.github/workflows/', and then inside that directory create a file "gh-pages.yml". So the path of the file should look like '***my-website***/.github/workflows/gh-pages.yml'.
```
mkdir -p ./.github/workflows/
touch ./.github/workflows/gh-pages.yml
```
6. In 'gh-pages.yml', copy and paste the following code into it:
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
7. Git add and commit your changes by running:
```
git add .
git commit -m "adding gh-pages yaml file"
git push
```
8. Go to the Github UI and see your latest changes. [How to fix Git push issues]
9. Ggo to **Settings**, then on the left sidebar go to **Pages**. In the dropdown menu for **Source**, select **Deploy from a branch**, then **gh-pages**. Click **Save**
10. Near the top-middle of the Github UI, click on **Actions**. See the page actions jobs that are running (should show yellow dots).
11. Once the jobs complete (are green), visit your website on Github pages. You are done.
