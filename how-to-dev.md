# How to develop the BCCA website

This guide explains how to set up GitHub, GitHub Copilot, Visual Studio Code,
extensions, Git, and the local Jekyll development environment for the Bassendean
Community Children's Association website.

The website is a static Jekyll site. It uses HTML, CSS, JavaScript, YAML data,
and Markdown content. You do not need a traditional server-side application or
framework to edit it.

## 1. What you need

Before beginning, make sure you have:

- A Windows computer.
- An internet connection.
- A GitHub account.
- A GitHub Copilot subscription or access through an eligible plan. (The free one is fine)
- Visual Studio Code.
- Git.
- Ruby and Bundler.
- A terminal in Visual Studio Code.

The commands in this guide are written for Windows PowerShell. If you use Git
Bash, the same Git commands work, but the PowerShell environment variables below
will need to be adapted.

## 2. Create a GitHub account

1. Open <https://github.com/>.
2. Select **Sign up** in the upper-right corner.
3. Enter your email address and choose a strong password.
4. Choose a GitHub username. Use a name you are comfortable sharing publicly.
5. Confirm that you are human if GitHub requests verification.
6. Select **Create account**.
7. If prompted, complete the account-security checks.
8. Sign in to GitHub and open **Settings → Emails** to verify your email address.
9. Add a GitHub email address that you check regularly. This is important because
   GitHub uses it for account recovery and repository notifications.

You may be asked to enable two-factor authentication. GitHub offers several
security methods, including passkeys and authenticator applications. A passkey
is usually the simplest option for a personal computer.

## 3. Sign up for GitHub Copilot

GitHub Copilot availability depends on the plan and account type offered to you.
The free plan has been offered to eligible users, but GitHub can change its
availability and limits.

1. Sign in to GitHub.
2. Open <https://github.com/features/copilot> or go to **Settings → Billing and
   plans**.
3. Review the available Copilot plans.
4. Choose a plan that includes Copilot Chat and completion features.
5. If you are using a free plan, follow the prompts to join the eligible free
   tier and confirm your account information.
6. Sign out and back in if GitHub does not immediately show Copilot in your
   account.
7. Open the GitHub Copilot subscription page in your account settings and confirm
   that the correct plan is active.

If you are using GitHub through an organisation, ask the organisation owner
whether Copilot is already enabled for your account. You may need to accept an
invitation or sign in through the organisation's GitHub account.

> Do not share your password, authentication codes, or private API keys with an
> AI assistant. Copilot can help edit and explain code, but you remain responsible
> for reviewing the produced changes.

## 4. Install Visual Studio Code

1. Open <https://code.visualstudio.com/>.
2. Select **Download for Windows**.
3. Run the installer.
4. Select **Add Visual Studio Code to PATH** if the installer offers that option.
   This makes it easier to open the editor from PowerShell.
5. Select **Install**.
6. After installation, open Visual Studio Code.
7. If prompted, select **Open Visual Studio Code**.

To verify the installation, open a PowerShell terminal and run:

```powershell
code --version
```

If the command is not found, restart PowerShell and run the command again. You
can also use the **Command Palette** with **Shell Command: Install 'code'
command in PATH**.

## 5. Install Git

Git is required to work with GitHub and to track changes in the repository.

1. Download Git for Windows from <https://git-scm.com/download/win>.
2. Run the installer and allow Git to add itself to your PATH.
3. Restart Visual Studio Code or the PowerShell terminal.
4. Verify Git:

```powershell
git --version
```

5. Configure your Git identity for commits. Replace the sample values with your
   own name and email:

