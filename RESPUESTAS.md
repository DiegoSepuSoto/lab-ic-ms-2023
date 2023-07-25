# Respuestas

Indica tu nombre a continuación: Diego Sepúlveda Soto

Por cada etapa agrega una sección abajo y escribe las respuestas a las preguntas de cada etapa.

## ETAPA 1

```
Revisa el contenido del diretorio sql_migrations.

¿Cuál es la diferencia entre los archivos con el verbo `Create` con los archivos con el verbo `Add`?
```
- Los archivos de migraciones con verbo *Create* tienen la misión de ejecutar la tarea inicial de migración, que es 
crear las tablas dentro del motor de base de datos para que luego, con los archivos de migraciones con verbo *Add* se 
puedan agregar registros a la base de datos. En los archivos no existe diferencia salvo las instrucciones SQL que 
contienen.

```
Revisa el contenido del archivo `docker-compose.yml`. 

¿Cómo se llama el servicio que se declara en el archivo `docker-compose.yml`?
```
- El servicio se llama **flyway**

```
¿Cuál es el comando que se ejecuta en el servicio declarado?
```
- Se ejecuta el comando **migrate** con dos flags; *-locations=filesystem:/flyway/sql* y *-connectRetries=60*

## ETAPA 2

```
¿Qué pasa si cambias el nombre del servicio de `postgres` a `db`? ¿Qué otros cambios tendrías que hacer?
```
- Al cambiar el nombre del servicio a **db** en el archivo docker-compose.yml (en la línea 3) no va a funcionar el 
comando tal como funcionó anteriormente, dado que es necesario cambiar también en nuestro archivo de secretos 
**.env** el nombre del servidor de PostgreSQL *POSTGRES_SERVER* de la siguiente manera:

    ```env
    POSTGRES_SERVER=db
    ```

## ETAPA 3

```
Revisa el archivo `movies-api/Dockerfile`.

¿Qué te llama la atención?
```
- Me llama la atención que presenta una construcción en multiples pasos para generar una imagen de docker liviana
(solo con el sistema operativo de debian) y sin las librerias relacionadas a la compilación del lenguaje Go

```
Revisa el archivo `docker-compose.yml`.

¿Cómo se relacionan el archivo `docker-compose.yml` y el archivo `movies-api/Dockerfile`?
```
- El archivo docker-compose.yml necesita conocer de antemano cómo construir la imagen del microservicio en go, dado 
que no puede ir a buscarla a internet. Entonces, en la declaración de docker-compose es necesario ubicar la ruta 
donde exista un **Dockerfile** válido

```
¿Qué crees que hace el atributo `context` debajo de `build` (está en la linea 6 del archivo `docker-compose.yml`)?
```
- El atributo **context** permite definirle a docker-compose la ruta/espacio donde ejecutar una variación a 
*docker build* para construir la imagen. Al señalar la ruta **./movies-api**, docker-compose sabrá de dónde copiar 
los archivos fuente para construir la imagen.

```
Intenta cambiar el puerto a 8080.
```
- No existe ningún cambio en la manera de llamar al archivo, salvo el puerto que se utiliza para consultar la
información (**8080**)

```
¿Qué pasa si en vez `movies-api` usas `localhost` para la variabla `BIND_IP`?
```
- No funciona, dado que dentro del contenedor de Docker existe una referencia muy distinta al concepto de 
**localhost** que se utiliza en otros sistemas diferentes, como nuestro equipo MacOS/Windows/Linux