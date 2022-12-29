# Smore 
Smore is a gruvbox theme created for hugo. I use this theme on my personal site but have put it here for anyone to take advantage of! 
![image](https://user-images.githubusercontent.com/19278569/209897243-ec1d1554-40e9-4079-8bb9-62ef40e0d181.png)

![image](https://user-images.githubusercontent.com/19278569/209897278-3b2d2528-59ae-4346-9bc4-1280388f1d07.png)

![image](https://user-images.githubusercontent.com/19278569/209897360-4b2f5cbe-211b-45c9-93d6-6fdc4df78610.png)

I made this template for those looking to quickly spin up a resume site. If you would like to read about why you should have a blog/resume site, you can read my [Post about it](https://grahamhelton.com/blog/infosecblog1/) and my post about [How to set it up](https://grahamhelton.com/blog/infosecblog2/). I will be doing a detailed writeup about how I created this theme soon!
- Site Demo - https://grahamhelton.com

---

## Features
- Simple Gruv-y look 
- Easy to customize and edit
- License and copyright free. Credit me if you use the theme, or don't. Up to you
- Analytic tag support


#### Code highlighting
Adding the following to your config.toml will enable syntax highlighting for your code. You can browse the supported themes [Here](https://github.com/alecthomas/chroma/tree/master/styles)

```bash
[markup]
  [markup.highlight]
   anchorLineNos = false
    codeFences = true
    guessSyntax = false
    hl_Lines = ''
    hl_inline = false
    lineAnchors = ''
    lineNoStart = 1
    lineNos = true 
    lineNumbersInTable = false 
    noClasses = true
    noHl = false
    style = 'gruvbox'
    tabWidth = 4



```
![Pasted image 20221228201622](https://user-images.githubusercontent.com/19278569/209893775-0e62c6fe-501e-4c20-ae5e-61dedf331268.png)



## How to install
You can download the theme by cloning this repository into your themes folder. 

⚠️ The theme was tested using hugo version 0.109. It will likely still work on older versions but some features (such as syntax highlighting) will probably not work. You can check your hugo version by typing `hugo version`.

## Install theme locally
Ensure you are in your root web directory (The one that contains `config.toml`)

```bash
git clone https://github.com/grahamhelton/smore themes/smore
```

This will clone the repository directly to the `themes/smore` directory.

## How to run your site

```bash
hugo server -t smore
```

and go to `localhost:1313` in your browser. From now on all the changes you make will go live, so you don't need to refresh your browser every single time.

## How to configure

The theme doesn't require advanced configuration. Just copy:

```toml
title = "Your_Site_Name"                # Change me!
baseURL = "https://yoursite.com"        # Change me!
relativeURLs = true
theme = "smore"
enableEmoji = true

# Change me if you use google analytics
googleAnalytics = "UA-123456789"        
# Sets the amount of blog posts that appear before creating a new page
paginate = 15

# Set the parameters for your site
[params]
author = "Your Name"
description = "Site Description"
# path to a .ico to use as favicon
favicon = "favicon.ico"  

# Define syntax highlighting
[markup]
  [markup.highlight]
   anchorLineNos = false
    codeFences = true
    guessSyntax = false
    hl_Lines = ''
    hl_inline = false
    lineAnchors = ''
    lineNoStart = 1
    lineNos = true 
    lineNumbersInTable = false 
    noClasses = true
    noHl = false
	# Syntax style. Choose themes from here
    style = 'gruvbox'
    tabWidth = 4
```

to `config.toml` file in your Hugo root directory and change params fields. 

## How to edit the theme <a id="how-to-edit" />

All you need to do is go into `website_root/themes/smore/` then you can directly edit anything in the theme. No compilation step needed.

## Found a bug? 

If you spot any bugs, please use [Issue Tracker](https://github.com/grahamhelton/smore/issues) or create a new [Pull Request](https://github.com/grahamhelton/smore/pulls) to fix the issue.

## Are you using this theme?
I made this theme for myself, but open sourced it so others could use it! I'd love to see your site if you're using this theme. If you are, let me know! I would love to have a list of all the sites using this theme!

## License

Use this however you want. Credit me or don't. Up to you.

## Upcoming Features
- Add sane metatag support
- Zoom in mobile UI. ( I thought it looked fine but others have said it is too small)

## Inspiration
- This theme was HEAVILY inspired by [Researcher](https://github.com/ojroques/hugo-researcher). Some of the CSS from smore is taken from there as well! 
