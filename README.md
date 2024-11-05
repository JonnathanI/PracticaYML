# Informe: Generación de Contenedores usando Docker Compose

## Tiempo de Duración
El tiempo estimado para completar esta práctica es de aproximadamente 1 a 2 horas, dependiendo del nivel de familiaridad con Docker y la configuración de los contenedores.

## Fundamentos
Docker Compose es una herramienta que permite definir y ejecutar aplicaciones multi-contenedor en Docker. Mediante un archivo `docker-compose.yml`, es posible configurar y levantar múltiples servicios de manera sencilla, lo que facilita la gestión y orquestación de contenedores. En esta práctica, se utilizarán dos contenedores: uno para **PostgreSQL** y otro para **PgAdmin**.

## Conocimientos Previos
- Conocimiento básico de Docker.
- Familiaridad con el uso de la línea de comandos.
- Conceptos básicos de bases de datos, especialmente PostgreSQL.
- Conocimiento de la sintaxis de YAML y su uso en la configuración de servicios.

## Objetivos a Alcanzar
- Crear y configurar un archivo `docker-compose.yml` para levantar dos contenedores.
- Implementar un contenedor con PostgreSQL para gestionar bases de datos.
- Implementar un contenedor con PgAdmin para la gestión visual de las bases de datos.
- Aprender a interactuar con servicios que se comunican entre sí en un entorno de contenedores.

## Equipo Necesario
- Computadora con Docker y Docker Compose instalados.
- Acceso a la terminal o línea de comandos.

## Material de Apoyo
- [Documentación oficial de Docker](https://docs.docker.com/)
- [Documentación oficial de Docker Compose](https://docs.docker.com/compose/)
- [PostgreSQL](https://www.postgresql.org/)
- [PgAdmin](https://www.pgadmin.org/)

## Procedimiento
1. **Instalación de Docker y Docker Compose**: Asegúrate de tener Docker y Docker Compose instalados en tu máquina.
   
2. **Creación del archivo `docker-compose.yml`**:
    - Abre un editor de texto y crea un archivo llamado `docker-compose.yml`.
    - Agrega la configuración para los servicios de PostgreSQL y PgAdmin:
    
    ```yaml
    services:
     # Servicio de PostgreSQL
     postgres:
       image: postgres:latest
       container_name: postgres
       environment:
         POSTGRES_USER: admin
         POSTGRES_PASSWORD: admin
         POSTGRES_DB: mydatabase
       volumes:
         - postgres_data:/var/lib/postgresql/data
       ports:
         - "5432:5432"
   
      Servicio de pgAdmin
     pgadmin:
       image: dpage/pgadmin4:latest
       container_name: pgadmin1
       environment:
         PGADMIN_DEFAULT_EMAIL: admin@example.com
         PGADMIN_DEFAULT_PASSWORD: admin
       ports:
         - "8080:80"
       depends_on:
         - postgres
   
   volumes:
     postgres_data:
    ```

3. **Iniciar los contenedores**:
    - En la terminal, navega hasta la carpeta donde guardaste el archivo `docker-compose.yml`.
    - Ejecuta el comando `docker-compose up` para iniciar los contenedores.
      ![image](https://github.com/user-attachments/assets/61268887-36e8-4c08-af41-a854f1404398)


4. **Acceso a los contenedores**:
    - PostgreSQL estará accesible en el puerto `5432` en tu máquina.
    - PgAdmin podrá ser accedido a través de `http://localhost` en tu navegador.
      
    
    Ingresa a PgAdmin con las credenciales definidas (`admin@admin.com` y `admin`), y añade el servidor de PostgreSQL utilizando las credenciales configuradas en el contenedor `db` (`user` y `password`).
   ![image](https://github.com/user-attachments/assets/f5a732c7-aece-4e7b-9e28-fa27d0f7089b)


6. **Verificación**:
    - Abre PgAdmin y asegúrate de que el contenedor de PostgreSQL esté conectado correctamente.
    - Crea una nueva base de datos y realiza una conexión para confirmar que todo esté funcionando como se espera.
      ![image](https://github.com/user-attachments/assets/48438474-0373-4dfa-8ab5-d5bc6d1631e6)


## Resultados Esperados
- Los contenedores de PostgreSQL y PgAdmin deberían estar funcionando correctamente.
- Deberías poder acceder a PgAdmin a través del navegador y gestionar la base de datos PostgreSQL sin problemas.
- Las bases de datos creadas en PostgreSQL deberían ser visibles y gestionables a través de PgAdmin.

## Bibliografía
- Docker Documentation: https://docs.docker.com/
- Docker Compose Documentation: https://docs.docker.com/compose/
- PostgreSQL Documentation: https://www.postgresql.org/docs/
- PgAdmin Documentation: https://www.pgadmin.org/docs/
