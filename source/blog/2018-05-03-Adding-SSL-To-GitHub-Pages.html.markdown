---
title: "Adding and enforcing SSL / HTTPS  to Your Custom Domain Github Pages for free"
date: '2018-05-03'
category: blog
blog: blog
tags:
- blog
---

My dayjob involves writing a lot of backend code, and I have written most of the code used on this website. I host it on GitHub Pages with a custom domain. Until May 1, I could not use HTTPS on here. It wasn't such a con when I first started this, but Google now prioritizes SSL encrypted sites and gives big huge warnings on many browsers about forms on non-HTTPS sites. So this meant either using something like CloudFlare CDN or moving to something like Netlify. As I am sure you understand, this site is mostly held together with shoestring and paperclips and do you think I want to spend a day sorting through DNS records for a domain I haven't touched in...a long time?
 
 But GitHub has announced you can now have HTTPS enforced on custom domains! However, getting it to work took the better part of a very late night. Their docs on it aren't very clear. It should be straightforward as clicking "Enforce HTTPS" in the repo settings for repos and pages made after today, but if you have an older one you want to turn HTTPS on for, follow this guide!
 
 1.) Go to the settings for the repo you are using. There's a gear symbol, and clicking on it should take you there. Towards the middle is the settings for GitHub Pages. There's a form input called "Custom Domain." This should be where you've already entered your custom domain. You want to delete it. Yes, delete it. Empty the text field and hit "Save". I know, scary. Don't worry, we will add it back later.
 
 2.) Right below that is a checkbox labeled "Enforce HTTPS". It will have been grayed out and unclickable before you deleted the custom domain. Now that it isn't, check the box!
 
 3.) The fancy new HTTPS comes with new IP addresses. So you want to go to your DNS provider and update the IPs. The old ones still work, but you can't get a cool SSL cert with them. I tried. [You can find the new IP addresses here](https://help.github.com/articles/setting-up-an-apex-domain/#configuring-a-records-with-your-dns-provider). Make sure to add them all as `A` with a host name of `@`. 
 
 4.) Wait. You're gonna be waiting a bit. You are waiting for two things: a.) Your GH Page to get an SSL certificate, b.) the new IP addresses in your DNS to propagate. I periodically checked with a DNS propagation tracker and when a decent amount of them had the new IP addresses, I moved on to the next step.
 
 5.) Add back in your custom domain on your GH Pages settings and hit 'save'. If everything worked, the "Enforce HTTPS" setting should remain checked! If something is wrong, you might get the error "Not yet available for your site because the certificate has not finished being issued." This error means you didn't wait long enough for GH to create your SSL cert. Delete the custom domain and wait some more. If it goes back to being grayed out, it means you didn't wait long enough for the new IPs to propagate. Delete the custom domain from your GH pages and wait some more.
 
 That's it! 