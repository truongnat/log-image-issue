### Sumary

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
  - build snoreToast to .exe file.
  - build ternimal-notifier to "app mac os" file.
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
    - It only show alarm with development environment.
    - It not show alarm with production environment.
    - Not show alarm button actions.
  
  
