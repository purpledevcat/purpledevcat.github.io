---
layout: post
title: 5 things you can do to make your Gradle plugin better
author: Maria Camenzuli
---

Over the past few months, I've been doing a lot of work on Gradle plugins. My team at work currently produces and maintains a set of plugins that automate our software release process, by taking care of project versioning, publishing software aritfacts, packaging service configurations, and much more. Having gone through several iterations of these plugins, adding new features, refactoring existing ones, and listening to feedback from my colleagues who use them, I think that I have gotten a pretty good idea of what a good plugin looks like. I therefore want to share with you 5 tips I think would help you write a great Gradle plugin.

## 1. Write a typed DSL in your extension to accept user input.
If you are writing your plugin using Groovy, and you need to accept user input to configure your plugin, you can make use of closures and the [`@DelegatesTo`](http://docs.groovy-lang.org/docs/latest/html/documentation/core-domain-specific-languages.html#section-delegatesto) annotation to turn your configuration into a nice DSL.

## 2. Take a design first approach to your config DSL.
You want your user's build script to be as clean, readable, and intuitive as possible.

## 3. Print out helpful error messages.
You don't want your users to have to dig through your code and a stracktrace.

## 4. Declare task inputs and outputs.

## 5. Write good documentation.
When you need help understanding how to use a bash command, you bring up the manual pages, where you know you will find all the information you need. When you need help understanding what some Spring method does, you take a look at the Spring javadocs, because you know you will find an explanation. Similarily, your colleagues, or any other users of your plugin should have a reliable source of information when they need help properly using and configuring it.

I personally found that a good readme for your plugins will make life easier for both you and your users. It will help you because your colleagues will stop interrupting you to ask questions about how to use your plugins, and it will help your colleagues because they will have quick access to the information they need.

But what is in a good readme? It's probably safe to say that most people do not want to read a giant wall of text when they're adding a plugin to their buildscript. Buildscripts are rarely what you want to spend most of your time on when working on a project. Therefore I would suggest as much simplicity as possible ([KISS](https://www.wikiwand.com/en/KISS_principle) is not just for code you know). Nothing beats a couple of code snippets showing example configurations that cover the majority of use cases. You can supplement that with some brief sentences or paragraphs indicating how the examples can be customized to meet different needs. If your plugin adds any tasks, consider listing them as bullet points with a short sentence outlining what each task does.
