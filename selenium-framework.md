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

Argument

If a step definition’s regular expression contains one or more capture groups, it will treat them as arguments 
to the step definition’s block.

World

