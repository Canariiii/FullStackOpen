sequenceDiagram
    participant user
    participant browser
    participant server

    Note right of user: User writes a note and clicks "Save"
    user->>browser: Click "Save" button

    Note right of browser: The browser captures the input and sends it to the server

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note (with note data)
    activate server
    server-->>browser: Redirect to /notes
    deactivate server

    Note right of browser: The browser follows the redirect and reloads the page

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, { "content": "New note", "date": "2024-7-23" }, ... ]
    deactivate server

    Note right of browser: The browser executes the callback function that renders the notes, including the new note
