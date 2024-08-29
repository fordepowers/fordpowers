---
layout: ../../layouts/post.astro
title: Modern Web App Testing
description: A cursory summary through how to test web apps in the modern age
dateFormatted: Jan 21st, 2022
---

A few years ago I started my software journey as a quality assurance intern assisting a development team.
At the time, we used many <i>older</i> industry tools to automate our quality checks, namely Selenium Webdriver via Java.

Fast forward a few years, and now as an older and wiser web developer the task of finding tools to help our team identify and triage issues fell into my slot on the Trello board. 
So, I set out to find what's new on the scene and what could help developers with a modern <abbr title="MongoDB, Express, React, NodeJS">MERN</abbr> stack.

### Memory Leaks - <a href="https://github.com/nolanlawson/fuite">Fuite</a>

First up is <code>fuite</code>, a memory leak testing tool. 
Oddly enough, I don't see a lot of <abbr title="Single Page Application">SPA</abbr> developers testing applications for memory leaks, even though it could be a breaking issue for the user, and one that is frustratingly hard to debug.
Fuite does an excellent job of taking the hassle out of memory testing, by doing all the memory consumption comparison for you (in a pretty straightforward and intelligent way) and then gives you actual metrics you can use to measure improvement afterwords.
I also thought basing the tool off of <a href="https://pptr.dev/#?product=Puppeteer&version=v12.0.1&show=api-class-page">Puppeteer Pages</a> was
clever, as it's a solid standard and most of us will need to configure custom scenarios so the tool can access privileged or restricted routes.
For more info on how to use it, read the <a href="https://nolanlawson.com/2021/12/17/introducing-fuite-a-tool-for-finding-memory-leaks-in-web-apps/">official blog post & how to guide.</a>

### Load & Stress - <a href="https://locust.io/">Locust.io</a>

Previously I had experience using JMeter as a stress & load testing tool for a few applications.
It worked well enough and has a large community supporting it, but I can definitely appreciate why someone made a modern tool.
Pretty much all my previous gripes with JMeter (Java based, clunky interface, high initial time sink) are fixed with <code>locust.io</code>. 
Python-based, gives you metrics and pretty graphs out of the box so you can compare results across runs and code updates.
It's also capable of being much more than just a simple load balancing tool, but it remains easy enough to setup for the layman. <i>(Open source is another big plus in my book)</i>

### Integration - <a href="https://www.cypress.io/">Cypress</a>

Full feature integration testing (end to end testing) is a non-trivial pursuit. 
Depending on the complexity of the application it can require large amounts of code in order to have the automated sequence perform well.
Having used Selenium Webdriver personally, while it still remains the standard for a number of reasons, I don't think those reasons are particularly good. 
A couple of my grievances:

 - It's unabstract and too specific when writing page interactions
 - Selenium is heavy as far as packages go - the Java implementation in particular is not easy to install
 - It doesn't play nicely at all with any modern <abbr title="Continuos Integration/Continuous Deployment">CI/CD</abbr> pipeline- we had to break things to get it working

Cypress is 100% easier and nicer to use.
It's also Javascript, which, when you're writing JS anyways for development makes life quite a bit easier.

### Unit - <a href="https://jestjs.io/">Jest</a>

Good ole' Jest. Can't say much really that hasn't already been said, Jest has remained as the standard for Javascript unit testing for years, and decidedly deserves it's crown.

 - It's lightweight (4kb unpacked)
 - Extensively documented
 - Has a massive community
 - It's actively maintained and has deep pockets due to Facebook money

It also works with all the good stuff like Typescript, Babel and Node, so there's not really a case it can't handle.