
# Comunidad Fiuba Remake
Info sobre los servicios actuales

## Servicios

- [Archivos](#archivos)
- [Usuarios](#usuarios)
- [Deploy](#deploy)
- [Likes](#likes)
- [000webhost](#000webhost)
- [404 SPA](#404-spa)
- [Apps Script](#apps-script)

## Archivos
Los archivos se suben directamente a Drive usando [Apps Script](#apps-script)

### Uso Actual

Actualmente los archivos solo se suben con la informacion del nombre, y estan todos en una sola carpeta "Archivos".

### Problemas

La informacion de los archivos, por ejemplo de que materia es, se guarda en un host aparte [000webhost](#000webhost).

Hay un tamaño maximo de 15 mb approx para los archivos que se suben de esta manera.


### Pros

Al guardar las cosas en drive tenemos bastante espacio disponible en la cuenta, por lo que no necesitamos un host para esto. 


## Usuarios

El login de usuarios se maneja directamente con firebase

### Uso Actual

Se usa firebase solo para verificar a los usuarios con google, y no se guarda mas información

### Problemas

La informacion de los usuarios, por ejemplo su nombre, se guarda en un host aparte [000webhost](#000webhost).

### Pros

Es facil de usar
## Deploy
La pagina esta deployada usando github pages

### Uso actual

El frontend del proyecto esta hecho en React y se buildea para poder usarlo en github pages.


### Problemas

Github pages no tiene el mejor soporte para spa y la unica pagina indexada es la pagina principal, porque para llegar al resto se usa un mecanismo que los crawler no permiten ver [404 SPA](#404-spa)

Si no usamos una SPA, hay que buscar alguna manera de que cada archivo pueda tener un link especifico e indexable.


### Pros

El frontend va a estar siempre activo y no dependemos de otro host que pueda limitarnos el tiempo activo o los recursos.
## Likes

Los likes se guardan en la base de datos 


### Uso actual

Actualmente los likes se cargan en la base de datos como una relacion entre la tabla de usuarios y la de posts.


### Problemas

Los likes se guardan en el host [000webhost](#000webhost).

## 000webhost

Toda la informacion sobre los archivos y los usuarios se guarda en una base de datos en este host

### Problemas

Se termina la version gratuita el 20/3/2024

El codigo no esta vinculado a un repositorio de github y es dificil de manipular

Esta escrito en php (Laravel)


### Pros

000webhost nunca nos dio problemas de recursos o de tiempo activo
## Apps Script

Se usa apps script para poder manejar el drive mediante codigo

### Problemas

No es un host o un servidor como tal, cada llamada a un script se ejecuta de manera paralela y no se pueden coordinar, llevando en muchos casos a una race condition que provoca que se pierdan datos si eso no se tiene en cuenta.


### Pros

Podemos ejecutar funciones sin necesidad de un host y manejar mediante el codigo el drive.

Tiene muchas otras herramientas que no estamos usando y podrian ser utiles.

## 404 SPA

Para que se pueda acceder a un link especifico como:

https://comunidad-fiuba.github.io/post/formulas-para-fisica-1

Se usa un redireccionamiento desde la pagina de error 404, ya que github no reconoce ninguna otra pagina que no sea la pagina de inicio. Cuando se accede a un link especifico, github envia el html de la pagina de error 404, ahi se guarda el link al que el usuario intentó acceder y se redirecciona a la pagina de inicio, una vez cargada la pagina de inicio se vuelve a redireccionar hacia la pagina original que el usuario intento acceder.