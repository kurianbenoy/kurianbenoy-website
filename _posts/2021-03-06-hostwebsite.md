---
title: Hosting my website with Github pages
type: post
readtime: true
---

Disclaimer: This may not just be the first blog post on this topic, but this is going you not just to host your website, but also on how does web hosting working and the why part which will delve a bit into some theoretical portions like DNS.

I am discussing in this article how to host a self domain with GitHub:

Buy a domain name. I got mine from bigrock.in, while there are sites like google domains, hover, GoDaddy etc. My domain name cost about Rs 900+ after taxes like GST. If you are using a name with more than 5 characters a suffix like .com, .in etc. you will surely get a domain name in that price range. If the name is short, you may need to pay more and I have seen prices go up to Rs 6000 for a short domain name.



Create a repository with GitHub pages with the name: username.github.io. By default without a domain name, your default domain name is username.github.io. I used [Beautiful Jekyll theme](https://github.com/daattali/beautiful-jekyll) for building my blogging website. If you have a custom name, Enter your custom domain name in GitHub pages, and enforce HTTPS for our custom domain. Thanks to [Lets Encrypt which is providing free SSL/TLS Certificates](https://letsencrypt.org/). This process will create a CNAME record in your repository.


3. Create an A record and CNAME in your DNS management system in your domain name and set the associated values. Check the below link for settings - [Configuring a custom domain for your GitHub Pages site - GitHub Docs](https://docs.github.com/en/github/working-with-github-pages/managing-a-custom-domain-for-your-github-pages-site)
4. Tada, your site is hosted like mine - https://kurianbenoy.com/
