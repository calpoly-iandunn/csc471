---
layout: page
active: references
title: "Use Git and GitHub Classroom"
auto-title: true
---

There are approximately 1,000,000 tools that can help you learn git.
So far as I know, [this is as good as any](https://try.github.io/).
If you take any issue with this source or have any alternative recommendations, please let me know!

We will be using [GitHub Classroom](https://classroom.github.com/) to turn in assignments this quarter.

After you accept the assignment, you will be able to select a **clone** url.


## Hand-In

Create a git repository by running this command in the directory with your files:

```bash
git init
```

Add your source code and readme to it like this:

```bash
git add src/
git add resources/
git add CMakeLists.txt
git add README.md
git status
git commit -m 'Add my source, build scripts, and readme!'
```

Then, push your git repo to the assignment on GitHub Classroom.

You can accept access to your repository by clicking on the blue button at the top of this page.

You will need to copy either the **HTTPS** or **SSH** clone url for your repository.

**HTTPS** will require your GitHub password every time you try to push.

**SSH** will require that you set up [SSH Keys](https://help.github.com/articles/connecting-to-github-with-ssh/) with your GitHub account,
but will never ask for a password when you push!
I am happy to help you set this up.

Once you have picked and copied the URL for your repository, run this command:

```bash
git remote add origin YOUR_COPIED_URL
git push origin master
```

Then your code should be saved in GitHub Classroom!


### Troubleshooting

If your repository already has a `origin` remote (and you get some sort of error about not being able to add the origin remote), first run this command:

```bash
git remote remote origin
```

And then you should be able to add the `origin` remote as above.
