# Solarwind

Solarwind is the for-reals no-bullshit static site generator.

Static site generators have become confusing and bloated. I've tried 4 or 5 and
they don't make sense, they have terrible defaults, the templates are hard to
understand, yadda yadda nerd rage yadda.

This is a simple and easy to use SSG.

## Installation

You will need Solarwind:

`go get github.com/kyleterry/solarwind`

This shit will show up in your `$GOPATH/bin`.

## Usage

All this assumes your project lives under `~/src/my-site`.

### Configuration
First things first, you will need a `Solarwindfile`. Put this shit `~/src/my-site/Solarwindfile`:

```
{
    "site-title": "My Site Title",
    "site-description: "This is a description that will be in my meta tags"
}
```

It's fucking JSON. How about that?

Now you will need to copy the starter template into your site root:

`cp -r $GOPATH/src/github.com/kyleterry/solarwind/starter/templates ~/src/my-site/`

Now create a content and posts dir:

`mkdir -p ~/src/my-site/content/posts`

### File mappings

Non-markdown files are mapped pretty much 1 to 1 between source and destination,
so if you have a file called `~/src/my-site/content/index.html`, it will be
rendered to `~/src/my-site/public/index.html`.

Markdown post filenames are derived from the title of the post as a slug:
`~/src/my-site/public/posts/my-first-post-title.html`.

Add some html and markdown (use .md extension) to your
`~/src/my-site/content{,posts}` and generate your site:

### Markdown and posts

Posts are markdown files with an optional header describing metadata about the
post. Below is an example of a markdown post:

```markdown
###
title: This is the Post Title
date: 06 Mar 15 13:30 PST
category: computers
###

I have long used computers because they rule.

Here I will write another paragraph about computers.

I use [Google](https://google.com) to figure stuff out.
```

The above text should be stored in something like
`~/my-site/content/posts/my-computer-post.md`.

### Generating the site

`solarwind generate`

All your shit shows up in `~/src/my-site/public`

If you need static assets, just put them in `~/src/my-site/static/{css,js,images}`
or whatever (really, I just copy that entire dir to `~/src/my-site/public/static`).

### Post ordering

Posts are currently ordered based on the filename. I'm going to later add the
ability to sort by post date.

### Development Server

A development server is included. It will watch your content, templates, and
static directories for changes and regenerate the site when they occur.
It optionally takes a -bind param but will listen on localhost:8090 by default.

`solarwind server [-bind :8091]`

Now edit the templates to your liking and draw the rest of the fucking owl.
