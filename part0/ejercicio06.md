sequenceDiagram
    participant Usuario
    participant Navegador
    participant Servidor
   
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