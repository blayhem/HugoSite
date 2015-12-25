+++
date = "2015-12-25T17:24:01+01:00"
description = ""
title = "Under Construction"
draft = false
+++

# Building this blog from scratch.

First of all I am assuming you are reading this from an O.S. with a good terminal ~~not the Microsoft shitty attempt~~, that is, OS X or Linux.

Although I used my mac for the creation of this site, I am sure that most of the tools can be used from Linux. There is also a version of Hugo [for Windows](https://github.com/spf13/hugo/releases).
Now, the very first thing I did was to use [Homebrew](http://brew.sh) in [iTerm](https://www.iterm2.com), as 

```
brew install hugo
```

Then, we need to order Hugo to **create a site for us**, by typing

``` bash
$ hugo new site PATH-TO-SITE
```

Because I wanted all my work on Github, I did 'hugo new ~/Github/HugoSite'. There, if we 'cd' the directory we can find several folders and files.

```
dfr-MBP 🍕:HugoSite$ ls
archetypes	content		layouts		static
config.toml	data		public		themes
```

### Creation time!

If you want an **'about'** page for your blog, you have to write the command that you will be using **for creating every single post**:

```
$ hugo new about.md
```

Now you can use VIM, ~~emacs,~~ gedit, atom, or whatever text editor to edit your about page, with some information about the website, abour yourself...

The metadata of the file is between the '+++' signs. Below that, you can start writing anything in markdown, then hugo will craft a beautiful *about* page from it.

Next step is **chosing a theme for your site**. You have to clone the themes repository and chose one for your blog. Do

```
$ git clone --depth 1 --recursive https://github.com/spf13/hugoThemes.git themes
```

Now, for rendering your site you have to write

```bash
$ hugo server --theme=themename -D
```

Where -D stands for *'--buildDrafts'*, or **preview your blog entries as if they were already posted**. If you have 'draft = true' in your post, it will not be published unless you add that flag. To undraft it, however, you only have to write

```
$ hugo undraft content/post/POST-TITLE.md
```

Now, every time you update your posts, you can have **hugo server** running, and the site will automatically load the changes on *localhost*.

### Final touches and publishing.

Once you have decided your theme, you have to edit the file **config.toml** in the root directory of your website. 
This file has special parameters and metadata, which are crucial for the building process. 
Each theme has a set of particular parameters, I recommend to read your theme's README to see which requirements does it have.
For example, this is part of the requirements needed for my theme, *'cactus'*:

```
# Site settings
baseurl = "http://replace-this-with-your-domain.com/"
languageCode = "en-us"
title = "Hugo Cactus Theme"
theme = "hugo-cactus-theme"
# Enter your tracking code to enable Google Analytics
googleAnalytics = ""
# Disable comments by leaving disqusShortname empty
disqusShortname = "spf13"

[params]
	name = "Mr. Hugo"
	description = "Describe your website"
	bio = "Blogger - Programmer - Gopher"
	# Enter optionally your twitter account
	twitter = "Your Twitter account"'
	enableRSS = true
```

It is important to notice that, if we specify a theme in the **config.toml** file, we do not need to write the '--theme=asdf' flag when typing '$ hugo server'. In fact, after specifying a theme and undrafting all the posts, we only need to write **'$ hugo server'** to preview our site, and

```
$ hugo
```

to publish it in the /public directory!
 
The last thing you have to do now is to **put all the files** inside that folder **into your hosting platform**.
In my case, as I already had a [Hubpress](http://hubpress.io) project running, I only substituted the files in my Github/Hubpress repo with the Hugo ones.

#### Et voilà!
