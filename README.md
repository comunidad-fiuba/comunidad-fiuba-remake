
# Comunidad Fiuba Remake
Info sobre los servicios actuales

## Servicios

- [Archivos](archivos)
- [Usuarios](usuarios)
- [Deploy](deploy)
- [Likes](likes)




## Archivos
Los archivos se suben directamente a Drive usando Google Apps Scripts.

### Uso Actual

Actualmente los archivos solo se suben con la informacion del nombre, y estan todos en una sola carpeta "Archivos".

### Problemas

La informacion de los archivos, por ejemplo de que materia es, se guarda en un host aparte [000webhost](000webhost).

Hay un tamaño maximo de 15 mb approx para los archivos que se suben de esta manera.

## Usuarios

El login de usuarios se maneja directamente con firebase

### Uso Actual

Se usa firebase solo para verificar a los usuarios con google, y no se guarda mas información

### Problemas

La informacion de los usuarios, por ejemplo su nombre, se guarda en un host aparte [000webhost](000webhost).
## Deploy
La pagina esta deployada usando github pages

### Uso actual

El frontend del proyecto esta hecho en React y se buildea para poder usarlo en github pages.


### Problemas

Github pages no tiene el mejor soporte para spa y la unica pagina indexada es la pagina principal, porque para llegar al resto se usa un mecanismo que los crawler no permiten ver [404 SPA](404-spa)

Si no usamos una SPA, hay que buscar alguna manera de que cada archivo pueda tener un link especifico e indexable.
## Likes

(To do , en un rato vuelvo y termino de escribir esta seccion)
## 000webhost

Toda la informacion sobre los archivos y los usuarios se guarda en una base de datos en este host

### Problemas

Se termina la version gratuita el 20/3/2024

El codigo no esta vinculado a un repositorio de github y es dificil de manipular

Esta escrito en php (Laravel)
## 404 SPA

Para que se pueda acceder a un link especifico como:

https://comunidad-fiuba.github.io/post/formulas-para-fisica-1

Se usa un redireccionamiento desde la pagina de error 404, ya que github no reconoce ninguna otra pagina que no sea la pagina de inicio. Cuando se accede a un link especifico, github envia el html de la pagina de error 404, ahi se guarda el link al que el usuario intentó acceder y se redirecciona a la pagina de inicio, una vez cargada la pagina de inicio se vuelve a redireccionar hacia la pagina original que el usuario intento acceder.