# 🐱 VPM Project template for VRChat World

My template for the VPM project (for VRChat worlds creation)

## 💭 Difference from original template

- Added some linters e.g. CSpell, EditorConfig, Markdownlint
- Added some actions e.g. CodeQL, CodeRabbit.AI, Dependabot
- Auto invoke the VPM registry update when the package is updated
- Improved a deployment process with GPG signing
- Improved a GitHub Actions for testing and building
- Improved the git attributes and ignore files
- and more...

## ▶ Getting Started

This template is built with Unity **2022.3.22f1**. Make sure your project
uses this version or later when opening the project.

### 1. Import the registry via the VRChat Creator Companion (VCC)

Visit the **[VPM Catalogue page](https://kurone-kito.github.io/vpm/)** and
click on the **Add to VCC** button.

### 2. Import the package to your project

1. Click on the "Manage Project" button in the VCC
2. Find the "VRChat Example Package" package and click on the
   "(+) Add package" button

### 3. Use the package, enjoy :D

## 🛠 Using `git vrc` Filter

This project uses a custom git filter named `git vrc` to normalize Unity
files such as `.asset`, `.prefab`, and `.unity`. The filter removes
unstable data so diffs stay readable and merges remain smooth.

### Install and configure

#### 1. Install the `git-vrc` package

```sh
cargo install --locked --git 'https://github.com/anatawa12/git-vrc.git'
git vrc install --config --global
```

#### 2. Make the `.gitconfig` file available for referencing from local `.git/config`

```sh
git config include.path '../.gitconfig'
```

The `.gitattributes` file in this repository already applies the filter to
Unity YAML files.

## 🤖 Setting up the Automation

Create a repository variable with the name and value described below.
For details on how to create repository variables, see
[Creating Configuration Variables for a Repository](https://docs.github.com/en/actions/learn-github-actions/variables#creating-configuration-variables-for-a-repository).
Make sure you are creating a **repository variable**, and not a
**repository secret**.

- `PACKAGE_NAME`: the name of your package, like `com.vrchat.demo-template`.
  1. Open your GitHub repository and go to **Settings**.
  2. Select **Variables** and then **Actions** from the sidebar.
  3. Click **New repository variable**.
  4. Enter the following values and press **Add variable** to save.
     - **Name**: `PACKAGE_NAME`
     - **Value**: the name of your package, like `com.vrchat.demo-template`.

Workflows triggered by `pull_request` events also read this variable. Pull
requests from forks do not have access to repository variables, so the CI
may fail unless the pull request originates from a branch in the same
repository.

Finally, go to the "Settings" page for your repo, then choose "Pages", and
look for the heading "Build and deployment". Change the "Source" dropdown
from "Deploy from a branch" to "GitHub Actions".

That's it!
Some other notes:

- We highly recommend you keep the existing folder structure of this
  template.
  - The root of the project should be a Unity project.
  - Your packages should be in the "Packages" directory.
  - If you deviate from this folder structure, you'll need to update the
    paths that assume your package is in the "Packages" directory on lines
    24, 38, 41 and 57.
- If you want to store and generate your web files in a folder other than
  "Website" in the root, edit the `listPublishDirectory` value in
  [.github/workflows/build-listing.yml](.github/workflows/build-listing.yml).

## Contributing

Welcome to contribute to this repository! For more details,
please refer to [CONTRIBUTING.md](.github/CONTRIBUTING.md).

## License

This repository is licensed under the [MIT License](LICENSE).
