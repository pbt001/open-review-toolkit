# Open Review Toolkit

The [Open Review Toolkit](http://www.openreviewtoolkit.org/) enables you to convert your book manuscript into a website that can be used for Open Review. During the Open Review process everyone can read your manuscript and help make it better, and you can collect valuable feedback to improve the manuscript and help launch your book.

You can view a [sample site](http://sample.openreviewtoolkit.org/) generated by this repository.

## Overview

The Open Review Toolkit contains 1) a template for a book written in Markdown and 2) a virtual machine with all the neccesary open-source software pre-installed.  The template includes a few files that contain the content of the book, a few supporting files (e.g., figures, bibtex files), and a [make file](https://swcarpentry.github.io/make-novice/) that converts your manuscript into either a PDF or a website.  You can drop your book's content into this template, and you can even extend the template's basic structure to suit your needs.  If you follow the same basic structure as the template, then the make file should continue to work.  

The virtual machine includes is basically a standard Linux box pre-installed with the open-source software that is needed to power the make file (e.g., [pandoc](http://pandoc.org/), [LaTeX](https://www.latex-project.org/)).  This virtual machine ensures that the Open Review Toolkit works in the same way on different computers.

Unfortunately, at the moment, the Open Review Toolkit only supports manuscripts in Markdown.  If your book is currently in LaTeX, Word, or some other format, you can convert it to Markdown.  Or, you can contact us.  We're interested in developing the codebase to support LaTeX and Word.

## Getting Started

0. Download and install [Vagrant](https://www.vagrantup.com/).
1. Download the soure code by either cloning the git repository or downloading the [latest release](https://github.com/open-review-toolkit/open-review-toolkit/releases/latest).
2. Once you've cloned the git repository or extracted the release source code, open your favorite terminal and navigate to the directory the holds the source code. You should see several files and directories in this directory, including a file call `Vagrantfile`.
3. From your terminal, run: `vagrant up`. The very first time you run this command it will download roughly 1.5GB of data, so it may take a few minutes or more depending on the speed of your internet connection.
4. Once the previous command has completed, run `vagrant ssh`. You are now inside the Vagrant VM, which includes all the dependencies for the project.
5. `make book` will create a PDF file of the book and place it in the `output/` directory.
6. `make site` will build an Open Review site from the book. After building the site, you can view it in your browser by visiting: http://0.0.0.0:17278/. This link only works on your local machine. See the [Hosting Your Site](#hosting-your-site) section before for how to publish your site publicly.

As you make changes to the Markdown files that contain the content of your book, you will need to re-run the relevant `make` command above in order to re-build the PDF and/or site. Once you're done working with the Vagrant VM, it's a good idea to shut it down with `vagrant halt`. The next time you want to start again, you can run `vagrant up` and `vagrant ssh`.

## Modification Tips

**Reminder:** after you make any improvements to your book (by editing the Markdown files), you'll need to re-run the appropriate `make` command to re-build the PDF or site.

The [sample site](http://sample.openreviewtoolkit.org/) includes some details on how to customize your site.

The Open Review websites are build for to be integrated with [Google Analytics](https://www.google.com/analytics/). In order configure the your Open Review website to use your Google Analytics account, you must update the `ga_code` configuration item in `website/config.rb`.

## Hosting Your Site

After running `make site`, the complete website is available as static HTML pages and assets in the `website/build/` directory. These can be copied over to the web host of your choice. You can also use a static web site host like [GitHub Pages](https://pages.github.com/).