```powershell
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

6. Verify the configuration:

```powershell
git config --global --list
```

Use an email that GitHub can associate with your account. If GitHub provides a
GitHub-specific email address, you can use that address here.

## 6. Install the recommended Visual Studio Code extensions

Open Visual Studio Code, select **Extensions** in the left sidebar, and search
for the following extensions. Install each one that is not already installed.

### GitHub Copilot

1. Search for **GitHub Copilot**.
2. Install the extension published by GitHub.
3. Search for **GitHub Copilot Chat**.
4. Install that extension as well.
5. Open the Command Palette with **Ctrl+Shift+P**.
6. Run **GitHub Copilot: Sign in**.
7. Follow the browser prompts to sign in with the GitHub account that has the
   Copilot plan.

Copilot can help explain files, generate code, suggest content, and review
changes. It is not a replacement for reviewing the source files or testing the
site.

Realistically though, if you make it here you should be alright. Between Google and Copilot you should be able to fenagle your way into making changes -> reviewing them locally -> creating a pull request -> merge to kick off a build.

### GitHub Pull Requests and Issues

Install the extension named **GitHub Pull Requests and Issues** by GitHub.
It provides a convenient interface for issues, pull requests, and branch-based
workflows.

### GitLens

Install **GitLens — Git supercharged**. It adds useful Git features, including
commit history, repository status, blame information, and branch management.

### Markdown Preview Enhanced

Install **Markdown Preview Enhanced** by shd101wyy. This is useful for previewing
these instructions and any documentation you create.

### Markdownlint

Install **Markdownlint** by David Anson. It checks Markdown formatting and
common mistakes. You can enable formatting on save with the **Markdownlint:
Format all files** command.

### YAML

Install **YAML** by redhat. This helps validate YAML files such as
`_data/navigation.yml` and `_data/committee.yml`.

### Prettier

Install **Prettier - Code formatter** by Prettier. It helps keep HTML, CSS,
JavaScript, and Markdown consistent. You can use **Format Document** from the
Command Palette or enable format-on-save.

### Code Spell Checker

Install **Code Spell Checker** by streetsidesoftware. It helps catch typos in
content and documentation.

### Jekyll and Liquid support

The repository does not currently include a dedicated Jekyll extension.
Instead, use the Jekyll build and the Markdown, YAML, and HTML extensions above.
The Jekyll compiler can still be run from the terminal.

### Recommended optional extensions

- **-files: GitHub** for repository file links and interactions.
- **Files: Explorer** for selecting files from the workspace.
- **Better Comments** for colour-coded comments.
- **Live Server** for a simple local static preview, although this project should
  use the Jekyll build and local server command because it depends on Liquid and
  generated site assets.

You can install all of the extensions from the Extensions view by searching for
the names above. The editor will often suggest installing an extension when you
open a file type or use a feature.

## 7. Connect Visual Studio Code to GitHub

### Sign in to GitHub from Visual Studio Code

1. Open Visual Studio Code.
2. Open the Command Palette with **Ctrl+Shift+P**.
3. Run **GitHub: Sign in**.
4. Enter the GitHub account that owns or has access to the repository.
5. Complete any two-factor authentication or browser approval steps.
6. Confirm that the account appears in the Source Control view.

### Sign in to the GitHub extension

1. Open the Extensions view.
2. Search for **GitHub Pull Requests and Issues**.
3. Select the extension and choose **Sign in**.
4. Select the correct GitHub organisation or personal account.
5. If prompted, authorize the extension and allow it to use GitHub.

### Connect a repository

If you are already using a local repository, follow these steps:

1. Open the repository folder in Visual Studio Code.
2. Open the Source Control view.
3. Select **Initialize Repository** if the folder is not already a Git repository.
4. If the repository is already initialized, you can use the Source Control view
   to create a branch and make commits.

If you have not downloaded the repository yet, clone it from GitHub:

```powershell
git clone https://github.com/AndrewRLogan/bcca-website.git
cd REPOSITORY
code .
```

## 8. Apply to contribute and clone the website repository

The repository must already exist and the project owner must grant you contributor
access before you can push changes.

1. Apply to become a contributor using the repository owner's approved process.
2. Wait until your GitHub account has been granted access to the repository.
3. Sign in to GitHub with the account that has contributor access.
4. Open the repository and confirm that you can push to the repository or create
   branches from it.
5. Clone the existing repository locally:

```powershell
git clone https://github.com/AndrewRLogan/bcca-website.git
cd bcca-website
code .
```

6. Confirm the remote is the repository you were granted access to:

```powershell
git remote -v
```

7. Create a descriptive branch from the appropriate main branch:

```powershell
git switch main
git pull origin main
git switch -c your-branch-name
```

Use a branch name that describes your work, such as `update-home-page` or
`add-committee-profile`.

## 9. Install Ruby and Bundler

The site is configured with Jekyll 4.4 and Gemfile-based plugins. Ruby is the
runtime used to build the site locally.

### Windows installation with RubyInstaller

1. Download RubyInstaller from <https://rubyinstaller.org/>.
2. Run the installer.
3. Choose a recent Ruby version supported by the project's gems.
4. Add Ruby and Bundler to your PATH.
5. Restart the terminal after installation.
6. Verify Ruby:

```powershell
ruby -v
```

7. Verify Bundler:

```powershell
bundle -v
```

If `bundle` is not available, install it:

```powershell
gem install bundler
```

### If Ruby resolves to the wrong installation

The current project instructions mention a common Windows problem where `ruby`
resolves to an application-controlled Ruby installation, often under
`C:\Program Files`. This can cause permission errors while installing gems.

First check where Ruby is being resolved:

```powershell
Get-Command ruby
ruby -v
```

If Ruby is not from the installation you want, place your Ruby installation
first on the current PowerShell PATH. For example:

```powershell
$env:Path = "C:\Ruby40-x64\bin;$env:Path"
```

Replace the path with the actual version installed on your computer. Then verify:

```powershell
ruby -v
bundle -v
```

Only change the current terminal's PATH if you do not want this setting to apply
across sessions. You can also add the Ruby installation directory permanently
through the Windows environment editor after verifying the path.

## 10. Install the project dependencies

Open the project folder in Visual Studio Code. Then run the following commands
in the integrated PowerShell terminal:

```powershell
gem install bundler
bundle install
```

The `bundle install` command reads the `Gemfile` and installs the Jekyll and
plugin dependencies required by the site.

If Bundler reports that a gem cannot be installed, run the following commands:

```powershell
gem update --system
bundle update
```

If you see a permission error, confirm that the Ruby executable used by the
terminal is the Ruby installation you installed, then rerun the command.

Do not commit the generated `vendor`, `node_modules`, or local Ruby gem caches.
The project already excludes `vendor` and `Gemfile.lock` in `_config.yml`, but
other local environment files should also be ignored.

## 11. Build and preview the website locally

The site uses a Jekyll layout and `_data` files. The local server should be
started from the repository root.

### Run the site with the recommended command

From the integrated terminal, run:

```powershell
bundle exec jekyll serve --livereload
```

Open:

```text
http://127.0.0.1:4000/
```

Jekyll rebuilds the site when its source files change. The `--livereload`
option reloads the browser when files are changed.

### Run the site from a VS Code task

1. Open the Command Palette with **Ctrl+Shift+P**.
2. Run **Tasks: Run Task**.
3. Select **Serve site locally** if the repository has a task configured.
4. If the task is not listed, create a task or run the command manually from the
   integrated terminal.

The current repository should contain a task configuration before this option
appears. If the task does not exist, you can add one to `.vscode/tasks.json`.

### Run a one-time build without serving

```powershell
bundle exec jekyll build
```

The generated site is written to `_site/`. The `_site/` folder is normally
ignored by Git, and the README describes this folder as a local preview output.

## 12. Understand the website structure

The site is organized around the following files and folders:

- `index.html` — the home page.
- `about.html` — the about page.
- `contact.html` — the contact page.
- `support.html` — the support page.
- `_layouts/default.html` — the common page layout.
- `_includes/header.html` — the shared header.
- `_includes/footer.html` — the shared footer.
- `_data/navigation.yml` — the main navigation links.
- `_data/committee.yml` — committee member details.
- `assets/css/style.css` — the main site stylesheet.
- `assets/img/` — images used by the site.
- `_config.yml` — Jekyll site settings and excluded files.
- `Gemfile` — Ruby dependencies.
- `CNAME` — the custom domain used for GitHub Pages.

The page files use Jekyll front matter. For example, the home page begins with:

```yaml
---
layout: default
title: Home
hide_title: true
---
```

The YAML front matter controls how Jekyll processes the page. The `layout`
setting selects the shared layout, while `title` and `hide_title` control the
page heading.

## 13. Use the content data files

### Navigation

Edit `_data/navigation.yml` to change the navigation labels and URLs. The file
currently contains a list of navigation entries with `title` and `url` fields.

Example:

```yaml
- title: About Us
  url: /about/
