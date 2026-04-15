```mermaid 
sequenceDiagram 
    participant browser 
    participant server

    Note over browser: user writes a note and click Save button 
    Note over browser: spa.js calls e.preventDefault() to prevent default form submission 

    browser -> server: POST ttps://studies.cs.helsinki.fi/exampleapp/new_note_spa

    Note right of browser: Body: { content: "...", date: "..." }

    Header: Content-type: application/json
    activate server 

    Not right of browser: Server saves the note 
    
    server -> browser: HTTP 201 created
    deactivate server

    Note right of browser: spa.js appends the note to the lcoal array 
    and re-renders the DOM directly 
    No additionbal HTTP request are made
```