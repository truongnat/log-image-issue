### Feature

  - Start meeting before one minute.
  - User joined lobby.
  - End meeting
  - Reject, Admit meeting.
  
 
 ### Implementation
 
 - Library:
   + [node-notifier](https://github.com/mikaelbr/node-notifier) - ( cross-platform )
   + [snoreToast](https://github.com/KDE/snoretoast) - (window)
   + [terminal-notifier](https://github.com/julienXX/terminal-notifier) - (macOS)
   
 We are using node-notifier for send alarm to OS, mechanism:
  - build snoreToast to .exe file ( language: C++ ).
  - build ternimal-notifier to "app mac os" file ( language: Objective C, Ruby ).
  - move two file above to /vendor folder inside node-notifier library.
  - when send alarm => node-notifier will check current OS and send to it.
  
 Low level:
  - node-notifier open socket, execute file ( .exe or app ) and pass properties down to app.
  - under hood, app will listening socket and send event or data when user interactive to node-notifier.
  - node-notifier using emit-event comunicate with node js ( current is electron js ).
  
  ### Problem
  
  - On window:
    Work well with development and production environment.
    
  - On mac:
    - It only show alarm with development environment and not work on production.
    - Not show alarm button actions.
    - Because it doesn't have button actions, so I don't guarantee button click event to work.
  
  I think we need to check the native code to be compatible with electron js and need more time to check. Previously on Window platform it had the same problem and
  I found the PR for it [(See PR)](https://github.com/KDE/snoretoast/pull/15/files)
