---
layout: post
title: "Cracking The Perimeter - Offensive Security Certified Expert"
description: "Here is my take on Cracking The Perimeter course and relative exam for Offensive Security Certified Expert"
share: true
tags:
 - courses
 - certifications
 - red
---

# Offensive Security - Cracking The Perimeter (CTP)

[CTP](https://www.offensive-security.com/ctp-osce/) looked the perfect "next step" after having [PWK and OSCP back in 2015]({{site.baseurl}}/2015/08/Offensive-Security-Certified-Professional).

## Overview

Even in 2016, CTP looks a bit outdated, but I must agree with [g0tm1lk](https://blog.g0tmi1k.com/2013/08/cracking-perimeter-ctp-offensive/) here, and I think I will stress this also for future reviews: you can't run if you can't walk.  
The thing I appreciate the most about Offensive Security courses is that they (try to) make you develop a method: if you will, you can take all the steps needed to fast forward to current techniques studying yourself.  
And CTP makes no exception here.


## Material

Offensive Security puts **a lot** of effort to deliver very good PDFs. All courses I've taken (ndr: 4 in total) are damned good at presenting and making you to struggle while solving exercises.  
A plus to me but YMMV, PDF and videos are not a carbon copy: you'll find stuff only on PDF or only on the videos, and sometimes neither. You must be able to do your homework, or you won't survive the course - let alone the exam.

I remember I felt that some textes have been written to make you to fail during the exercise just to make you to "try harder" and find the way yourself. But let me explain better: you're not alone, and material is not incomplete, it's made with a purpose.

The course covers a very wide area: she starts from the web angle, presents how to exploit networks, and also focuses on antivirus bypass and (basic) Windows exploit development.

---

The web angle is quite classic nowdays (you'll read this post in 2020 or later, because I'm writing 4 years after having done the course) but still interesting. After all, you're not going to do CTP to learn web tricks, but offsec reminds you that web should always be kept in mind when attacking a network.  
You are required to exploit XSS and to do some directory traversal, as I said, nothing on the bleeding edge but still interesting.

The network angle shows how to hijack network flows by exploiting weak protocols and reconfiguring a router. Make sure to have a talk with your legal before attempt this attack on a production network ;)  
Again, the attack is not bleeding edge but shows how to move from layer7 to layer2/3: a must for a "full stack" penetration tester.

You will surely spend more time in the next two arguments: backdooring (and AV bypass) and exploiting.

During this long journey you will learn how to find (or create) space in a PE32 file for a backdoor, and how to make the backdoor undetected by antivirus.  
You will split your payload, find offending bytes, replace with similar expression or encode them. All by hand.  
You could argue that there are tons of programs and scripts that can do this in a fraction of time, but the goal of a course is to learn what's happening so you can better understand how thing works and develop your own tool or modify an existent one. You should know what happens when a script becomes mainstream, and you must have a plan-B.  
Indeed I encourage you to write your own tool once you solved the exercise.

Plus, I was surprised to see this tricks working still in 2018, and sometimes even nowdays (2020).

Exploitation angle presents some old techniques: SEH and egghunting on a Windows with no DEP.  
Let me repeat it: you won't exploit any modern system if you are not able to exploit classic ones. Plus, the reversing side of this chapter has been overlooked by most of reviews I've read: you're not going to put a *msfpattern* here and there and call it a day, you have to understand what's going on. Being fluent with a disassembler, and of course with the debugger itself, will help a lot.  
Trust me, you won't forget HP Openview NNM soon.

You will also be introduced to a basic fuzzing framework, SPIKE, and OllyDbg, even if my take was to use ImmunityDebugger and mona.py. The debugger itself is nowdays a bit outdated, but again: start walking, then run.

The lab is way smaller than the one you eventually pillaged during OSCP because the goal is completely different. Trust me, it's big enough.

## Extra miles

For the exploitation exercises, my suggestions are:
* [Corelan Exploit Writing Tutorials](https://www.corelan.be/index.php/articles/) Corelan is like Dorian Gray: he must have a picture that ages and fades somewhere. Read starting from [part1](https://www.corelan.be/index.php/2009/07/19/  exploit-writing-tutorial-part-1-stack-based-overflows/), try to not jump into the rabbit hole too early.
* [FuzzySecurity Windows Exploit Development Tutorial Series](https://www.fuzzysecurity.com/tutorials.html) from part1 to part7, another very neat introduction to Windows exploitation
* [Vulnserver](http://www.thegreycorner.com/p/vulnserver.html) is a daemon affected to different class of vulnerabilities, very very useful to practice
* I remember I've read The Art of Exploitation (2nd Edition) [ISBN-13: 978-1-59327-144-2]
* doing [SLAE32](https://www.pentesteracademy.com/course?id=3) (you can read my review [here]({{ site.baseurl }}/2019/10/SLAE))will surely help a lot for both backdooring and exploiting, do it if you're new with assembly

Do as much assembly as you can.

For the web side, good old Web Application Hackers' Handbook (2nd Edition) [ISBN-13: 978-1118026472] will be more than enough. If you want a more updated one, you can go with [Portswigger's Web Security Academy](https://portswigger.net/web-security)


## Exam

The exam is a 48hrs full immersion on labs, and a 24hrs for the report.  
There is at least one curve ball, so be ready to re-read twice every statement and to follow step-by-step (yep, like a child) the notes you took during the course.

My advice on this are always the same:
* be ready with your cheatsheet, I personally love to mind map
* force yourself to take rest
* start with an easy one to get in the mood if you like so

## Conclusion

Regarding the time, I think a 30days is enough, but if you have a full time job (and you know you could be forced to put on hold for a week or like) I'd go for a 60days.

I'm not sure I would suggest OSCE in 2020, even that there are rumours about a v2 coming later this year.  
Don't take me wrong: the course is awesome, but it's 12/15 Franklin.

Given that Offensive Security does a very good work on helping students to build a method, I see this course as a good summary of three different angle: web (see you with [OSWE]({{site.baseurl}}/2019/08/Offensive-Security-Web-Expert) for the whitebox approach), network, exploitation. With the backdooring chapter as a plus. And a jackhammer in your head everytime you work on backdoring and exploiting.

You can surely follow the syllabus and find similar resources online, but you quite surely won't struggle like exploiting NNM. Plus, OffSec exams gives an unparalled thrill.

To me, exams' are worth a big part of the journey.

Personally, I would re-take this one: company's budget will surely cover.
