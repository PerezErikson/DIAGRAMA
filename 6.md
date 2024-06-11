```mermaid
sequenceDiagram
    participant browser
    participant server

    Note right of browser: El usuario escribe una nota en el campo de texto y hace clic en "Save"

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    Note right of server: El servidor recibe la nueva nota y la guarda
    server-->>browser: { "message": "note saved" }
    deactivate server

    Note right of browser: El navegador actualiza la lista de notas sin recargar la página
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ..., { "content": "Nueva nota", "date": "2024-6-10" }]
    deactivate server

    Note right of browser: El navegador renderiza la nueva lista de notas
