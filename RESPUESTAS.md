# Respuestas

Indica tu nombre a continuación: Diego Sepúlveda Soto

Por cada etapa agrega una sección abajo y escribe las respuestas a las preguntas de cada etapa.

## ETAPA 1

```
Revisa el contenido del diretorio sql_migrations.

¿Cuál es la diferencia entre los archivos con el verbo `Create` con los archivos con el verbo `Add`?
```
- Los archivos de migraciones con verbo *Create* tienen la misión de ejecutar la tarea inicial de migración, que es crear las tablas dentro del
motor de base de datos para que luego, con los archivos de migraciones con verbo *Add* se puedan agregar registros a la base de datos. En los archivos no existe diferencia salvo las instrucciones SQL que contienen.

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

Escribe respuestas de la etapa 2 acá

...