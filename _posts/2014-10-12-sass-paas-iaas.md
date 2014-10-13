---
layout: post
title:  "What's Saas, Paas, Iaas?"
date:   2014-10-12 20:05:00
categories: programming
---

**Preface:**

For a while now, I've been wondering how can I host a web application with the freedom to customize my system however I want (like when I develop on my Mac). Shared host are definitely not working. They do provide many of the popular apps like PHP, Ruby, Python, etc. But they lack the ability to switch versions or add add-ons and plug-ins. So shared hosting ends up being very limited.

I've been researching for a while on something relative simple and cheap for me to host my apps and what not. Very quickly, I learned about Amazon Web Services (AWS). But it was very intimidating, with so many services and products that I have no idea what they do. I thought I was looking for a service/product that can be managed similarly to a shared host, but with more power in managing the installed applications. Researching more, I learned about a few more cloud hosts, where I learned about Saas (something I've heard many times before), Paas, and Iaas. Though, I'm still very confused, I think I have a better understanding of the kind of services I'm looking for.

#### Saas ####

Saas stands for "Software as a Service". It is a software that is being offered. Gmail is a Saas. It is a software that companies use to manage email. Client does not need to worry about how the emails are stored or retrieved. Administrator can edit options and add users, but that is all done within the software. The software itself is managed by the service provider, the service that the software runs on is managed by the provider. Essentially, the software is externally managed. Client does not (and cannot) need to manage the software in anyway.

For example, a content management system build on Ruby and Rails in a CentOS server. The content management system is what the client sees, and they can only see that. Anything to do with Ruby or Rails version updates, updating databases, server load, firewall, etc are all handled by the provider.

#### Paas ####

Paas stands for "Platform as a Service". It is a platform. A place where a developer can build applications. As it is a platform, there is no "software". It is much like a framework where the developer can focus on developing the application. Much of the server managing like load balance, OS, storage, etc are done by the provider. Developer using Paas build applications on middleware, like Ruby or Java. And the applications they develop sort of become a Saas if offered to clients.

In the previous content management system, the developer would be building the content management system on Rails. They would worry about Ruby and Rails version that the application needs, and they would update the database as required. While server related activities are still handled by the provider.

#### Iaas ####

Iaas stands for "Infrastructure as a Service". It is like buying servers, but without actually having servers. Difference between Iaas and having dedicated servers is that Iaas is charged based on usage. The more you use (storage, database, bandwidth), the more you pay. Dedicated servers are pretty predictable in their rates. Using Iaas, you become the server administrator. You can change literally everything about the server. You can put more resources into database, or toughen up on the firewall. Though, cloud related virtualization and storage are still managed by the provider. Having this much power also means that if something does go wrong, you have to access the server and figure out what's causing the problem.

Iaas would represent the actual server that the Rails application runs on in the content management system example. "Nothing" (cloud system is managed by the provider) is managed by the provider, and everything is managed by you. The server, the application, and the content.

#### Conclusion? ####

So I guess I'm looking at a Paas system. I definitely not looking for Saas, and I don't want to be a server administrator. So time to find a Paas service provider.


References:

[apprenda](http://apprenda.com/library/paas/iaas-paas-saas-explained-compared/) <br />
[rackspace](http://www.rackspace.com/knowledge_center/whitepaper/understanding-the-cloud-computing-stack-saas-paas-iaas)