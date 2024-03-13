> [!CAUTION]
> This Theme is under development

# BlogTheme for Automad

This is a simple Bootstrap based theme with 3 layouts and an optional sidebar. This theme has a light and a dark mode. 

---

- [Included Layouts](#included-templates)
    - [Page]()
    - [Post]()
    - [Blog]()
    - [Settings Navbar]()
- [Light/Dark mode](#development-workflow)
- [Cheat Sheets](#cheat-sheets)

## Included Templates

This package contains these simplified templates that only serve demonstrational purposes:

1. The `page.php` template represents a basic page with a navbar, a content area and a sidebar with menu.
2. The `post.php` template contains a filterable and sortable pagelist that can be used as a skeleton for blogs or portfolios.
3. The `blog.php`template demonstrates the usage of session variables and the `set` function.

Also included is a navbar with some options

> ☝️ To see those templates in action while playing around just apply them to any page in your installation!

## Development Workflow

This very detailed in-depth guide describes step by step the workflow of setting up and publish a new theme using [Composer](https://getcomposer.org). You can probaly skip some of the points in case you have been working already with Composer in the past.

> ☝️ This guide assumes you're familiar with Visual Code Studio and working on a system with a Bash shell or similar &mdash; like macOS or Linux. However, it is of course possible to do the same on a Windows PC &mdash; just slightly different. 

### The Local Package

1. It's a good practice to start developing a new package outside of the Automad packages directory. Therefore change to some directory outside of Automad where you want to develop your new theme. Let's assume you want to put your package into a directory called `dev` within your home folder.

    ~~~
    cd ~/dev
    ~~~
    
2. Create new skeleton theme in your `dev` directory using Composer.

    ~~~
    composer create-project automad/theme-skeleton my-theme
    ~~~

3. Change to the new theme directory and edit the `composer.json` and `theme.json` files. VS Code is used here as the editor. At least change the vendor and theme name.

    ~~~
    cd my-theme
    code composer.json
    ~~~
    
    Also edit the name in `theme.json`.
    
    ~~~
    code theme.json
    ~~~

4. Now change to your Automad root directory. For example `~/Sites/automad-site`.

    ~~~
    cd ~/Sites/automad-site
    ~~~

5. Edit the `composer.json` file of the Automad installation.
    
    ~~~
    code composer.json
    ~~~

    Add the following snippet to Automad's composer file (note the path to your package).
    
    ~~~
    {
        ...	
        "repositories": [
            {
                "type": "path",
                "url": "~/dev/my-theme"
            }
        ],
        ...
    }
    ~~~

6. Still in the Automad directory run the following Composer command.
    
    ~~~
    composer require my-vendor/my-theme:@dev
    ~~~
    
    Now your theme is available in Automad and you can start developing your templates.
    After all the setup it's now time to create a repository for your theme.


### Create a Git Repository

When developing is done, it's time to publish your work.

1. Init new Git repository and commit files.

    ~~~
    cd ~/dev/my-theme
    git init
    git add .
    git commit -m "First commit"
    ~~~

2. Create a first release tag for your finished theme following the semantic versioning scheme. 

    ~~~
    git tag -a 1.0.0 -m "my version 1.0.0"
    ~~~
    
3. Create a new repository on [GitHub](https://github.com).
4. Now, add its URL as a remote to your local repository and push changes. When creating a repository, the URL will be printed on the GitHub page.

    ~~~
    git remote add origin /remote/URL/of/your/new/repo
    git push -u origin master
    ~~~

### Register Your Package

Now it's time to submit your theme package to [Packagist](https://packagist.org). After succseffuly registering it, it will automatically show up in the package [browser](https://packages.automad.org).


## Cheat Sheets

In case you prefer to start developing a theme or extension without reading the full documention, the [Cheat Sheets](https://automad.org/developer-guide/cheat-sheets) are a good point to start.