```

### Committee members

Edit `_data/committee.yml` to change committee member names, roles, images, and
blurbs. Each member should include the `name`, `role`, `image`, and `blurb` fields.

Example:

```yaml
- name: "Jane Doe"
  role: "Committee Member"
  image: "/assets/img/committee/jane-doe.png"
  blurb: "A short description of the committee member."
```

Make sure that an image path is valid and that the image exists under
`assets/img/committee/`.

### Site title and metadata

Edit `_config.yml` for global site settings such as the site title, description,
email, and URL. The file includes the Jekyll site settings used by the website.

## 14. Edit and preview changes

1. Open the relevant page or data file in Visual Studio Code.
2. Make the change.
3. Save the file with **Ctrl+S**.
4. Check the editor's Errors screen for HTML, YAML, CSS, or Markdown problems.
5. Run the local site preview if you need to inspect the rendered page:

```powershell
bundle exec jekyll serve --livereload
```

6. Open the local site in a browser.
7. Test the page, links, images, navigation, and content on desktop and mobile
   widths.
8. Run a full build before pushing:

```powershell
bundle exec jekyll build
```

9. Review the generated files in `_site/` if needed, but do not commit generated
   output unless the project specifically requires it.

## 15. Use Git and GitHub for changes

### Create a branch

From the repository root, run:

```powershell
git status
git switch -c your-branch-name
```

Use a descriptive branch name, such as `update-home-page` or
`add-committee-profile`.

### Review changes

```powershell
git diff
git diff --stat
```

Review every change before committing. If you used Copilot to generate content,
verify accurate names, URLs, spelling, accessibility, and page behavior.

### Commit changes

```powershell
git add .
git commit -m "Describe the change"
```

The `git add .` command stages all changes in the current repository. If you only
want to commit selected files, replace the period with the specific paths.

### Push the branch

```powershell
git push -u origin your-branch-name
```

The `origin` remote must point to the repository where you have contributor
access. If it does not, update the remote before pushing.

### Open a pull request

1. Sign in to GitHub.
2. Open the BCCA website repository.
3. Select **Compare & pull request**.
4. Choose the branch you changed.
5. Select **Create pull request**.
6. Add a clear title and description.
7. Use the pull request to explain what changed and how it was tested.

## 16. Publish the site with GitHub Pages

This repository is described as a GitHub Pages site. The build is normally
performed by GitHub rather than by your local computer.

1. Open the repository on GitHub.
2. Select **Settings → Pages**.
3. Choose the source branch used for the site.
4. Select the branch and folder expected by the repository, commonly `main` and
   `/` or `/docs`.
5. Select **Save**.
6. Confirm that the repository contains a `CNAME` file with the public domain if
   the site uses a custom domain.
7. Push the branch to GitHub.
8. Wait for GitHub Pages to build the site.
9. Open the public URL shown in the Pages settings.

If the repository has no GitHub Pages configuration, use the repository's
existing settings or ask the project owner for the required branch and domain
configuration. Do not rename or move the generated `_site/` folder as a
substitute for configuring GitHub Pages.

## 17. Configure the GitHub account and repository settings

For a personal development workflow, make sure that:

- Your GitHub account has a verified email address.
- GitHub Copilot is enabled for the correct account.
- The repository is public or private as intended.
- The default branch is named `main` or the branch that your workflows expect.
- Your GitHub account has permission to push to the repository.
- The remote URL points to the correct repository.

Check the repository remote:

```powershell
git remote -v
```

If the remote is wrong, remove and add the correct repository URL:

```powershell
git remote remove origin
git remote add origin https://github.com/AndrewRLogan/bcca-website.git
```

Use the exact repository URL granted to you, and confirm that your account has
permission to push to the repository.

## 18. Troubleshooting

### `code` is not recognized

Open Visual Studio Code and run **Shell Command: Install 'code' command in
PATH** from the Command Palette. Restart PowerShell, then run:

```powershell
code --version
```

### Git is not recognized

Install Git for Windows, restart the terminal, and run:

```powershell
git --version
```

If Git still does not work, search the installed Git location and add its `bin`
folder to the PATH.

### Copilot does not appear

1. Confirm that you signed in to the correct GitHub account.
2. Confirm that your account has an eligible Copilot plan.
3. Confirm that your organisation has enabled Copilot.
4. Restart Visual Studio Code.
5. Run **GitHub Copilot: Sign in** from the Command Palette.
6. Open the GitHub Copilot settings and verify the account and plan.

### Ruby or Bundler is not recognized

Check `ruby -v` and `bundle -v`. If Ruby is from the wrong application, move a
recent Ruby installation to the front of the PATH as described above.

### `bundle install` fails

Run:

```powershell
ruby -v
bundle -v
Get-Command ruby
Get-Command bundle
```

Confirm that Ruby and Bundler come from the same installation. Then rerun:

```powershell
bundle install
```

If the project uses a newer Ruby version than the installed version supports,
install a newer Ruby version before running Bundler again.

### Jekyll cannot find a page or image

Check the file path and use the project-relative path. For example, an image in
`assets/img/committee/` should be referenced with a path beginning at the site root:

```html
<img src="/assets/img/committee/cara.png" alt="Cara">
```

Jekyll links and assets can use Bash or Liquid expressions in the existing
project. Use `relative_url` for site root paths when the page is rendered under a
subpath or custom domain.

### The site does not refresh after file changes

Stop the existing server and start it again:

```powershell
bundle exec jekyll serve --livereload
```

Then open <http://127.0.0.1:4000/>. If the terminal is still running, use
**Ctrl+C** to stop it before starting a new server.

### GitHub Pages shows an error

- Confirm that the site is built from the correct branch.
- Confirm that the source folder is correct.
- Confirm that the repository is compatible with GitHub Pages.
- Check the GitHub Pages build log.
- Re-run `bundle exec jekyll build` locally to catch Jekyll errors first.

## 19. Recommended development routine

For each change:

1. Open the repository in Visual Studio Code.
2. Sign in to GitHub and Copilot.
3. Create a branch for the work.
4. Edit the relevant HTML, CSS, YAML, or Markdown file.
5. Use Copilot for explanation or suggestions, but review all output.
6. Validate files with the editor's Errors view.
7. Run the local Jekyll preview.
8. Test important pages and links.
9. Run `bundle exec jekyll build`.
10. Commit and push the changes.
11. Open a pull request or publish through the expected GitHub Pages workflow.

## 20. A quick checklist

Before starting to build the website, verify that you can complete all of these
items:

- [ ] GitHub account created and email verified.
- [ ] GitHub Copilot plan enabled.
- [ ] Visual Studio Code installed and `code --version` works.
- [ ] Git installed and `git --version` works.
- [ ] Git identity configured.
- [ ] GitHub Copilot and GitHub Pull Requests extensions installed.
- [ ] Visual Studio Code connected to the correct GitHub account.
- [ ] The repository cloned or opened in Visual Studio Code.
- [ ] Ruby and Bundler installed.
- [ ] `bundle install` completed.
- [ ] `bundle exec jekyll serve --livereload` starts successfully.
- [ ] The site opens at <http://127.0.0.1:4000/>.
- [ ] The repository is ready to push changes to GitHub.
