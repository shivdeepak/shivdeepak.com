+++
title = 'It’s so easy to host a blog today (2020)'
description = 'Discover why I moved my blog from Posthaven to WordPress for better emoji support and customization. Learn about my seamless setup with WordPress, LetsEncrypt for SSL, and CloudFront for media hosting. Find out how I offloaded media to AWS S3 and set up automated backups with UpdraftPlus. Explore other useful plugins for social sharing, SEO, email subscriptions, and theme customization.'
date = 2020-06-28T09:45:44-07:00
draft = false
type = "post"
aliases = ['its-so-easy-to-host-a-blog-today-2020']
+++

I moved this blog from Posthaven to WordPress as Posthaven has poor support for emojis and supports minimal customizations. And the reason to use WordPress was quite simple; it is the most popular blogging CMS in the world and has a vibrant developer community around it.

Along with WordPress, I used [LetsEncrypt](https://letsencrypt.org/getting-started/) for SSL and [CloudFront](https://aws.amazon.com/cloudfront/) for media hosting. And the setup was super simple and at a very nominal cost.

So, I installed WordPress with Apache Webserver, and LetsEncrypt’s CLI tool [certbot](https://certbot.eff.org/) had the support to read/write apache config files, and the SSL setup was a breeze. I remember spending hours to set up SSL certs not many years back.

I wanted to move the media library out of the server because I did not want to worry about disk space and disk IO. So, I used the [WP Offload Media Lite](https://wordpress.org/plugins/amazon-s3-and-cloudfront/) plugin, which allowed me to move the media library to AWS S3. And, it also has support to add a CDN URL. So, I set up CloudFront with a custom domain, and to my surprise, [the SSL setup](https://deliciousbrains.com/wp-offload-media/doc/custom-domain-https-cloudfront/) was as easy as LetsEncrypt.

Next, backups are essential! And, I assumed that I have to write a cronjob to back up the files and database to AWS S3, but I looked for a plugin first, and I found one. [UpdraftPlus – Backup/Restore](https://wordpress.org/plugins/updraftplus/) has support for automated backups and can backup WordPress files (plugins, themes, uploads, etc.) and database to AWS S3 (and has support for several other cloud storage solutions).

### Other Plugins

Here is a list of few other plugins I found useful:

[Share Buttons by AddThis](https://wordpress.org/plugins/addthis/): A easy way to set up neat social share buttons to your posts.

[Yoast SEO](https://wordpress.org/plugins/wordpress-seo/): This plugin enables seamless meta tags set up for social share cards, such as Facebook, Twitter, and Linkedin. So, a perfect complement to the AddThis plugin.

[Site Kit by Google](https://wordpress.org/plugins/google-site-kit/): Set up Google Analytics, Google Search Console, PageSpeed Insights, Google Tag Manager, Google AdSense, Google Optimize through OAuth. So, No code editing required.

[Email Subscribers & Newsletters](https://wordpress.org/plugins/email-subscribers/): Pretty nifty plugin to set up email subscriptions for your blog. But, it does expect that your site is configured to send emails. However, it wasn’t a big challenge because I was able to quickly set up [WP Offload SES Lite](https://wordpress.org/plugins/email-subscribers/) to send emails using AWS SES.

[WP-CLI](https://wp-cli.org/): Unlike traditional WordPress plugins, WP-CLI is a command-line tool. So, we have to install it on the host server. This tool allows you to install and update plugins and themes from the command line without exposing an FTP server.

### Theme Customization

And finally, the Theme. WordPress came with [TwentyTwenty](https://github.com/WordPress/WordPress/tree/master/wp-content/themes/twentytwenty) as the default theme. It has plenty of customization options and custom CSS support. So, customizing the Theme to my liking didn’t take very long.
