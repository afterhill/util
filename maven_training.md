Maven:

+ Convention over Configuration.
+ Plug-ins based architecture
+ Phase based build cycle

##Plug-ins

###Core plugin (composited by goals)

+ clean
+ compiler
+ deploy
+ failsafe
+ install
+ resources
+ site (Maven 2)
+ site (Maven 3)
+ surefire
+ verifier

###packing types/tools

+ ear
+ ejb
+ jar
+ rar
+ war
+ app-client
+ shade

###Reporting

+ changelog
+ changes
+ checkstyle
+ doap
+ docck
+ javadoc
+ jxr
+ linkcheck
+ pmd
+ project-info-reports
+ surefire-report

###Tools

+ ant
+ antrun
+ archetype
+ assembly
+ dependency
+ enforcer
+ gpg
+ help
+ invoker
+ jarsinger
+ one
+ patch
+ pdf
+ plugin
+ release
+ reactor
+ remote-resources
+ scm
+ source
+ stage
+ toolchains

###IDEs

+ eclipse
+ idea


##Thrid Party plug-ins

##CodeHaus.org

+ animal-sniffer
+ build-helper
+ castor
+ clirr
+ javacc
+ jdepend
+ native
+ sql
+ taglist
+ versions

##Misc

+ cargo
+ clover
+ jetty
+ jalopy
+ rat

##Phase (bind plugin goals to pahse)

+ process-resources
  + resources:resources
+ compile
  + compiler:compile
+ process-classes
+ process-test-resources
  + resources:test-resources
+ test-compile
  + compiler:testCompile
+ test
  + surefire:test
+ prepare-package
+ package
  + jar:jar
+ install


##Maven Coordinate

POM - Project Object Model, a declarative description of a project.

Goals of plugin will look up the POM to get the parameters. Coordinate is a unique identifier of project and defines the relationship between the project and other through dependencies.

###Format of coordinate

groupId:artifactId:packing:version

+ groupId: group, company, team, project name. reverse of domain name of organization.
+ artifactId: unique identifier under groupId that represents a single project.
+ version: special release of a project.
+ packing: type of project, default to jar.

##Maven Repository

a collection of project artifacts stored in a directory structure that closely matches a project Maven's coordinates.

The standard for a Maven repository is to store an artifact in the following directory relative to root of repository:

```
/<groupId>/<artifactId>/<version>/<artifactId>-<version>.<packing>
```

```
groupId:artifactId:packing:version
```








