---
layout: post
title: Incremental Builds with Gradle
author: Maria Camenzuli
---

Gradle tasks provide support for incremental builds. If some work has already been done, Gradle can speed up the build by not redoing it. If you've ever noticed the `UP-TO-DATE` label on a task in one of your builds, then you have already seen this in action. This label indicates that no work was done on that task, because it had already been done.

Incremental builds work using defined task inputs and outputs. For each of your tasks, you can specify what files or directories will be used as input, and what will be produced as output. As an example, consider a Java compilation task. This task should take a collection of source files as inputs, and it should generate some class files as outputs.

When your task is run, Gradle checks whether any of your declared inputs and outputs have changed since the last time you ran the task. If it finds a change, it will rerun the task, but if not, it considers the task up to date and does not run it.

Declaring inputs and outputs for your custom task type is very straightforward. All you need to do is add each of your inputs and outputs as properties to your type, and annotate them as inputs and outputs. Take a look at this sample archive task.

```
package org.example

import java.io.File
import org.gradle.api.*
import org.gradle.api.file.*
import org.gradle.api.tasks.*

class ArchiveTask extends DefaultTask {

    private FileCollection targetFiles
    private File outputFile

    @InputFiles
    FileCollection getTargetFiles() { return this.targetFiles }

    @OutputDirectory
    File getOutputFile() { return this.outputFile }

    // add setter methods for the above

    @TaskAction
    void archiveFiles() {
        // ... do work
    }

}
```

You can read more about Gradle incremental builds, and how you can declare inputs and outputs in the [Gradle documentation](https://docs.gradle.org/current/userguide/more_about_tasks.html#sec:up_to_date_checks).