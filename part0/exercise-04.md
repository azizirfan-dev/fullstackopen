```mermaid
sequenceDiagram
    participant browser
    participant server

    note over browser: User writes a not and click Save

    browser -> server: POST https://studies.cs.helsinki.fi/exampleapp/new_note 
    activate sever
    Note right of server : Server saves the new note to the notes [] array
    server -> browser: HTTP 302 Redirect -> Location: /notes
    deactivate server

    Note over browser : Browser follows the redirect

    browser -> server : GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server 
    server -> browser : HTML document 
    deactivate server

    browser -> server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server -> browser: CSS file 
    deactivate server 

    browser -> server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server 
    server -> browser: Javascript file 
    deactivate server 

    Note right of browser: Browser executes JS -> fetches data.json

    browser -> server : GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server -> browser: [{ "content": "new note", "date": "..." }, ...]
    deactivate server

    Note right of browser: JS renders all notes to the DOM 
```