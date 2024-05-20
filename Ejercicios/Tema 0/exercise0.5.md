```mermaid
sequenceDiagram
    participant UI 
    participant Servidor

 UI->>Servidor: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate Servidor
    Servidor-->>UI: HTML document
    deactivate Servidor

    UI->>Servidor: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate Servidor
    Servidor-->>UI: the css file
    deactivate Servidor

    UI->>Servidor: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate Servidor
    Servidor-->>UI: the JavaScript file
    deactivate Servidor

    Note right of UI: The browser starts executing the JavaScript code that fetches the JSON from the server

    UI->>Servidor: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate Servidor
    Servidor-->>UI: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]
    deactivate Servidor

    Note right of UI: The browser executes the callback function that renders the notes
    