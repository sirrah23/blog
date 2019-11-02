# The Blog

## Description

In this repository you'll find the code that generates my blog. This blog exists
thanks to [gatsby](https://www.gatsbyjs.org/) and the
[gatsby-starter-blog](https://www.gatsbyjs.org/starters/gatsbyjs/gatsby-starter-blog/).

## Instructions

### How to create a new blog post

1. Create a new subdirectory in `./content` for your blog post
2. Create an `index.md` file in the subdirectory and start typing away
3. Throw any other assets (images, etc.) into the subdirectory and reference them
   as needed

Note: Remember to fill in the metadata (title, timestamp, etc.) for the blog
post at the top of the `md` file.
 
### Commands

* `npm run start` - Start up a local instance of your blog
* `npm run build` - Build your blog such that it can be served via static files
  (similar to how it will be served in "production")
* `npm run serve` - Serve the most recent result of whatever was created by the
  `npm run build` command (remember to hard-refresh your browser, otherwise you
  may see stale, cached content)
* `npm run deploy` - Ship the blog off to production [(Github
  pages)](https://sirrah23.github.i)