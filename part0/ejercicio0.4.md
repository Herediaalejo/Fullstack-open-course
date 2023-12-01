sequenceDiagram
    participant Usuario
    participant Navegador
    participant Servidor

    Usuario->>Navegador: Completa el formulario y hace clic en 'Save'
    Navegador->>Servidor: POST https://studies.cs.helsinki.fi/exampleapp/new_note

    activate Servidor

    Note right of Servidor: Procesa la solicitud POST
    Note right of Servidor: Crea una nueva nota con el contenido del formulario y la fecha actual
    Note right of Servidor: Agrega la nueva nota al array 'notes'
    Servidor-->>Navegador: Redirecciona la página, 302 Found

    Navegador->>Servidor: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate Servidor
    Servidor-->>Navegador: Documento HTML
    deactivate Servidor

    Navegador->>Servidor: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate Servidor
    Servidor-->>Navegador: El archivo CSS
    deactivate Servidor

    Navegador->>Servidor: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate Servidor
    Servidor-->>Navegador: El archivo JavaScript
    deactivate Servidor

    Note right of Navegador: El navegador comienza a ejecutar el código JavaScript que obtiene el JSON del servidor

    Navegador->>Servidor: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate Servidor
    Servidor-->>Navegador: [{ "content": "HTML es fácil", "date": "2023-1-1" }, ... ]
    deactivate Servidor

    Note right of Navegador: El navegador ejecuta la función de devolución de llamada que renderiza las notas



