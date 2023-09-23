![logo](assets/logo.png)

# Integración de CABAPROP

¡Bienvenido al portal de integración de CABAPROP! En esta documentación, encontrarás todas las indicaciones necesarias para integrar y publicar propiedades en el portal CABAPROP de manera eficiente. También proporcionamos ejemplos prácticos para ayudarte a comenzar rápidamente.

## Contenido de la Documentación

1. **Guía de Integración**: Comienza con nuestra guía paso a paso sobre cómo integrar tus propiedades con CABAPROP. Aprenderás cómo enviar datos, gestionar propiedades y mucho más.

2. **Ejemplos de Integración**: Ofrecemos ejemplos de código y casos de uso comunes para que puedas entender mejor cómo funciona la integración.

3. **Acceso a Swagger**: Para una referencia detallada de todos los endpoints de la API, puedes acceder a nuestra documentación Swagger en el siguiente enlace:

   [Documentación Swagger](https://cabaprop.ar/api/v1/integration-docs#/)

## Primeros pasos

1. Antes de comenzar, asegúrate de tener acceso a tus credenciales de integración proporcionadas por CABAPROP. Cada inmobiliario matriculado tiene acceso al portal de administración donde puede conseguir las credenciales y enviartelas.

    [Crear Credenciales](Credenciales.md)

2. Revisar la documentación de la API para familiarizarse con los diferentes endpoints y sus parámetros.

    [Documentación Swagger](https://cabaprop.ar/api/v1/integration-docs#/)

3. Tenemos disponible un entorno de test para que puedas realizar todas las pruebas necesarias antes de publicar tus propiedades en el portal CABAPROP. Para acceder a este entorno, enviaremos las credenciales a cada integrador que nos contacte.

    > **IMPORTANTE**
    >
    > Las credenciales de pruebas son válidas únicamente para el entorno de pruebas. Una vez que hayas finalizado las pruebas, debes utilizar las credenciales de producción para publicar tus propiedades en el portal CABAPROP.

4. Revisar Ejemplos de Integración para ver casos de uso comunes.

    * [Obtener Token](Ejemplos.md#obtener-token)
    * [Mis Datos](Ejemplos.md#mis-datos)
    * [Mis Propiedades](Ejemplos.md#mis-propiedades)
    * [Publicar Propiedad](Ejemplos.md#publicar-propiedad)
    * [Actualizar Propiedad](Ejemplos.md#actualizar-propiedad)
    * [Eliminar Propiedad](Ejemplos.md#eliminar-propiedad)

## Soporte Técnico

Si tienes alguna pregunta o encuentras algún problema durante el proceso de integración, no dudes en ponerte en contacto con nuestro equipo de soporte técnico. Estamos aquí para ayudarte en todo momento.

Para poder contactar al soporte técnico, es necesario que completes el siguiente formulario.

[COMPLETAR FORMULARIO](https://google.com)


> **CONTENIDO:** **Listado de los diferentes contenidos en esta documentación**
>
> + [Language Specification][specification]
> + [Examples][API Blueprint Examples]
> + [Glossary of Terms][API Blueprint Glossary of Terms]
> + [API Blueprint Map][map]
> + [Tools for API Blueprint][Tooling Section]


```apib
# GET /message
+ Response 200 (text/plain)

        Hello World!
```
