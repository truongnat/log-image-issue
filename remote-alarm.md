### Issue

MacOS: 
 - Not show alarm button actions.
 - Because it doesn't have button actions, so I don't guarantee button click event to work.

 ### Libray
 
 - Library:
   + [node-notifier](https://github.com/mikaelbr/node-notifier) - ( cross-platform )
   + [snoreToast](https://github.com/KDE/snoretoast) - (window)
   + [terminal-notifier](https://github.com/julienXX/terminal-notifier) - (macOS)
   
   
 ### Flow work
 
 We are using node-notifier for send alarm to OS, mechanism:
  - build snoreToast to .exe file ( language: C++ ).
  - build ternimal-notifier to "app mac os" file ( language: Objective C, Ruby ).
  - move two file above to /vendor folder inside node-notifier library.
  - when send alarm => node-notifier will check current OS and send to it.
  
 Low level:
  - node-notifier open socket, execute file ( .exe or app ) and pass properties down to app.
  - under hood, app will listening socket and send event or data when user interactive to node-notifier.
  - node-notifier using emit-event comunicate with node js ( current is electron js ).

![image](https://user-images.githubusercontent.com/87919564/173243996-22986a61-9c71-4643-8122-040b877c5063.png)

  
  ### Solution
  
  Previously on Window platform it had the same problem and I found the PR for it [(See PR)](https://github.com/KDE/snoretoast/pull/15/files)
  
  - I think need to fix ternimal-notifier work with electron js and re-build app, then move to /vendor in hello project.

  ### Advice
  
  - This one need more time to investigate inside native code ( terminal-notifier )
  - Then update lib or clone and re-build code.

> if you have any idea please share to us
