![logo](assets/logo.png)

[🔙 Volver a inicio](Readme.md)

# Webhook

Un webhook, también conocido como "devolución de llamada web", es un método sencillo que permite que una aplicación o sistema proporcione información en tiempo real cada vez que ocurre un evento. En otras palabras, es una forma pasiva de recibir datos entre dos sistemas a través de una solicitud HTTP POST.

Puedes configurar notificaciones mediante webhooks en el panel del inmobiliario al crear tus credenciales. [Crear Credenciales](Credenciales.md)

Una vez configurado, el webhook enviará información automáticamente cuando se produzcan eventos registrados. Esto evita la necesidad de realizar búsquedas constantes para obtener respuestas y, en consecuencia, reduce la carga del sistema y previene la pérdida de datos en situaciones específicas.

Hasta el momento, la única notificación disponible es cuando un usuario envía un mensaje a través de CABAPROP, enviaremos un JSON por POST a la url indicada en el panel de integración con el siguiente formato.

```json
{
    "id": 12345,
    "live_mode": true,
    "type": "payment",
    "date_created": "2015-03-25T10:04:58.396-04:00",
    "user_id": 44444,
    "api_version": "v1",
    "action": "payment.created",
    "data": {
        "id": "999999999"
    }
}
```

aca otro texto explicando los datos.

>[!IMPORTANTE]
>
>Enviaremos la notificación solo una vez, y esperamos una respuesta con status 200 en un máximo de 200mls, por lo tanto, recomendamos ejecutar las tareas necesarias en segundo plano con colas de trabajo.
