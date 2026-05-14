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
