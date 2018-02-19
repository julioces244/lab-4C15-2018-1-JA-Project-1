# [Guía de Código](https://github.com/Mayccoll/guia-de-codigo)


## Introducción

Una guía de estilo de un lenguaje de programación es un conjunto de recomendaciones sobre la forma de dar formato a los programas. El interés de utilizar un estilo específico es facilitar la re utilización de código y la detección de errores. Existen muchos estilos de programación y no se puede decir que uno sea mejor que otro, pero sí que es conveniente adoptar algún estilo determinado y utilizarlo de forma consistente.

Esta guia se basa en las recomendaciones hechas por el grupo PHP-FIG (PHP Framework Interop Group)[1] en el cual participan los autores de los frameworks PHP mas populares.

[1] - [PHP-FIG](http://www.php-fig.org/)

## Referencias

[PHP-FIG](http://www.php-fig.org/)

[Code Guide by @mdo](http://adrianayala.mx/code-guide/es/)

[Guía de estilo para PHP](http://www.mclibre.org/consultar/php/otros/ot_guiaestilo.html)

## Guia

- Los archivos DEBEN emplear solamente la codificación UTF-8 sin BOM para el código PHP.

## Comentarios

- Todo archivo debe estar comentado en la cabecera.

```php
<?php
/**
* Nombre del archivo
* Ruta:              /ruta/archivo
* Fecha Creación:    18/Ene/2014
*
* Descripción breve
*
* Descripción extensa (opcional)
*
* @author           Fulanito de Tal <fulanito@example.com>
* @copyright        2007 Fulanito de Tal
* @license          GPL 2 or later
* @version          2007-02-06
* @link             http://www.example.org
*
* Revisiones:
*       Bob (18/Ene/2014)   - Descripción
*       Susi (18/Ene/2014)  - Descripción Método modificado
*                           - Otro cambio  
*/
?>
```

Mas info: http://en.wikipedia.org/wiki/Javadoc

- Todos los métodos deben estar comentados.

```php
<?php
/**
 * El sistema no está disponible.
 *
 * @param string $message
 * @param array $context
 * @return null
 */
?>
```

- Delimitadores de bloque PHP

Los fragmentos PHP deben delimitarse con <?php ... ?> y no con <? ... ?>.

```php
<?php
    ......
    ......
?>
```

También se puede usar

```php
<?= $this->var ?>
```

## Longitud de línea

- No se deben superar los 85 caracteres por línea.

- Al partir una línea, la segunda y siguientes líneas deben sangrarse 4 espacios. Si es posible, estas líneas deben empezar por un operador.

## Instrucciones por línea

- Se aconseja no incluir más de una instrucción por línea.

## Espacios en blanco

- [PEAR] Después de una coma, debe haber un espacio en blanco.

```php
<?php
    $var = foo($bar, $cel, $ona);
?>
```

- [PEAR] Cualquier operador binario (por ejemplo: + - * / = . == && || ? : ) debe estar rodeado de espacios en blanco.

```php
<?php
    $cmTotal = 100000 * $km + 100 * $m + $cm;
?>
```

- [PEAR] Los operadores unarios (por ejemplo: ! ++ --) deben unirse a su argumento sin espacios en blanco.

```php
<?php
    $correcto = !$error;
?>
```

## Líneas en blanco

- Se aconseja separar con líneas en blanco las diferentes partes de un programa (recogida de datos, mensajes de error, respuesta del programa, etc.).


## Comillas dobles y simples

-Se aconseja delimitar las cadenas con comillas dobles (") en vez de con comillas simples ('). Se aconseja también que el código html generado por PHP incluya comillas dobles:

```php
<?php
    print "<p style=\"text-align: center\">Hello</p>";
?>
```

## Nombres de variables

- Emplear una convención de pseudo-espacios de nombres con prefijos en los nombres de las clases con el formato Proveedor_.

```php
<?php
$nombre             = "Fulano";
$nombre_alumno      = "Mengano";
$nombre_profesor    = "Zutano";
?>
```

##  Alineación de definiciones de variables

- [PEAR] Si se definen varias variables, se deben alinear las igualdades con espacios en blanco para facilitar la legibilidad.

```php
<?php
$nombre             = "Fulano";
$nombre_alumno      = "Mengano";
$nombre_profesor    = "Zutano";
?>
```

## Constantes

- Las constantes deben escribirse en mayúsculas y separando las palabras con guiones bajos (_).

- Las constantes true, false y null debe escribirse en minúsculas.

## Sangrado


- Se debe utilizar un sangrado de 4 espacios (soft-tabs) y no utilizar tabuladores. En estructuras anidadas, se acumularán los sangrados.

```php
<?php
if (condicion1) {
    accion1;
} else {
    accion2;
    if (condicion3) {
        accion3;
    } else {
        accion4;
    }
}
?>
```

## Estructuras de control

- Las estructuras de control deben tener un espacio entre la palabra reservada y el paréntesis inicial, para distinguirlas de las funciones.

- En los bloques de sentencias deben utilizarse siempre llaves, incluso cuando podrían omitirse (por ejemplo, cuando el bloque está formado por una única sentencia). La llave de apertura debe situarse al final de la línea y la llave de cierre debe situarse al principio de la línea.

Ejemplos de estructuras de control:

```php
<?php
if (condicion1 || condicion2) {
    accion1;
} elseif (condicion3 && condicion4) {
    accion2;
} else {
    accionpredeterminada;
}
?>
```

```php
<?php
for (expresión_inicial; expresión_final; expresión_paso) {
    bloque_de_sentencias
}
?>
```

```php
<?php
foreach ($matriz as $valor) {
    bloque_de_sentencias
}
?>
```

```php
<?php
while (expresión) {
    bloque_de_sentencias
}
?>
```

```php
<?php
do {
    bloque_de_sentencias
} while (expresión)
?>
```

```php
<?php
switch (condicion) {
case 1:
    accion1;
    break;

case 2:
    accion2;
    break;

default:
    accionpredeterminada;
    break;
}
?>
```

## Expresiones lógicas

- No es necesario comparar las variables booleanas con los valores true o false, se aconseja utilizar directamente la variable o su negación.

```php
<?php
if ($correcto) {
    print "<p>Es correcto</p>";
}
if ($correcto) {
   print "<p>Es correcto</p>";
}
?>
```

- Al concatenar expresiones lógicas sencillas, no es necesario escribir cada expresión entre paréntesis.

```php
<?php
if ($numero < 0 || $numero > 100) {
    print "<p>El número no está en el intervalo [0, 100]</p>";
}
?>
```

## Definición de funciones

- Las funciones deben declararse de acuerdo con el estilo "BSD/Allman":
- Los argumentos con valores predeterminados se deben colocar al final de la lista de argumentos.
- Las funciones deben devolver algún valor.

```php
<?php
Class FooClass {
    function fooFuncion($arg1, $arg2 = '')
    {
        if (condicion) {
            sentencia;
        }
        return $val;
    }
}
?>
```

##  Llamadas a funciones

- No debe haber espacios entre el nombre de la función, el paréntesis inicial y el primer argumento.
- Debe haber espacios tras las comas que separen argumentos.
- No debe haber espacios entre el último argumento, el paréntesis final y el punto y coma.

```php
<?php
    $var = foo($bar, $cel, $ona);
?>  
```

## Bibliotecas

- [PEAR] Para incluir bibliotecas cuya inclusión no depende de ninguna condición, debe utilizarse require_once y no deben utilizarse paréntesis alrededor del nombre de la biblioteca.

```php
<?php
    require_once "biblioteca.php";
?>
```

-----
By: Mayccoll
https://github.com/Mayccoll/guia-de-codigo