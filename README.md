<h1 align="center">GitHub Dependency Checker/Updater for Flutter Projects</h1>

<p align="center">

<img src="https://img.shields.io/badge/made%20by-TaylorHo-blue.svg" >

<img src="https://badges.frapsoft.com/os/v1/open-source.svg?v=103" >

<img src="https://img.shields.io/github/stars/TaylorHo/flutter-package-update-checker.svg?style=flat">

<img src="https://img.shields.io/github/languages/top/TaylorHo/flutter-package-update-checker.svg">

<img src="https://img.shields.io/github/issues/TaylorHo/flutter-package-update-checker.svg">

<img src="https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat">
</p>

<p align="center">
  <i>Verify periodically by updates in your <a href="https://pub.dev/">Flutter Packages</a>.</i><br/>
  Dependencies up-to-date is safer 😁
</p>

&nbsp;
&nbsp;

---
# About

The file [dependency_checker.yml](https://github.com/TaylorHo/flutter-package-update-checker/blob/main/dependency_checker.yml) defines an [GitHub Action](https://github.com/features/actions) to **verify if there's package updates into your Flutter Project**.
If there's a package out-of-date, the action will create a **Pull Request** updating the package.

A dependency tree up-to-date is a best practice for security issues 😌


# Installing

### First Step:
Place the [dependency_checker.yml](https://github.com/TaylorHo/flutter-package-update-checker/blob/main/dependency_checker.yml) file into folder ```.github/workflows/``` (you may need to create one) - if you want to understand why, [read it](https://docs.github.com/en/actions/using-workflows).
The structure will look like this:

```
project
|
└── .github
    └── workflows
        └── dependency_checker.yml
```

### Second Step:

You'll need to create a [PAT (Personal Access Token)](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token). To do this, follow the GitHub official tutorial, remembering thoose things:

1. Give Read/Write access to the token when creating
2. The token name can be anything you want
3. Save the generated token in a safe place, you'll need it later

### Third Step:

First, go to your ![Project/Repository settings](/images/settings.png "Repository Settings"), into *"Security" area*, select the *"Actions"* item.
Then, click in *"New Repository Secret"* button in top of the page.
The name of the secret must be **"ACCESS_TOKEN"** (without quotation marks) and his value must be the generated PAT (created in [step 2](#second-step)).

### You're done!

---

# Notes:

The action will be executed once a day, at 12:00 AM UTC 🕒
You can update this value as you need, changing the schedule cron in the [dependency_checker.yml](https://github.com/TaylorHo/flutter-package-update-checker/blob/main/dependency_checker.yml) file.

To do this, you need to change the *"cron"* value in this part of the script. You can use the [Cronitor Crontab](https://crontab.guru/) to create a custom schedule, as needed by you.
```
on:
  workflow_dispatch:
  schedule:
    - cron: "0 0 * * *"
```