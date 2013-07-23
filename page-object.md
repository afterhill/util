###Overview

PageObject
  
+ methods (Services)
+ object repositories

Page Object encapsulate all the details of webdriver.

+ test should be responsible for making assertions
+ page object offering service

####Summary

+ public method represent the services that page offers
+ try not to expose internal of page
+ generally don't make assertion in page object
+ methods can return other pages
+ need not represent an entire page
+ different result for the same action are modelled as different methods

####Example

```
LoginPage --> HomePage
     |
    \|/
     |
    FailPage
```

###Page Factory

+ lazy initialization
+ more easiable code
+ object repository abstraction layer
+ test assertion layer
+ service layer
    
###Take Screenshots

####TakeScreenshot

+ get full screen and then save to one place


+ get frame screen


+ get OS full screen
