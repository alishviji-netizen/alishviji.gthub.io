```markdown
# alishviji.gthub.io

This document explains how to create a website using GitHub Pages. Choose the option that fits your goal: a user/organization site or a project site.

## Quick overview

- GitHub Pages can host static websites directly from a repository.
- Two common site types:
  - User/Organization site: repository named `USERNAME.github.io` (example: `alishviji.github.io`). It publishes to `https://USERNAME.github.io`.
  - Project site: any repository. It publishes to `https://USERNAME.github.io/REPO_NAME` (or a custom domain).

## Option A — Create a User (or Organization) site

1. Create a new repository named exactly `USERNAME.github.io` (replace USERNAME with your GitHub username).
2. Locally, create a simple `index.html` (or `index.md`) file:
   ```html
   <!doctype html>
   <html>
     <head><meta charset="utf-8"><title>My site</title></head>
     <body><h1>Hello from GitHub Pages</h1></body>
   </html>
   ```
3. Push to the `main` (or `master`) branch:
   - git init
   - git add .
   - git commit -m "Initial site"
   - git branch -M main
   - git remote add origin https://github.com/USERNAME/USERNAME.github.io.git
   - git push -u origin main
4. Wait a few minutes, then visit `https://USERNAME.github.io`.

GitHub will serve the site automatically from the default branch.

## Option B — Create a Project site

Two common ways:

A. Publish from the `docs/` folder on the `main` branch:
1. Add your site files to a `docs/` folder at the repo root (`docs/index.html`).
2. Push to `main`.
3. In the repository Settings -> Pages, choose branch `main` and folder `/docs` and save.

B. Publish from a `gh-pages` branch:
1. Build your static site into the repository root or a `build/` folder and push the static output to a branch named `gh-pages`.
2. In Settings -> Pages, select branch `gh-pages` as the source.

After enabling, the site will be available at `https://USERNAME.github.io/REPO_NAME`.

## Using Jekyll (built-in)

- GitHub Pages supports Jekyll by default. Add files like `_config.yml`, `_layouts/`, and markdown pages.
- To use a theme, add in `_config.yml`:
  ```
  theme: minima
  ```
- Commits to the branch configured for Pages will be built with Jekyll automatically.

If you need plugins unsupported by GitHub Pages, build locally or via GitHub Actions and push the static output to the publishing branch.

## Using a static site generator (Hugo, Gatsby, Next.js, etc.)

- Option 1: Build locally and push the generated static files (HTML/CSS/JS) to the publishing branch (`main`, `gh-pages`, or `docs/`).
- Option 2: Use GitHub Actions to build on push and deploy the generated files to the Pages branch. Search for “deploy to GitHub Pages” actions; many ready-made workflows exist.

Simple GitHub Actions approach:
- Use a workflow that checks out code, installs tools, builds, and uses an action to deploy to `gh-pages` or the Pages branch.

## Custom domain

1. In your repository, create a file named `CNAME` with your custom domain (e.g., `example.com`).
2. In GitHub repo Settings -> Pages, set the custom domain as well.
3. Configure DNS:
   - For apex domains (example.com), add A records pointing to GitHub Pages IPs (check GitHub docs for current IPs).
   - For subdomains (www.example.com), add a CNAME pointing to `USERNAME.github.io`.
4. Wait for DNS propagation. GitHub will provide HTTPS via Let's Encrypt automatically (may take some time).

## Tips & troubleshooting

- 404 page: If you get 404, verify:
  - The publishing source (branch/folder) is correct in Settings -> Pages.
  - `index.html` is present in the published folder/branch.
  - Wait a few minutes after pushing.
- Custom domain problems: check CNAME file and DNS records.
- Use an automatic deploy workflow if your site generator needs a build step.
- Preview changes locally (Jekyll: `bundle exec jekyll serve`; Hugo: `hugo server`).

## Example minimal commands (user site)

Replace USERNAME with your GitHub username:

```
mkdir username.github.io
cd username.github.io
echo "<h1>Hello</h1>" > index.html
git init
git add index.html
git commit -m "Initial website"
git branch -M main
git remote add origin https://github.com/USERNAME/USERNAME.github.io.git
git push -u origin main
```

## Resources

- GitHub Pages documentation: https://docs.github.com/en/pages
- Jekyll docs: https://jekyllrb.com
- Search for “deploy to GitHub Pages” GitHub Actions templates for CI/CD.

---

If you’d like, I can:
- Commit this README to your repository,
- Create a starter `index.html`, or
- Create a GitHub Actions workflow that builds and deploys a static site for you.

Tell me which option you want and (if you picked me to commit) confirm repository and branch and whether overwriting README.md is OK.
```
```
