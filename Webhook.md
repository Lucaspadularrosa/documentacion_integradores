![logo](assets/logo.png)

[🔙 Volver a inicio](Readme.md)

# Webhook

Un webhook, también conocido como "devolución de llamada web", es un método sencillo que permite que una aplicación o sistema proporcione información en tiempo real cada vez que ocurre un evento. En otras palabras, es una forma pasiva de recibir datos entre dos sistemas a través de una solicitud HTTP POST.

Puedes configurar notificaciones mediante webhooks en el panel del inmobiliario al crear tus credenciales. [Crear Credenciales](Credenciales.md)

Una vez configurado, el webhook enviará información automáticamente cuando se produzcan eventos registrados. Esto evita la necesidad de realizar búsquedas constantes para obtener respuestas y, en consecuencia, reduce la carga del sistema y previene la pérdida de datos en situaciones específicas.

Hasta el momento, la única notificación disponible es cuando un usuario envía un mensaje a través de CABAPROP, enviaremos un JSON por POST a la url indicada en el panel de integración con el siguiente formato.

```json
{
    "apiKey": "kib5tcxwsw5ain9ppngi9fodmiks0z",
    "type": "message",
    "action": "create.message",
    "id": 44444,
}
```

En este json recibiran:

1. **apiKey**: La apiKey de la integración que envió el mensaje.
2. **type**: El tipo de notificación, en este caso siempre será "message".
3. **action**: La acción que se realizó, en este caso siempre será "create.message".
4. **id**: El id de la conversación que se creó.

>**IMPORTANTE**
>
>Enviaremos la notificación una sola vez y esperaremos una respuesta con un estado 200 en un máximo de 200 milisegundos. Por lo tanto, recomendamos ejecutar las tareas necesarias en segundo plano utilizando colas de trabajo.


Con los datos recibidos pueden consultar la conversación a través de la API de CABAPROP. [Documentación Swagger](https://cabaprop.ar/api/v1/integration-docs#/)

La conversación se puede consultar a través del endpoint:

```
curl -X 'GET' \
  'https://cabaprop.com.ar/api/integration/get-conversation/[ID_CONVERSACION]' \
  -H 'accept: */*' \
  -H 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhcGlLZXkiOiIzdjd2aThpZHdpbmxqaGFxNm9odGZwbzZzcGNhbGoiLCJzZWNyZXQiOiJ1aDR6NGtiYTZzM2EzdTU0MHFrYXJsaXUxeGJtbGFxbm0xeWlicml4cW1xaWlqeThlaXkzbnI2MjZtYXhkNjY1IiwidXNlcklkIjoiZmM5NjQ5MjAtNGU3Ni00YmUyLTgyNmUtMDlmZmJiMjRmODA5IiwibmFtZSI6Ik1pQXBwIiwiaWF0IjoxNjk1NDc4MTg4LCJleHAiOjE2OTgxMDYxODh9.f-2mBpbj2VadnN6l3004u2Z-QO-y_LqhU79DmwoGrVc'
```

Recibiras los datos del interesado, el ID de la propiedad, los datos de la sucursal a la que estan consultando y un objeto con todos los mensajes de la conversación.

Seguiremos trabajando para agregar más notificaciones en el futuro. Si tienes alguna sugerencia, no dudes en ponerte en contacto con nosotros.