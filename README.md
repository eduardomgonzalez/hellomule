# hellomule

Proyecto Mule 4 de prueba creado en Anypoint Studio.

El objetivo inicial es tener una aplicacion simple para practicar desarrollo, configuracion por ambiente, versionado con Git y despliegue de servicios Mule.

## Estado actual

La aplicacion expone dos endpoints HTTP:

- `GET /hellomule`: devuelve una respuesta JSON basica de la aplicacion.
- `GET /health`: devuelve el estado de salud de la aplicacion.

En ejecucion local, la URL base por defecto es:

```text
http://localhost:8081
```

Ejemplos:

```text
GET http://localhost:8081/hellomule
GET http://localhost:8081/health
```

## Estructura principal

```text
src/main/mule/
  global.xml       Configuracion global del listener HTTP y properties por ambiente
  hellomule.xml    Flows principales de la aplicacion

src/main/resources/
  config.yaml      Properties comunes de la aplicacion
  dev.properties   Properties del ambiente dev

docs/
  hellomule-baseline.md
```

## Configuracion

La aplicacion usa properties para separar configuracion del codigo.

Actualmente el listener HTTP toma host y puerto desde:

```text
http.listener.host
http.listener.port
```

Tambien incluye configuracion de Secure Properties para leer valores cifrados desde archivos por ambiente:

```text
${env}.secure.properties
```

La clave de descifrado se recibe por property externa:

```text
secure.key
```

## API Manager

La aplicacion esta preparada para registrarse en API Manager mediante API Autodiscovery.

El `api.id` identifica la API Instance creada en API Manager y se usa en `global.xml` para vincular el flow principal:

```text
api.id
```

En CloudHub tambien se configuran las credenciales del environment para que Mule pueda conectarse con Anypoint Platform:

```text
anypoint.platform.client_id
anypoint.platform.client_secret
```

Estos valores deben cargarse como properties del runtime y protegerse en Runtime Manager cuando corresponda.

Sobre la API Instance se pueden aplicar politicas desde API Manager. Actualmente el proyecto se usa para practicar Client ID Enforcement, que permite exigir credenciales de aplicacion cliente antes de consumir la API.

Cuando esta politica esta activa, las llamadas deben enviar las credenciales de cliente aprobadas por API Manager, por ejemplo mediante Basic Auth o headers equivalentes segun la configuracion de la policy.

Los archivos locales o sensibles no se versionan, por ejemplo:

- `local.properties`
- `*.secure.properties`
- `target/`
- metadata local de Anypoint Studio/Eclipse

## Versionado

Este repositorio se usa para guardar la evolucion del proyecto y poder volver a puntos anteriores si algun cambio rompe el flujo.

La idea es mantener commits chicos y claros a medida que se agreguen nuevos flows, configuraciones, conectores o documentacion.

## Notas

Este README es una base inicial. Se ira actualizando junto con el crecimiento del proyecto.
