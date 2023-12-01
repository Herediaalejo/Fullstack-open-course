sequenceDiagram
    participant Navegador
    participant Servidor

    Navegador->>Servidor: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate Servidor
    Servidor-->>Navegador: Documento HTML
    deactivate Servidor

    Navegador->>Servidor: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate Servidor
    Servidor-->>Navegador: El archivo CSS
    deactivate Servidor

    Navegador->>Servidor: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate Servidor
    Servidor-->>Navegador: El archivo JavaScript
    deactivate Servidor

    Note right of Navegador: El navegador comienza a ejecutar el código JavaScript que obtiene el JSON del servidor

    Navegador->>Servidor: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate Servidor
    Servidor-->>Navegador: [{ "content": "......", "date": "2023-10-10" }, ... ]
    deactivate Servidor

    Note right of Navegador: El navegador ejecuta la función de devolución de llamada que renderiza las notas