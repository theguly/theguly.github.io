---
layout: post
title: "Advanced Web Attack and Exploitation - Offensive Security Web Expert"
description: "Here is my take on Advanced Web Attack and Exploitation course and relative exam for Offensive Security Web Expert""
share: true
tags:
 - courses
 - certifications
 - exploit
---

# Offensive Security - Advanced Web Attack and Exploitation (AWAE)

All Offensive Security fans was waiting for [AWAE](https://www.offensive-security.com/awae-oswe/) to become available online since forever, and finally they announced availability in spring 2019 (and now are waiting for AWE, but that will hopely be another blog).

## Overview

The course prepares students for a whitebox code review, starting from decompilation and debug to find authentication bypass (stealing cookies with XSS and grabbing token with SQL Injection is still auth bypass) and achieve RCE by chaining 2 or more small vulnerabilities.

You are first introduced in source code analysis, what I must say here is that they probably didn't make clear enough that you are not *reading source code*, you are *reviewing source code* to find vulnerabilities.  
The flow is **so different**, and you have to know it because you'll end up reviewing applications with 100k if not millions line of code. And no human can review so much code in a lifespan.

Course continues by showing how to find and abuse stored XSS in Atmail, attack used to steal a cookie, and how to chain it with another vulnerability you've found at file upload routines to achieve RCE.

ATutor chapter shows how to abuse unfiltered SQL queries and well known PHP SNAFU (type juggling), both used to bypass authentication and achieve RCE again by exploiting routines that involve file upload.  
This chapter also shows that you shoudn't NOT trust ANY routine: always review them, even if they look safe, paying attention to details.

I loved both Atmail and ATutor because of PHP: I love it (from a pentester point of view actually).

You will now move to a vulnerable Java code, where you exploit SQL injection on Postgres to achieve RCE. I think this chapter is the one who gave me more headaches: extramiles are quite hard and there are lot of small details and interaction between components that will make an attack to fail.  
You will also cut&paste/write a lot of hawful code here, at least I did.

Bassmaster is a Node.js app you are required to exploit using a vulnerability that will also require sandbox escape. I never liked .js and I like it even less now: too many changes between releases. But it was very interesting, I surely added new shells on my belt.

The one I think is the biggest chapter, the last one, is about DNN, DotNetNuke: a big .net web framework. You will use and abuse DNN in so many ways you will be tempted to go back at some PHP (I've also read about new exploit came out after AWAE has been release online, just to say that if you give a challenge to lot of determined reviewers you will surely came up with at least some CVE).  
This chapter also introduce the concept of unsafe deserialization, you will find lot of details on it by reading [ysoserial](https://github.com/frohoff/ysoserial), [ysoserial.net](https://github.com/pwntester/ysoserial.net), and [Friday the 13th: Attacking JSON - Alvaro Muñoz & Oleksandr Mirosh - AppSecUSA 2017](https://www.youtube.com/watch?v=NqHsaVhlxAQ) and related resources.

For every reviewed and exploited webapp, you will:
* decompile the code, if it's compiled (Java and .net for example)
* learn how to do live debug, if possible (I remember debugging every webapp but ManageEngine, because of Java FUBAR)
* understand what's wrong
* exploit it

The course is also provided with working example of XSS fuzzer, and some SQLi automation that could be handy.

## Material

The course is provided with the usual PDF and some videos. I felt the material followed Offensive Security standard of quality, everything is clear and complete, even if you will find some "ok, now suffer doing this yourself" but this is expected.
As you read before, the lab has *just* 5 webapp. Way enough to make you cry mommy.

## Extra miles

AWAE PDF already recommend some extra miles. Do them. Do all of them.

While healing from the lab, I started crawling the Internet to find pre-installed webapp to do some code review, and have them readily up&running for a possible exploitable vulnerability.

One resource I've used is [bitnami](https://bitnami.com/stacks), a service that distributes images of widestream app for multiple virtualization technologies or container.  
You are sure there are vulnerabilities, because bugs are everywhere, but you aren't sure they are 1) exploitable 2) easy to find in the time you choose to spend.

And that's why, after having spent like 30/40 hrs and having found (not disclosed yet, maybe I will do later, messy notes :/) some exploitable one, I falled back to exploit-db.  
Like I will do for [XDS]({{ site.baseurl }}/2020/02/eLearnSecurity-eXploit-Development-Student), I used a lot [exploit-db](https://www.exploit-db.com/) to look for vulnerable webapp: you have the webapp (opensource or to be decompiled), you know that there is **at least** an exploitable vulnerability, and you can read the first lines of the exploit (or google for a writeup) as a spoiler if you feel you are stuck.  
You just need to deploy it if you want a proof.

I've mostly read review (and prep guide: remember that any extra mile could also be a good way to prepare for a course. any one.) where you are given a list of resources to read and study.  
I feel that AWAE and OSWE will be a better bout if you follow a different approach:
* you want to practice for exploit like Atmail XSS to RCE? use proper filter on exploit-db
* you want to practice for exploit like ATutor auth bypass to RCE and type juggling? use proper filter on exploit-db
* you want to practice for exploit like ManageEngine SQLi to RCE? use proper filter on exploit-db
and so on for all vulnerability classes you want to practice on.

There are tons of exploit on exploit-db, I think this is the best way to sharpen your whitebox skills in a controlled environment.

## Exam

Like for [OSCE]({{site.baseurl}}/2016/11/Offensive-Security-Certified-Expert), the exam is a 48hrs lab time plus 24hrs to write/review/send the report.  
You will have *some* webapp to analyze and exploit, and you can easily guess required steps.

As I said before, you could be asked to review a multi-million lines-of-code webapp. A lifetime wouldn't be enough to do a full code review, and you have just 48hrs to find and exploit.  
You have chances only if you start doing code analysis, and that's where our loved mind map came to help.

I strongly suggest you to write your own one, 48hrs are enough to find all the vulnerabilities but can be a short time if you take the wrong turn. Having a mind map ready at hand will help you to go back to your own method.

Of course things like Burp Suite Pro, SQLMap, commercial code review tool are forbidden, so be ready.


Two more advices:
* force yourself to take rest
* start with an easy one to get in the mood if you like so


## Conclusion

It's not so common for me to do whitebox review like I learnt doing AWAE, but the method I've learnt has been useful even for blackbox.

As you should now know, the course is not a web one like, say, eLearnSecurity [Web Application Penetration Testing eXtreme](https://www.elearnsecurity.com/course/web_application_penetration_testing_extreme/) or PortSwigger [WebSecurity Academy](https://portswigger.net/web-security). If you want to learn how to find and exploit vulnerabilities just by browsing webapp, don't take AWAE.

If you want to learn how to do code review, be ready to draw a mind map and go for it even if you are not seasoned: you'll need more practice and more extra miles, but you can do it.

I've read that the course could be taken also by web developer. I don't disagree, but I think this course alone would not be that useful if the dev doesn't have some notion about information security before to delve with this one.  
If you are a developer, read some [OWASP](https://owasp.org/) resources before to subscribe.

I also would like to debate common rant I've read so far:
* the lab is too small: no, it isn't, trust me. if you do **all** the exercises and extra miles, you'll see that you'd preferred a smaller one.
* it's not about web: well, it's not a web one if you think about blackbox/graybox approach. this is a whitebox one, you will learn how to find small vulnerabilities by reading the source code and how to chain them to achieve RCE.
* it doesn't teach you so much: re-read course material and take notes, I wrote a mind map. you'll soon see that you are provided with a clear way to find common pitfall. now it's up to you to find your own and to master it.
* they show you the vulnerable code but not how they found the vulnerability: partially covered with last one, let me repeat myself. if you pay attention to where showen vulnerabilities are, you can create a list of more interesting functions. that's how OffSec staff gives you hint, now you have to develop your own method.
