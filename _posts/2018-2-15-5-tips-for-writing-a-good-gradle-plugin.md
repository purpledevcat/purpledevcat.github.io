---
layout: post
title: 5 tips for writing a great Gradle plugin
author: Maria Camenzuli
---

Over the past few months, I've been doing a lot of work on Gradle plugins. My team at work currently produces and maintains a set of plugins that automate our software release process, by taking care of project versioning, publishing software aritfacts, packaging service configurations, and much more. Having gone through several iterations of these plugins, adding new features, refactoring existing ones, and listening to feedback from my colleagues who use them, I think that I have gotten a pretty good idea of what a good plugin looks like. I therefore want to share with you 5 tips I think would help you write a great Gradle plugin.

## 1. Write a typed DSL in your extension to accept user input.
Use delegates.

## 2. Take a design first approach to your config DSL.
You want your user's build script to be as clean, readable, and intuitive as possible.

## 3. Print out helpful error messages.
You don't want your users to have to dig through your code and a stracktrace.

## 4. Use appropriate log levels.

## 5. Write a good readme.

