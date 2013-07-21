How to run Cucumber-jvm from commandline:              
http://stackoverflow.com/questions/11466040/cucumber-jvm-ant-task

Take Screenshot in Cucumber:           
http://stackoverflow.com/questions/16160200/take-a-screenshot-with-cucumber

Cucumber want to quit when any test case fails:         
http://stackoverflow.com/questions/15272523/what-is-the-cucumber-jvm-equivalent-of-cucumber-wants-to-quit

Embed screenshot into test:               
http://rlogiacco.blogspot.com/2012/10/embedding-screenshots-in-cucumber-jvm.html

Slideshare:       
http://www.slideshare.net/search/slideshow?searchfrom=header&q=cucumber-jvm

Speakdeck:                
https://speakerdeck.com/search?q=cucumber-jvm

How to run cucumber-jvm from command line:      
https://groups.google.com/forum/#!topic/cukes/9EqBYV3FJc8

```java
D:\maven_repo\info\cukes\cucumber-core\1.1.3>java -cp D:/maven_repo/info/cukes/cucumber-core/1.1.3/cucumber-core-1.1.3.jar;D:/maven_repo/info/cukes/cucumber-java/1.1.3/cucumber-java-1.1.3.jar cucumber.api.cli.Main --help
```

```java
Usage: java cucumber.api.cli.Main [options] [ [FILE|DIR][:LINE[:LINE]*] ]+

Options:

    -g, --glue PATH                    Where glue code (step definitions and hooks) is loaded from.
    -f, --format FORMAT[:PATH_OR_URL]  How to format results. Goes to STDOUT unless PATH_OR_URL is specified.
                                       Available formats: junit, html, pretty, progress, json, json-pretty.
    -t, --tags TAG_EXPRESSION          Only run scenarios tagged with tags matching TAG_EXPRESSION.
    -n, --name REGEXP                  Only run scenarios whose names match REGEXP.
    -d, --[no-]-dry-run                Skip execution of glue code.
    -m, --[no-]-monochrome             Don't colour terminal output.
    -s, --[no-]-strict                 Treat undefined and pending steps as errors.
        --dotcucumber PATH_OR_URL      Where to write out runtime information. PATH_OR_URL can be a file system
                                       path or a URL.
    -v, --version                      Print version.
    -h, --help                         You're looking at it.

```
