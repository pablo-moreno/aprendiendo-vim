# :student: Aprendiendo VIM

Notas tomadas a partir de vimtutor.

## :thinking: Modos de VIM

Vim tiene tres modos:

 - Modo normal (NORMAL)
 - Modo de inserción (INSERT)
 - Modo visual (VISUAL)

El modo normal es en el que nos pasaremos la mayor parte del tiempo
y sobre el que realizaremos la mayoría de operaciones.

El modo de inserción es en el que añadiremos texto al documento.

El modo visual nos permite seleccionar texto para hacer operaciones con él. 

## :arrow_left: :arrow_up: :arrow_down: :arrow_right: Moviéndonos por el documento

Para movernos a través del documento utilizaremos las teclas H (<), J (v), K (^) y L (>)

Comandos útiles para movernos rápidamente:

- `gg`: Nos lleva al principio del documento.
- `G`: Nos lleva al final del documento.
- `<número>G`: nos lleva a la línea del número especificado.
- `0`: Nos lleva al principio de la línea en la que estamos.
- `$`: Nos lleva al final de la línea en la que estamos.
- `w`: (Word) Nos avanza el cursor al principio de la siguiente palabra.
- `b`: (Backwards) Nos retrocede el cursor al principio de la palabra anterior.
- `e`: (End of word) Nos lleva al último carácter de la palabra.
- `f<carácter>`: (For) Nos lleva al siguiente carácter que le especifiquemos.  
- `F<carácter>`: Hace lo mismo que `f` pero hacia atrás.
- `t<carácter>`: (To) Nos lleva al carácter inmediatamente anterior al que hemos especificado.
- `T<carácter>`: Lo mismo que `t` pero hacia atrás.
 

Si anteponemos un número al comando nos realiza el desplazamiento tantas veces como
hayamos especificado.

Por ejemplo: 

```
2w: Nos desplaza las dos siguientes palabras 
3b: Nos desplaza tres palabras hacia atrás
7e: Nos lleva al final de la 7ª palabra siguiente desde donde estamos.
```

## :x: Borrando cosas

Podemos utilizar las siguientes instrucciones para borrar cosas:

- `x`: Borra el carácter sobre el que tenemos el cursor.
- `d`: Borra la entidad que especifiquemos. Por ejemplo, para borrar una palabra sería `dw`.

Podemos añadir modificadores para borrar una o varias entidades de golpe.

Por ejemplo:

```
6x: Nos borra los 6 siguientes caracteres
d2w: Nos borra las dos siguientes palabras.
d$: Nos borra desde el cursor hasta el final de la línea
```

## :arrow_right_hook: Deshacer y rehacer.

Para deshacer la última acción podemos usar `u`.

Para rehacer, pulsaremos CTRL + R

## :clipboard: :scissors: Copiar, cortar y pegar

Para cortar texto, tenemos que borrar en primer lugar el texto que deseemos cortar, 
desplazarnos a donde lo queremos insertar y usar el comando `p` (PUT).

Por ejemplo:

```sh
d3w: Borramos tres palabras
25G: Nos desplazamos a la línea 25
p: Pegamos las 3 palabras que hemos cortado.
```


Para copiar, utilizaremos el comando `y<modificador>` (yank) y de nuevo `p` (PUT) para pegarlo 
donde deseemos.

```sh
y3w: Copiamos tres palabras
25G: Nos desplazamos a la línea 25
p: Pegamos las 3 palabras que hemos copiado.
```


## :abc: Editar texto

Para reemplazar texto tenemos varios comandos:

- `r`: (Replace) Nos reemplaza el carácter en el que nos encontramos por otro.
- `c<entidad>`: (Change) Nos borra la entidad que deseemos cambiar y nos pone en modo de inserción.
   
## :pencil: Alternativas para entrar en modo de inserción

- `SHIFT + I`: Nos lleva al primer carácter que no esté en blanco (ignora espacios) y entramos.
- `a`: Nos abre el modo de inserción en el siguiente carácter a nuestro cursor.
- `A`: Nos lleva al final de la línea en la que estamos y nos abre el modo de inserción.
- `o`: Nos abre el modo de inserción en la siguiente línea
- `O`: Nos abre el modo de inserción en la línea anterior.
- `s`: Nos borra el carácter en el que estamos y nos abre el modo de inserción.
- `S`: Borra toda la línea y nos abre el modo de inserción.
- `c<modificador>`: Nos borra lo que le especifiquemos y abre modo inserción.
- `C`: Borra desde el cursor hasta el final de la línea.

## :rowboat: Moviéndonos a través de simbolos de apertura y cierre

Para movernos fácilmente los símbolos de apertura y cierre, como `()`, `[]`, `{}`, 
podemos utilizar el comando `%`, que nos lleva desde la apertura al cierre, y viceversa.

## :question: Búsqueda en el documento

Para buscar en el documento podemos utilizar `/<texto` (si queremos buscar hacia 
adelante) o `?<texto>` si lo queremos hacer hacia atrás.

Para avanzar al siguiente registro encontrado, utilizaremos el comando `n` (next) o `N` en caso que queramos volver hacia atrás.

Para volver al punto en el que estábamos antes de hacer la búqueda podemos usar `CTRL + O`.

Si quisiéramos volver de nuevo a la búsqueda, tendremos que usar `CTRL + i`

## :scroll: Reemplazando texto

Para reemplazar texto usaremos el siguiente comando:

```
:s/textoviejo/textonuevo/g
```

Si queremos reemplazarlo en todo el documento, tendremos que añadir el modificador `%` previo al comando

```
:%s/textoviejo/textonuevo/g
```

Podemos especificar el rango de líneas del documento entre las que queremos que actúe.

Por ejemplo, para cambiar todo desde la línea 1 hasta la 25:

```
:1,25%s/textoviejo/textonuevo/g
```

Si queremos revisar cada cambio que queremos hacer, podemos añadir un prompt que nos va a preguntar
si realmente queremos reemplazar o no el texto:

```
:%s/textoviejo/textonuevo/gc
```

## :wrench: Ejecutando comandos desde VIM

Para ejecutar un comando del sistema desde VIM podemos hacerlo escribiendo `:!<nombre del comando>`.

Por ejemplo:

```
:!ls -la
```
