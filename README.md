# HOLLYWOOD-MAL Libraries
**This is a collection of libraries I coded to help myself with my projects**

# IMPORTANT NOTE
From now (04/08/2020) I'm putting libraries using a global include file called **+Includes.hws** where all library names are defined along with their path, in order to run the examples you need to setup the variable **#INC_PATH** with the absolute path where you have saved/cloned the libraries, if you do this you will be able to run all the examples with a double click, for example let's suppose you have cloned the entire repository into the following path : `C:/MyHollywoodStuff/Libs/`  
All you have to do is:  
+ Open the file `+Includes.hws`  
+ Edit the line `Const #INC_PATH     = ""`  
+ Putting the absolute location, in our case `C:/MyHollywoodStuff/Libs/`  
+ Save the edited file  
+ You are ready!

---

# Lib-Helpers
 **Hollywood-MAL Helpers Library**
 
 This library includes a collection of common utility functions and methods, please refer to the **helpers.html** file fo a detailed description.

# Lib-Easing
 **Hollywood-MAL Easing Library**
 
 Easing library is an include file for Hollywood able to create very smooth transitions between values so you can use it to animate almost anything like: graphical objects, colors, values, and any value you  need to be smoothly changed into another value.
 For detailed informations have a look at **easing.md** file.
 
# Lib-Tables  
 **Hollywood-MAL Tables Library**
 
 Tables library is an include file for Hollywood with several functions to manipulate tables, including comparisons, merge, set, sort, push, shift and many others. Please have a look at the file **tables.md** for more informations.
 
# Lib-Debug
 **Hollywood-MAL Debug Library**
 
 Debug library is a library developed to help debugging session, it can be used to
 generate debug output to the console or to a one or more files, both debug output can use ANSI colors or plain text.
 
 Debug library can manage one or more debug channels so that you are able to switch
 on or off single channels and reduce the amount of output to analyze, this is very useful for complex programs involving several includes or libraries.
 
 If you have an ANSI capable terminal debug messages can be colored to help
 you identify errors and warning in no time.
 
 Debug library has the ability to show nested messages, this is incredibly useful
 when you have recursive functions and external library calls: without a proper
 output formatting a standard debug session could become a pain.
 
 You can output tables too, and they are formatted and idented properly to let
 you look easily at their contents.
 
# Lib-ANSI
 **Hollywood-MAL ANSI Library**
 
   Ansi library is an include file for Hollywood that will help you to 
 manage ANSI escape codes so you can print colored text in the console 
 of your host system.
 
   I’ve developed this library to have an invaluable help while I’m 
 debugging applications because this way I’m able to spot on the fly 
 errors and/or warning messages that are hilighted from the rest of the
 messages.
 
   Of course you need that your host system console is able to understand
 ANSI ascape codes, but almost any OS is able to do that… except 
 Windows! 
 For the Windows OS you need to install any thirdy party 
 application to accomplish the task, on my development machine, running
 Windows 10, I’m using **ansicon** program to make use of ANSI codes.

# Lib-GFX
 **Hollywood-MAL GFX Library**
 
   GFX library is an include file for Hollywood that helps with common
 graphical-related operations.
 
# Lib-FS
**Hollywood-MAL FS Library**

  FS is a library developed to help with common file system related
 operations.

 ---
 Latest update: 04/08/2020
 ---