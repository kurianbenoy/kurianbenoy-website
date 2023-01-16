---
title: Hosting your website  🌐 with Github pages
layout: post
categories: [coding, frontend, webdevelopment, hosting]
date: '2021-03-06'
---

*Disclaimer: This may not just be the first blog post on this topic, yet we are not merely talking how to do it only but also why part which will delve a bit into some theoretical portions like DNS, webhosting etc.*

I am discussing in this article how to host a self domain with GitHub:

**Buy a domain name** - I got mine from bigrock.in, while there are sites like google domains, hover, GoDaddy etc. My domain name cost about Rs 900+ after taxes like GST. If you are using a name with more than 5 characters a suffix like .com, .in etc. you will surely get a domain name in that price range. If the name is short, you may need to pay more and I have seen prices go up to Rs 6000 for a short domain name.

![domainname](https://user-images.githubusercontent.com/24592806/110367638-f1b69f00-806d-11eb-9ff8-3290cf08ce3c.png)

**Create a repository with GitHub pages** with the name: username.github.io. By default without a domain name, your default domain name is username.github.io. I used [Beautiful Jekyll theme](https://github.com/daattali/beautiful-jekyll) for building my blogging website. If you have a custom name, Enter your custom domain name in GitHub pages, and enforce HTTPS for our custom domain. Thanks to [Lets Encrypt which is providing free SSL/TLS Certificates](https://letsencrypt.org/). This process will create a CNAME record in your repository.

![githubrepo](https://user-images.githubusercontent.com/24592806/110367702-0dba4080-806e-11eb-9b96-15770a7982ed.png)

![image](https://user-images.githubusercontent.com/24592806/110367923-507c1880-806e-11eb-92e7-3728f5a7f772.png)

**Go to your DNS management system**. In the bigrock, scroll all the way down in your domain name page, and reach the setting for DNS Management

![image](https://user-images.githubusercontent.com/24592806/110369070-d9478400-806f-11eb-8424-9a7f1dc1b7a1.png)

Now on clicking Manage DNS create an A record, which is used to point to four name servers hosted by GitHub. First and
foremost create a CNAME record that points your subdomain to the default domain for your site. For example, if you want to use the subdomain www.example.com for your user site, create a CNAME record that points www.example.com to <user>.github.io
  
![image](https://user-images.githubusercontent.com/24592806/110369506-828e7a00-8070-11eb-9b89-fadd282e0374.png)

**So what is a CNAME record?**

- It's a record type in resource records that allows an alias to be created. It is a macro definition that helps in redirecting, from one website to another. So really we are actually mapping the server of kurianbenoy.github.io to kurianbenoy.com.

The next step is to create an A record in the DNS management system. In docs for [Configuring a custom domain for your GitHub Pages site - GitHub Docs](https://docs.github.com/en/github/working-with-github-pages/managing-a-custom-domain-for-your-github-pages-site), it's mentioned the various IPs used
for creating A records in DNS providing servicer.

![image](https://user-images.githubusercontent.com/24592806/110370904-4a883680-8072-11eb-8af8-231907f1f115.png)


**What is A Record**

- It is used to point your apex domain to the default domain for your site. 
- A record is the most important record type and it holds a 32 bit IP address for some host. Every Internet host must have at least one IP address to communicate with others.


Tada, your site is hosted like mine -[kurianbenoy.com](https://kurianbenoy.com/)

>Now to the theory portion. I also had hosted my domain earlier following the above steps more than once and it simply worked. Yet how it worked and why we needed black box was a big mystery to me, which I am trying to demystify with this article.

**DNS is used to map a specific name into an associated IP address**, an application program called library procedure called a **resolver**. Domain names were initially created specifically for solving the problem in ARPNET to understand which all nodes were there in the system. In those days they used a text file named hosts.txt to keep track of all hostnames and update every night. Yet as time progressed, things started changing for good, and the Domain name system was bought in place.


The domain name system consists of **Top-level domain names** which are managed by ICANN. The various top-level domains are classified into two types:

a) **Generic top-level domain names** - which maps domains that are commonly used all over the world like .com, .net, .org etc. They can be used for any purpose, and the bost TLD by far is .com with more than 100+ million .com domains.


b) **Country-level domain names** - which maps domain names based on the associated country names. Like our country India has .in, various government sites use domains based on it like data.gov.in


A domain name can be mapped to one or more associated servers. So even though when calling google.com, it can be mapped to multiple servers in various locations of the world


Besides these top-level domain names, there are **second-level domains** which is the name which you want to assign for your individual domain name. Also,**subdomains** can be used to map domain names to certain specific or other sites by adding a word followed by a dot. For example, if you want to create a specific blogging website in my domain name - you can easily add:

> blog.kurianbenoy.com


Another interesting thing about domain names is they can only be in ASCII, even though with certain software some certain Unicode words can be used for domain names. The business of **Domain name registries who are accredited with ICANN** sell the various domain names and are responsible for providing basic functionalities like name server for our use case. Domain names are considered like real estates, the shorter and attractive it is. The more money it costs.


The domain name is a component of a uniform resource locator (URL) used to access web sites(this is a common question in computer networks theory class), for example: [4]

URL: http://www.example.net/index.html
Top-level domain: net
Second-level domain: example
Hostname: www

**Resource Records** are associated with a single host or top-level domain names. The real function of DNS is to map domain names into resource records. The resource
records are five-tuple format as follows:

- Domain_name
- Time_to_live
- Class
- Type
- Value

I know it is not a proper ending, just let me know in the comments if I have missed anything. It's always to better to do something than doing nothing.
That's why I am continuing my weekly ramblings even though it's not perfect

~ Kurian Benoy

**📢 Resource alert** I found this awesome cartoon comic which explains [how DNS works](https://howdns.works/episodes/)

### References

1. Github docs
2. how to host your website on GitHub pages-medium
3. Computer Networks, Andrew S Tanenbaum
4. Use in website hosting-Domain Name, Wikipedia
