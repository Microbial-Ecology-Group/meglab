# www.meglab.org

## Overview

The meglab.org site is hosted on [GitHub Pages](https://pages.github.com/) under the "Microbial-Ecology-Group" GitHub account. This Git repository's master branch contains the source code for the website's static content. The repository is configured to automatically build and deploy a new version of the meglab.org site's static content once changes are committed and pushed to the master branch. The site is automatically deployed to the gh-pages branch. The dynamic part of the meglab.org site, the MEGARes database browser, is not a part of this repository. It is hosted as its own Github Page site under the subdomain "db.meglab.org" and in a separate repository located at [github.com/Microbial-Ecology-Group/megares](https://github.com/Microbial-Ecology-Group/megares). See that repository's [README.md](https://github.com/Microbial-Ecology-Group/megares#readme) file for more information.

### Technology stack

This site is built with [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) a static site generator that is based on the [Markdown](https://www.markdownguide.org/) syntax, a simple and easy-to-use markup language you can use to format virtually any document.


### Recommended development setup

Although it is possible to make changes to .md files directly in your browser, using GitHub's markdown editor, setting up a local development environment is recommended as you can preview your changes before you push them to the live site.

1. Install [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) manually or get [GitHub Desktop](https://desktop.github.com/).
1. Download and install mkdocs-material. See the [official instructions](https://squidfunk.github.io/mkdocs-material/getting-started/#installation) or use [Homebrew](https://formulae.brew.sh/formula/mkdocs) (macOS), [Chocolatey](https://community.chocolatey.org/packages/mkdocs-material) (Windows) or with `pip install mkdocs-material`
1. Download and install [Visual Studio Code](https://code.visualstudio.com/)
1. Install the [YAML extension](https://marketplace.visualstudio.com/items?itemName=redhat.vscode-yaml) in Visual Studio Code
1. Clone this repository and checkout its master branch. You should now have the latest version of the site's source code on your computer.
1. Open the cloned repository's root folder in Visual Studio Code.
1. Open a terminal (either in VSCode or separately) and make sure you are inside the root folder of the project. 
1. Run `mkdocs serve` to start a local development server. You can now make changes locally and see the changes reflected automatically in your browser.
1. Once you're happy with your changes, commit (write a short summary of your changes) and push to the master branch. Your changes will be live in a minute or so, after the GitHub actions continuos integration tasks are finished rebuilding and republishing the site.

## How-To Guides

### How to edit Markdown pages
The recommended way of editing markdown pages is to first setup a local development environment, as described above, and then first make changes locally, verify that the changes look as intended, and then push the changes to the repository's master branch - which in turn triggers a rebuild and republish of the site. It is also possible to edit markdown files directly in GitHub's interface, in your browser, but remember that every time you click "Save" a new commit is pushed, which over a period of time could make the history cluttered with lots of small edits. Also, you won't be able to preview your changes. Clicking Save immediately publishes your modifications.

### How to create a new page
To create a new page, simply create a new markdown file (sometitle.md) and save it in the folder structure where it logically belongs. The file and folder structure is organized according to the site's page hierarchy. To add the new page to the navigation, edit the `mkdocs.yml`'s nav part and insert a reference to your page where it fits in the page navigation hierarchy.

### How to create custom pages / override the default design

The [mkdocs-material documentation](https://squidfunk.github.io/mkdocs-material/customization/#overriding-blocks) provides useful information on how to override specific "blocks" and "partials". The root page/landing page of this site is overriding the default design using the techniques described on that page. To create a new "landing page", such as those for ["Home"](https://www.meglab.org/), ["MEGARes"](https://www.meglab.org/megares) and ["AMR++ Pipeline"](https://www.meglab.org/amrplusplus/), follow these steps:

#### Step 1:
Create a new html file in the ./overrides folder with contents in the code snippet below. Insert your custom HTML/CSS where appropriate. You may use any of the other files in the overrides folder as a starting point.

```html
{% extends "main.html" %}
{% block tabs %}
{{ super() }}
<!-- Insert custom HTML/CSS that should be displayed BEFORE the contents in the markdown file, such as a hero banner with logos -->
{% endblock %}

{% block content %}
<div class="center-container">
    <!-- Insert custom HTML/CSS that should be displayed BEFORE the contents in the markdown file, but after the banner part -->
    {{ super() }}
    <!-- Insert custom HTML/CSS that should be displayed AFTER the contents in the markdown file -->
</div>
{% endblock %}

{% block footer %}
<!-- Usually, you don't want to change this part. Anything you put here will be added to the footer of this page -->
<footer class="md-footer">    
  <div class="md-footer-meta md-typeset">
    <div class="md-footer-meta__inner md-grid">
      <div class="md-copyright">
        <div class="md-copyright__highlight">
          © Copyright Microbial Ecology Group.
        </div>  
      </div>      
    </div>
  </div>
</footer>
{% endblock %}
```

#### Step 2:
Create a new markdown file and reference the override html file at the top of the file, like shown below. Write your markdown syntax as you'd normally do below the dotted line.

```
---
template: your-override-file.html
title: Your Title
---
```

#### Step 3:
Save your markdown file and reference it in the `mkdocs.yml`, just as you would with any new markdown page. When you add new html files, or make changes to the html files in the overrides folder, you need to reload the server to see the changes. Stop your server and then re-run `mkdocs serve`. If that doesn't work, try `mkdocs build` before `mkdocs serve`.











