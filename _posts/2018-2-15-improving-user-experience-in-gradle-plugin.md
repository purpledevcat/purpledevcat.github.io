---
layout: post
title: Improving User Experience in your Gradle Plugin
author: Maria Camenzuli
---

Over the past few months, I've been doing a lot of work on Gradle plugins. My team at work currently produces and maintains a set of plugins that automate our software release process, by taking care of project versioning, publishing software aritfacts, packaging service configurations, and much more. Having gone through several iterations of these plugins, adding new features, refactoring existing ones, and listening to feedback from my colleagues who use them, I !!!TODO!!

## 1. Write good documentation.
When you need help understanding how to use a bash command, you bring up the manual pages, where you know you will find all the information you need. When you need help understanding what some Spring method does, you take a look at the Spring javadocs, because you know you will find an explanation. Similarily, your colleagues, or any other users of your plugin, should have a reliable source of information when they need help properly using and configuring it.

I personally found that a good readme for your plugins will make life easier for both you and your users. It will help you because your colleagues will stop interrupting you to ask questions about how to use your plugins, and it will help your colleagues because they will have quick access to the information they need.

But what is in a good readme? It's probably safe to say that most people do not want to read a giant wall of text when they're adding a plugin to their buildscript. Buildscripts are rarely what you want to spend most of your time on when working on a project. Therefore I would suggest as much simplicity as possible ([KISS](https://www.wikiwand.com/en/KISS_principle) is not just for code you know). Nothing beats a couple of code snippets showing example configurations that cover the majority of use cases. You can supplement that with some brief sentences or paragraphs indicating how the examples can be customized to meet different needs. If your plugin adds any tasks, consider listing them as bullet points with a short sentence outlining what each task does.

## 2. Print out helpful error messages and logs.
Your Gradle plugin should handle errors as gracefully as possible, giving the user helpful information about what went wrong. Remember that your users are developers trying to setup their buildscript. If something goes wrong in their build, they are going to need to know what happened so they can fix it. In particular, try to identify errors that can happen because of misconfiguation, or in relation to some other user input, and make sure you are printing out a helpful error message explaining what needs to be corrected in order for the build to work. You don't want your colleagues to have to try to figure out what went wrong by going through a stacktrace of your code, or worse, come disrupt whatever you're currently working on to ask how to fix their broken builds.

Apart from error messages, your plugin will probably also output some logs indicating what work is being done. It will be helpful to your users if you are logging only relevant information, so that you do not clutter builds logs. Logs at the `info` level should include any information you think would be useful in a standard successful build run. These tend to act as a progress indicator for your tasks. Logs that give deeper insight into the specifics of what the plugin is doing should be marked as `debug`.

## 3. Take a design first approach to your configuration.
For most non-trivial plugins, you will most likely need your users to set some configurations in their build script. Your plugin should be configured in the most intuitive way possible.

## 4. Add type information to configuration closures using delegation.
If you are writing your plugin using Groovy, and your configuration extension accepts a closure, use the [`@DelegatesTo`](http://docs.groovy-lang.org/docs/latest/html/documentation/core-domain-specific-languages.html#section-delegatesto) annotation to provide type information.

## Conclusion
You will note that the majority of these improvements are focused on improving the user experience for people using your plugin.

