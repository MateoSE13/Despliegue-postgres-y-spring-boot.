 ## 1. Título
Despliegue de PostgreSQL y Spring Boot con Docker Compose


## 2. Tiempo de duración
**20 minutos**


## 3. Fundamentos
Docker Compose permite definir y ejecutar aplicaciones en múltiples contenedores mediante un archivo de configuración YAML, simplificando la configuración y conexión de servicios.

En este caso:
- **PostgreSQL**: Sistema de bases de datos relacional robusto.
- **PgAdmin**: Herramienta gráfica para gestionar PostgreSQL.

La práctica incluye:
1. Configuración de contenedores para PostgreSQL y PgAdmin.
2. Generación de un artefacto `.jar` de una aplicación Spring Boot.
3. Creación de un contenedor Docker para la aplicación Spring Boot.

---

## 4. Conocimientos previos
- Comandos básicos en Docker y Docker Compose.
- Conceptos de bases de datos.
- Familiaridad con YAML.

---

## 5. Objetivos a alcanzar
- Configurar contenedores para PostgreSQL y PgAdmin con Docker Compose.
- Crear un contenedor para una aplicación Spring Boot.
- Comprobar el funcionamiento del despliegue.

---

## 6. Equipo necesario
- Computadora con Docker y Docker Compose instalados.
- Proyecto de Spring Boot descargado o disponible.
- Cuenta en Docker Hub para obtener imágenes.

---

## 7. Material de apoyo
- [Documentación oficial de Docker Compose](https://docs.docker.com/compose/).
- [Documentación de PostgreSQL](https://www.postgresql.org/).
- [Guía básica de comandos Docker](https://docs.docker.com/engine/reference/commandline/docker/).

---

## 8. Procedimiento

### Paso 1: Crear la base de datos
1. Crear un archivo `docker-compose.yml` con el siguiente contenido:
  ![image](https://github.com/user-attachments/assets/af537460-7a33-409a-93be-d44a5c6172f7)

Iniciar los contenedores:

![image](https://github.com/user-attachments/assets/e686bfef-2348-43a7-9970-dd29a5a56ecd)

Acceder a PgAdmin en http://localhost:5050 con las credenciales configuradas:

![image](https://github.com/user-attachments/assets/6485f435-2215-4e3b-bb97-61e93c2312d3)

![image](https://github.com/user-attachments/assets/c3a76de7-94da-415c-8ea6-ccd49bf5880e)


Paso 2: Configurar el proyecto Spring Boot
Descargar el proyecto:

git clone https://github.com/maguaman2/tendencias-mar22-security
cd tendencias-mar22-security

Configurar el archivo application.yml con los datos de conexión a PostgreSQL:
![image](https://github.com/user-attachments/assets/b02c10f2-d41f-4914-968f-542549e9c0df)


Paso 3: Generar el artefacto .jar
Crear un contenedor Maven para compilar el proyecto:



Verificar que el comando muestra:
![image](https://github.com/user-attachments/assets/2962bf4d-5594-4363-8a86-7b5901513fbb)
![image](https://github.com/user-attachments/assets/8ff38153-f63d-402e-aed7-e09cc6168835)

Crear la imagen Docker:

`docker build -t myapp .`

Ejecutar el contenedor de la aplicación:
 `docker run -d --network db_default -p 8081:8081 myapp`

Paso 5: Comprobar el funcionamiento
Abrir el navegador en  `http://localhost:8081/users`.

Verificar que la aplicación devuelve un JSON con la información esperada.
![image](https://github.com/user-attachments/assets/7e24236a-a411-4d71-af7c-ea6d1b5a10ed)


9. Resultados esperados
Contenedores de PostgreSQL, PgAdmin y Spring Boot ejecutándose correctamente.
Acceso exitoso a PgAdmin para administrar PostgreSQL.
Funcionamiento correcto de la aplicación Spring Boot con respuesta en /users.


10. Bibliografía
Merkel, D. (2014). Docker: Lightweight Linux Containers for Consistent Development and Deployment. Linux Journal, 2014(239), 2.
Kane, A. (2024). Docker in Action, Second Edition. Manning Publications.
Pahl, C., & Brogi, A. (2016). Cloud Container Technologies: A State-of-the-Art Review. IEEE Transactions on Cloud Computing, 5(4), 667-678.
