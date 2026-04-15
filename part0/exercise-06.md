``mermaid 
sequenceDiagram 
    participant browser 
    participant server

    Note over browser: user writes a note and click Save button 
    Note over browser: spa.js calls e.preventDefault() to prevent default form submission 

    browser -> server: POST ttps://studies.cs.helsinki.fi/exampleapp/new_note_spa

    Note right of browser: 