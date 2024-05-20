sequenceDiagram
    actor Usuario
    participant UI 
    participant Servidor

    Usuario->>UI: Escribe en el campo de texto
    Usuario->>UI: Hace clic en el botón Save
    UI->>Servidor: POST  https://studies.cs.helsinki.fi/exampleapp/new_note param:Note
    Servidor-->>UI: La respuesta se ha creado correctamente

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