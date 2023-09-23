![logo](assets/logo.png)

[🔙 Volver a inicio](Readme.md)

# Ejemplos

## Obtener Token

Una vez que cuentes con el ApiKey, puedes obtener el token en la sección Authentication del swagger.

## Mis Datos

Para obtener los datos del inmobiliario y sus diferentes sucursales, en la sección de Authentication del swagger, debes ingresar el token obtenido en el paso anterior.

Recibiras un Json similar a este:

```json
{
  "realEstate": {
    "id": 18033,
    "name": "Inmobiliaria Uno",
    "description": null,
    "logo": null,
    "socialNetworks": {},
    "email": "aspirante@uno.com",
    "old_id": null,
    "isActive": true,
    "created_at": "2023-09-21T21:39:38.730Z",
    "updated_at": "2023-09-21T21:39:38.730Z",
  },
  "branchOfficeId": [
    {
      "id": 18033,
      "branch_office_name": "Casa Central AVDA SANTA FE 1234",
      "isCentral": true,
      "isActive": true,
      "phoneNumber": "541130003058",
      "extraPhones": [],
      "openingHours": "No especificado",
      "address": "AVDA SANTA FE 1234",
      "barrio": 47,
      "email": "aspirante@uno.com",
      "whatsapp": null,
      "created_at": "2023-09-21T21:39:38.767Z",
      "updated_at": "2023-09-21T21:39:38.767Z"
    }
  ]
}
```

## Mis Propiedades

En la sección Api's Integration del swagger, puedes consultar las propiedades que tienes publicadas en CABAPROP.

