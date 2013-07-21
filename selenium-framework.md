*User Story*

A user story is a limited set of funcaitonality that the team feels comfortable implementing over the course of a single
iteration. These are tiny slices through the functionality. Usually a team strives to implement several user stories in 
one iteration. The business representive or product owner is responsible for defining stories.

*Story Card*

User stories are usually written on real cards. During the iteration, the cards are put onto the team's taskboard.

*Refactoring*

Refactoring is changing the structure of the source code without changing what it does. Usually I refactor codes before
introducing changes. By refactoring the code, I make the task of implementing the upcoming changes more easy.

*TDD*

In test-driven developement you write one single test that fails, write just enough code that make the failing test case
pass and all the other passed test case still passes. And then refactor your code to prepare it for the next tiny step.
TDD is a design approach and helps users write better code, because testable code is written by default.

------  

####Cucumber

+ features
+ cucumber command
+ step definition

####Gherkin

+ title
+ free-form narrative
+ arbitrary number of scenarios
+ arbitrary number of steps

####Features

In Cucumber, a feature is a high-level requirement expressed from the perspective of a person or another computer 
using the system. Features play a role similar to that of user stories in XP, but we take things a step further.

*Title*

few words that represent an activity for which a user may engage the system.

*Narrative*

The connextra format:

```xml
As a <role>
I want <feature>
So that <business value>
```

###Gherkin Keywords

+ Feature
+ Background
+ Scenario
+ Scenario outline
+ Scenarios or examples
+ Given
+ Then
+ And or but
+ | (define tables)
+ `"""` define multiline string
+ # comment

*Scenario*

concrete example of how we want the system to behaviour.

*Steps*

Scenario use an arbitrary number of steps to describe everything that happen within a scenario. A step is generally a 
single line of text that start with one of step keywords: Given, When, Then, And, But.

###Cucumber command

Cucumber command runs all the `*.feature` files below the features directories.

*Tags*

`cucumber --tags @wip`

`cucumber --tags @foo, @bar`  `@foo || @bar`

`cucumber --tags @foo --tags @bar` `@foo && @bar`

```
cucumber --tags ~@foo 
!@foo
```


###Cucumber Details

*Step Definition*

**Argument**

If a step definition’s regular expression contains one or more capture groups, it will treat them as arguments 
to the step definition’s block.

**World**

(https://groups.google.com/forum/#!topic/cukes/8ugcVreXP0Y)

The purpose of a "World" is twofold:
1) Isolate state between scenarios.
2) share data between step definitions and hooks within a scenario.

The equivalent of the World in Cucumber-Java is _all of the objects with hook or stepdef annotations_. 
In other words, any class with methods annotated with @Before, @After, @Given and so on will be instantiated exactly 
once for each scenario.

a) Use a single class for all of your step definitions and hooks
b) Use several classes divided by responsibility [1] and use dependency injection [2] to connect them to each other.

Option a) quickly breaks down because your step definition code becomes a mess. That's why people tend to use b).

**Nested Steps**

(https://groups.google.com/forum/#!topic/cukes/OUy9go8AsTo)

refactor to common method

*Hooks*

+ Before
+ After
+ Executed before and after each scenario!

**Tagged Hooks**

<https://github.com/cucumber/cucumber/wiki/Hooks>
<https://github.com/cucumber/cucumber-jvm/blob/master/ex
amples/java-webbit-websockets-selenium/src/test/java/cucumber/examples/java/websockets/SharedDriver.java>
<http://zsoltfabok.com/blog/2012/09/cucumber-jvm-hooks/>

DI Hooks:

<https://gist.github.com/paoloambrosio/3874974>
<https://gist.github.com/paoloambrosio/5952737>
<https://github.com/cucumber/cucumber-jvm/pull/295>
<https://groups.google.com/forum/#!topic/cukes/Z2mWgk0rSgs>

*Background*

Hooks in features files will be executed before each scenario.

Before Hooks will run before Background hook.

*Multiline Text*

use `"""`

*Table Values*

When Cucumber sees a | at the beginning of a line following a line with a Step keyword, it parses that 
and all subsequent lines beginning with | and stores the cell values in a Cucumber::Ast::Table object, which exposes
the data as an array of hashes via a hashes( ) method.

*Scenario Outline*

