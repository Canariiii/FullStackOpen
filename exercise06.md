sequenceDiagram
    participant user
    participant browser
    participant server

    Note right of user: User writes a note and clicks "Save"
    user->>browser: Click "Save" button

    Note right of browser: The browser captures the input and sends it to the server using AJAX

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa (with note data)
    activate server
    server-->>browser: { "content": "New note", "date": "2024-7-23" }
    deactivate server

    Note right of browser: The browser receives the response and updates the UI without reloading the page

    Note right of browser: The browser renders the new note in the list of notes