Por ejemplo, en este curl puedes ver como obtener las propiedades publicadas en el tipo venta, los tipos de operaciones y otros recursos se pueden consultar en la sección Utils del swagger. [Documentación Swagger](https://cabaprop.ar/api/v1/integration-docs#/Utils)

```bash
curl -X 'POST' \
  'https://cabaprop.com.ar/api/integration/find-properties?offset=0&limit=10&realEstateId=18033' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "operationType": 1
}'
```

## Publicar Propiedad

En el ejemplo, publicaremos un departamento en venta recordando que todos las publicaciones deben ser de la ciudad de buenos aires.

Primero crearemos la propiedad con todos sus valores, y luego subiremos las imagenes, las publicaciones permanecen pendientes hasta que tengan minimo 3 imagenes.

>**IMPORTANTE**
>Para publicar una propiedad, debemos enviar si o si el campo Bra

```bash
curl -X 'POST' \
  'http://localhost:9000/api/integration' \
  -H 'accept: */*' \
  -H 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhcGlLZXkiOiIzdjd2aThpZHdpbmxqaGFxNm9odGZwbzZzcGNhbGoiLCJzZWNyZXQiOiJ1aDR6NGtiYTZzM2EzdTU0MHFrYXJsaXUxeGJtbGFxbm0xeWlicml4cW1xaWlqeThlaXkzbnI2MjZtYXhkNjY1IiwidXNlcklkIjoiZmM5NjQ5MjAtNGU3Ni00YmUyLTgyNmUtMDlmZmJiMjRmODA5IiwibmFtZSI6Ik1pQXBwIiwiaWF0IjoxNjk1NDgxNTUxLCJleHAiOjE2OTgxMDk1NTF9.hVpC6h2Tv7N1jhfmV_t9a9dz5vTUUWoYpEraQfjf35Y' \
  -H 'Content-Type: application/json' \
  -d '{
    "status": "published",
    "external_reference": "documentacionCabaprop1",
    "title": "Departamento en venta Documentación",
    "description": "Esto es una descripción para mi departamento",
    "real_estate_id": 18033,
    "branch_office_id": 18033,
    "operation_type": 1,
    "property_type": 1,
    "sub_property_type": 15,
    "location": {
      "barrios": [
        31,
        32
      ],
      "area_level_1": "Buenos Aires",
      "area_level_2": "Comuna 7",
      "cp": "C1406",
      "cp_suffix": "string",
      "letter": "string",
      "lat": -34.921452,
      "lng": -57.954528,
      "locality": "Buenos Aires",
      "street" : "Av. Rivadavia",
      "number": 1234
    },
    "share": {
      "active": true,
      "percent": 30
    },
    "surface": {
      "totalSurface": 100,
      "coveredSurface": 75,
      "uncoveredSurface": 25,
      "semiCoveredSurface": 25,
      "exclusiveSurface": 25
    },
    "antiquity": {
      "years": 10
    },
    "price": {
      "currency": 2,
      "total": 80000,
      "expenses": 1,
      "expensesCurrency": 10000
    },
    "characteristics": {
      "ambience": 1,
      "bedrooms": 1,
      "bathrooms": 1,
      "privateBathroom": 1,
      "toilettes": 0,
      "underground": true,
      "building": true,
      "accessibilities": true,
      "inhabited": true,
      "hasPoster": true
    },
    "ambiences_types": {},
    "video": "https://www.youtube.com/watch?v=123456789",
    "video360": "https://www.youtube.com/watch?v=123456789",
    "extras": {
      "serviciosEsenciales": {
        "abl": true,
        "aysa": true,
        "gas": true,
        "electricidad": true,
        "internet_wifi": true,
        "tv_cable": true,
        "telefono": true,
        "agua_corriente": true
      },
      "vista": {
        "calle": true,
        "pulmonManzana": false,
        "jardin": false,
        "plaza": true,
        "abierta": true
      },
      "seguridad": {
        "alarma": true,
        "puertaBlindada": false,
        "grupoElectrogeno": false
      },
      "calefaccion": {
        "ventilador": true,
        "aireAcondicionado": true,
        "split": true,
        "caldera_central": true,
        "caldera_individual": true,
        "calefaccion_central": true,
        "calefaccion_estufa_gas": true,
        "calefaccion_losa_central": true,
        "calefaccion_losa_individual": true,
        "calefaccion_radiadores_central": true,
        "calefaccion_radiadores_individual": true,
        "calefaccion_placas_bajo_consumo": true,
        "termotanque_calefon": true,
        "chimenea": true
      },
      "vigilancia": {
        "encargado": true,
        "encargado_virtual": true,
        "portero_electrico": true,
        "camaras": true,
        "vigilancia_24hs": true,
        "vigilancia_diurna": true,
        "vigilancia_nocturna": true,
        "vigilancia_fin_de_semana": true
      },
      "adicionales": {
        "termotanque_electrico": true,
        "termotanque_gas": true,
        "cocina_electrica": true,
        "cocina_gas": true,
        "amoblado": true,
        "placards": true,
        "cancha_paddle": true,
        "cancha_tenis": true,
        "gimnasio": true,
        "hidromasaje": true,
        "laundry": true,
        "microcine": true,
        "parrilla": true,
        "piscina": true,
        "sala_de_juegos": true,
        "sauna": true,
        "solarium": true,
        "spa": true,
        "sum": true,
        "centros_comerciales_cercanos": true,
        "escuelas_cercanas": true,
        "parques_cercanos": true,
        "estacionamiento_visitas": true
      }
    }
  }'
```

En el ejemplo, enviamos un json como en [este ejemplo](examples/createProperty.json) y recibimos un json como en [este ejemplo](examples/createPropertyResponse.json)
de respuesta, en el cual podemos ver que la propiedad se creo correctamente y que se encuentra pendiente de publicación, Tomaremos el id de la imagen del campo ***_id***

> **IMPORTANTE**
>
> El campo *external_reference* es un campo opcional que puede ser utilizado para identificar la propiedad en tu sistema. Este campo no se mostrará en el portal CABAPROP.


## Subir Imagenes y Planos

Para subir imagenes a una propiedad, debemos agregar el id de la propiedad en el endpoint de imagenes informado en swager, en el ejemplo, subiremos 1 imagen a la propiedad creada anteriormente.
Adicionalmente podremos subir planos y tambien videos por url, estos videos fueron subidos al momento de publicar, pero en el caso que necesitemos modificarlos o enviarlos en este momento, pueden hacerlo.

De esta manera estaremos subiendo una imagen enviando un archivo que se guardara en el servidor de CABAPROP, en el caso que quieran enviar una imagen por url, pueden hacerlo en el endpoint de subir propiedad agregando la llave images de esta manera, en ese caso, la imagen se mostrará desde la url enviada.
  
  ```json
  {
    "images": [
      {
          "url" : "https://http2.mlstatic.com/D_862027-MLA69003406493_042023-O.jpg",
          "title" : "Ejemplo URL",
          "originalname" : "Ejemplo URL",
          "filename" : null
      },
      {
          "url" : "https://http2.mlstatic.com/D_961640-MLA69003406489_042023-O.jpg",
          "title" : "Ejemplo URL",
          "originalname" : "Ejemplo URL",
          "filename" : null
      }
    ]
  }
  ```

```bash
curl -X 'PATCH' \
  'https://cabaprop.com.ar/api/integration/upload-multimedia/650f010c66578aecc5e5f80a' \
  -H 'accept: */*' \
  -H 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhcGlLZXkiOiIzdjd2aThpZHdpbmxqaGFxNm9odGZwbzZzcGNhbGoiLCJzZWNyZXQiOiJ1aDR6NGtiYTZzM2EzdTU0MHFrYXJsaXUxeGJtbGFxbm0xeWlicml4cW1xaWlqeThlaXkzbnI2MjZtYXhkNjY1IiwidXNlcklkIjoiZmM5NjQ5MjAtNGU3Ni00YmUyLTgyNmUtMDlmZmJiMjRmODA5IiwibmFtZSI6Ik1pQXBwIiwiaWF0IjoxNjk1NDgxNTUxLCJleHAiOjE2OTgxMDk1NTF9.hVpC6h2Tv7N1jhfmV_t9a9dz5vTUUWoYpEraQfjf35Y' \
  -H 'Content-Type: multipart/form-data' \
  -F 'image=@test-dgt-1.png;type=image/png' \
  -F 'houseMap=' \
  -F 'video=' \
  -F 'video360='
```

### Subir imagenes por url

Al subir imagenes por url, mostraremos las urls desde la cual se descargaron las imagenes, en el caso que no se puedan descargar, se mostrara un error.
Ejemplo, si subo una imagen que esta en https://miweb.com/imagen1.jpg, en la web de CABAPROP buscaremos la imagen en esa url.

```bash

```

# Actualizar Propiedad

Para actualizar una propiedad, debemos enviar el id de la propiedad y el apikey en el endpoint de actualizar propiedad informado en swager, en el ejemplo, actualizaremos la propiedad creada anteriormente.
El body debe ser el mismo que al crear una propiedad pero con los datos actualizados.
Por ejemplo, si quisieramos pausar una propiedad, enviamos el mismo body que al crear la propiedad pero con el campo status en "paused"
```bash
curl -X 'PATCH' \
  'http://localhost:9000/api/integration/basic-data/650f0b41fb6f0eb918dfe355' \
  -H 'accept: */*' \
  -H 'x-api-key: 3v7vi8idwinljhaq6ohtfpo6spcalj' \
  -H 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhcGlLZXkiOiIzdjd2aThpZHdpbmxqaGFxNm9odGZwbzZzcGNhbGoiLCJzZWNyZXQiOiJ1aDR6NGtiYTZzM2EzdTU0MHFrYXJsaXUxeGJtbGFxbm0xeWlicml4cW1xaWlqeThlaXkzbnI2MjZtYXhkNjY1IiwidXNlcklkIjoiZmM5NjQ5MjAtNGU3Ni00YmUyLTgyNmUtMDlmZmJiMjRmODA5IiwibmFtZSI6Ik1pQXBwIiwiaWF0IjoxNjk1NDgxNTUxLCJleHAiOjE2OTgxMDk1NTF9.hVpC6h2Tv7N1jhfmV_t9a9dz5vTUUWoYpEraQfjf35Y' \
  -H 'Content-Type: application/json' \
  -d '{
    "external_reference": "documentacionCabaprop1CON_IMAGENES",
    "status" : "published",
    "title": "Departamento en venta Documentación CON IMAGENES",
    "description": "Esto es una descripción para mi departamento",
    "real_estate_id": 18033,
    "branch_office_id": 18033,
    "operation_type": 1,
    "property_type": 1,
    "sub_property_type": 15,
    "location": {
      "barrios": [
        31,
        32
      ],
      "area_level_1": "Buenos Aires",
      "area_level_2": "Comuna 7",
      "cp": "C1406",
      "cp_suffix": "string",
      "letter": "string",
      "lat": -34.921452,
      "lng": -57.954528,
      "locality": "Buenos Aires",
      "street" : "Av. Rivadavia",
      "number": 1234
    },
    "share": {
      "active": true,
      "percent": 30
    },
    "surface": {
      "totalSurface": 100,
      "coveredSurface": 75,
      "uncoveredSurface": 25,
      "semiCoveredSurface": 25,
      "exclusiveSurface": 25
    },
    "antiquity": {
        "type" : 1,
      "years": 10
    },
    "price": {
      "currency": 2,
      "total": 80000,
      "expenses": 1,
      "expensesCurrency": 10000
    },
    "characteristics": {
      "ambience": 1,
      "bedrooms": 1,
      "bathrooms": 1,
      "privateBathroom": 1,
      "toilettes": 0,
      "underground": true,
      "building": true,
      "accessibilities": true,
      "inhabited": true,
      "hasPoster": true
    },
    "ambiences_types": {},
    "video": "https://www.youtube.com/watch?v=123456789",
    "video360": "https://www.youtube.com/watch?v=123456789",
    "extras": {
      "serviciosEsenciales": {
        "abl": true,
        "aysa": true,
        "gas": true,
        "electricidad": true,
        "internet_wifi": true,
        "tv_cable": true,
        "telefono": true,
        "agua_corriente": true
      },
      "vista": {
        "calle": true,
        "pulmonManzana": false,
        "jardin": false,
        "plaza": true,
        "abierta": true
      },
      "seguridad": {
        "alarma": true,
        "puertaBlindada": false,
        "grupoElectrogeno": false
      },
      "calefaccion": {
        "ventilador": true,
        "aireAcondicionado": true,
        "split": true,
        "caldera_central": true,
        "caldera_individual": true,
        "calefaccion_central": true,
        "calefaccion_estufa_gas": true,
        "calefaccion_losa_central": true,
        "calefaccion_losa_individual": true,
        "calefaccion_radiadores_central": true,
        "calefaccion_radiadores_individual": true,
        "calefaccion_placas_bajo_consumo": true,
        "termotanque_calefon": true,
        "chimenea": true
      },
      "vigilancia": {
        "encargado": true,
        "encargado_virtual": true,
        "portero_electrico": true,
        "camaras": true,
        "vigilancia_24hs": true,
        "vigilancia_diurna": true,
        "vigilancia_nocturna": true,
        "vigilancia_fin_de_semana": true
      },
      "adicionales": {
        "termotanque_electrico": true,
        "termotanque_gas": true,
        "cocina_electrica": true,
        "cocina_gas": true,
        "amoblado": true,
        "placards": true,
        "cancha_paddle": true,
        "cancha_tenis": true,
        "gimnasio": true,
        "hidromasaje": true,
        "laundry": true,
        "microcine": true,
        "parrilla": true,
        "piscina": true,
        "sala_de_juegos": true,
        "sauna": true,
        "solarium": true,
        "spa": true,
        "sum": true,
        "centros_comerciales_cercanos": true,
        "escuelas_cercanas": true,
        "parques_cercanos": true,
        "estacionamiento_visitas": true
      }
    }
  }'
```

Como respuesta recibiremos un status 200 con el siguiente body

```json
{
  "message": "Propiedad actualizada con éxito"
}
```

# Eliminar Propiedad
Para eliminar una propiedad, debemos enviar el id de la propiedad y el apikey en el endpoint de eliminar propiedad informado en swager, en el ejemplo, eliminaremos la propiedad creada anteriormente.
```bash
curl -X 'DELETE' \
  'https://cabaprop.com.ar/api/integration/logical/650f108283f4e7920c9b3486' \
  -H 'accept: */*' \
  -H 'x-api-key: 3v7vi8idwinljhaq6ohtfpo6spcalj' \
  -H 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhcGlLZXkiOiIzdjd2aThpZHdpbmxqaGFxNm9odGZwbzZzcGNhbGoiLCJzZWNyZXQiOiJ1aDR6NGtiYTZzM2EzdTU0MHFrYXJsaXUxeGJtbGFxbm0xeWlicml4cW1xaWlqeThlaXkzbnI2MjZtYXhkNjY1IiwidXNlcklkIjoiZmM5NjQ5MjAtNGU3Ni00YmUyLTgyNmUtMDlmZmJiMjRmODA5IiwibmFtZSI6Ik1pQXBwIiwiaWF0IjoxNjk1NDgxNTUxLCJleHAiOjE2OTgxMDk1NTF9.hVpC6h2Tv7N1jhfmV_t9a9dz5vTUUWoYpEraQfjf35Y'
```

Como respuesta recibiremos un status 200 con el siguiente body

```json
{
  "message": "Propiedad eliminada con éxito"
}
```

[🔙 Volver a inicio](Readme.md)