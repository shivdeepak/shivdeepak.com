+++
title = 'Moving from Wordpress to Hugo'
type = "post"
date = 2024-07-19T11:21:24-07:00
draft = false
+++

Today, I am moving my blog from Wordpress to [Hugo](https://gohugo.io/).

The main reason for this move is simplicity, and fast load times.

I have described my Wordpress setup in a [previous post](https://shivdeepak.com/its-so-easy-to-host-a-blog-today-2020). It has too many moving parts, and I am quite surprised that nothing broke yet.

But, every now and then the website goes down because someone is running a bot against it to scan for vulnerabilities.

Although, I tried to mitigate much of it with Cloudflare, but that's not enough, and there are way too many requests for my tiny wordpress server.

Great thing about Hugo is it generates static HTML/CSS files, which means you are hosting static files, and are not generating it dynamically at request time. Which makes this setup blazing fast, and very easy to host.

I am a big fan of serverless because it takes away the maintainance burden from the admin. I have used Github pages, Cloudflare Pages and Vercel in the past.

But this time I am going to use Netlify, because I have heard many good things about it. Mainly, it can handle redirects, which I am planning to leverage to do SEO redirects.

The Wordpress setup lasted for 4 years. Let's see how long Hugo will last. :)
