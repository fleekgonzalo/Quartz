---
title: Set up this Website
draft: 
tags: []
---
This website template was made to be used with the [Obsidian](https://obsidian.md/) note taking application. If you had never heard of Obsidian you should try it, its great. If you want to get into note taking and as the productivity gurus call it, "Building your Second Brain", read this article [Molecular Notes: Principles · Reasonable Deviations](https://reasonabledeviations.com/2022/04/18/molecular-notes-part-1/) and its continuation [Molecular Notes: Practice · Reasonable Deviations](https://reasonabledeviations.com/2022/06/12/molecular-notes-part-2/).

To use this website template for your own blogsite use their [GitHub](https://github.com/jackyzha0/quartz) repository as the template for your own and follow the official [Quartz](https://quartz.jzhao.xyz/) documentation.

# Requirements

- Installed git
- Installed npm
- Installed npx
- [Github](https://github.com/) account
- [Cloudflare](https://www.cloudflare.com/) account
- (Recommended) Domain. You can buy it from a registar like [GoDaddy](https://www.godaddy.com/) or [Namecheap](https://www.namecheap.com/).


# Set up

1. Create a new repo using Quartz as a template.
2. Clone your newly created repo into your computer with `git clone` + the link to your repository.
4. Open the folder in a code editor like VSCode.
5. Open the terminal and run:
	- `npm i`
	- `npx quartz create`

After this you will have your own local respository for your website. One of the folders is called "content" and this is where you should put your Obsidian notes in.

After making changes to your website or blogposts run `npx quartz sync` to apply them.

Lets test that the website works so far. Run `npx quartz build --serve`, wait for the process to complete, then visit `http://localhost:8080/`. If everything is working you should see your website.


# Hosting

Now lets make our website accessible to anyone.

1. Open Cloudflare and add your domain.
2. Create a new Cloudflare Page and link it to your GitHub repository.
3. Set
	- Build command: npx quartz build
	- Build output directory: public
4. Wait for Cloudflare to build your website.
5. Add your custom domain to your website.
6. Go to your domain registar and set the DNS to whatever Cloudflare tells you to.

If everything works correctly your website should be up and running and accessible by visiting your domain in any browser.


# Customization

Changing the icon:
- Go into quartz/quartz/static
- Inside you will find two files, icon.png and og-image.png
- Replace these two files with your preferred icon, which need to use the same names as the previous files
*Note: you might need to hard reset your browser for the new icon to show up*

Changing the name:
- Go into quartz/quartz.config.ts
- Find `pageTitle` and change its value
- Also change `baseUrl` with your domain

Content folder: