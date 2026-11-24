# Sistema Bibliotecario

Proyecto del taller de CI/CD. PostgreSQL se ejecuta en Docker Compose y utiliza
un volumen persistente para conservar los datos de la base de datos.

## Requisitos

- Git
- Docker Engine con Docker Compose

## Configuracion

El archivo `.env` local contiene la contrasena de PostgreSQL y no se versiona.
Configura `POSTGRES_PASSWORD` en ese archivo antes de iniciar el servicio.

## Iniciar PostgreSQL

Desde la carpeta del proyecto, ejecuta:

```powershell
docker compose up -d
docker compose ps
```

PostgreSQL queda disponible en `localhost:5434`, con la base `biblioteca_db`
y el usuario `biblioteca`.

Para entrar en `psql`:

```powershell
docker compose exec postgres psql -U biblioteca -d biblioteca_db
```

Si cambias la configuracion del contenedor y necesitas recrearlo:

```powershell
docker compose up -d --force-recreate
```

## Ramas de Git

- `master`: version estable.
- `desarrollo`: integracion del trabajo en curso.
- `pruebas`: validacion de cambios antes de integrarlos.

Publica cada rama con:

```powershell
git push -u origin master
git push -u origin desarrollo
git push -u origin pruebas
```
