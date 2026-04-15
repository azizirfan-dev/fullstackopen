```
sequenceDiagram 
    participant browser 
    participant browser 

    browser -> server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server 
    server -> browser: HTML document 
    deactivate server 

    browser -> server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server 
    server -> browser: CSS file
    deactivate server 

    browser -> server: GET ttps://studies.cs.helsinki.fi/exampleapp/spa.js
    activate server
    server -> browser: Javascript file (spa.js)
    deactivate server 

    Note right of browser: Browser execute spa.js -> fetches notes data 

    browser -> server: GET GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "HTML is easy", "date": "..." }, ...]
    deactivate server

      Note right of browser: spa.js renders the notes to the DOM without reloading
```