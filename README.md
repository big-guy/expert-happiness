This doesn't do anything useful.

Build Gradle with branch `sg/native/source-deps` and then run:

`gradlet dependencies`

This should show something like:
```
compileClasspath - Compile classpath for source set 'main'.
\--- org.spockframework:spock-core:1.1-groovy-2.4 -> project :spock:spock-core
     +--- org.codehaus.groovy:groovy-all:2.4.12 -> project :groovy
```

This shows that Groovy and Spock are both coming "from source".  You'll notice that the Groovy build has a long configuration time. You may need to make sure only a single version of the build-scan plugin is applied (so remove/comment out any init scripts).

If you comment out the Groovy SCM information in `settings.gradle`, you'll see something like:
```
compileClasspath - Compile classpath for source set 'main'.
\--- org.spockframework:spock-core:1.1-groovy-2.4 -> project :spock:spock-core
     +--- org.codehaus.groovy:groovy-all:2.4.12
```

If you comment out all of the SCM information, you won't see any project substitutions.