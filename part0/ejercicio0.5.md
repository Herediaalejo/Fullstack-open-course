sequenceDiagram
    participant Usuario
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
    Servidor-->>Navegador: [{ "content": "HTML es fácil", "date": "2023-1-1" }, ... ]
    deactivate Servidor

    Note right of Navegador: El navegador ejecuta la función de devolución de llamada que renderiza las notas

    Usuario->>Navegador: Completa el formulario y hace clic en 'Save'

    Note over Navegador: Captura el evento de envío del formulario

    Note over Navegador: Previene la acción predeterminada del formulario evitando la redireccion

    Note over Navegador: Crea un objeto de nota con el contenido del formulario y la fecha actual

    Note over Navegador: Agrega la nueva nota al array 'notes'

    Note over Navegador: Limpia el campo de entrada del formulario

    Note over Navegador: Actualiza las notas

    Navegador->>Servidor: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa

    activate Servidor

    Note over Servidor: Procesa la solicitud POST
    Note over Servidor: Recibe los datos JSON y crea una nueva nota
    Servidor-->>Navegador: 201 Created

    deactivate Servidor