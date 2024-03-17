# EditorConfig

EditorConfig es un archivo de configuración utilizado por desarrolladores y equipos de desarrollo para mantener consistencia en el estilo de codificación entre diferentes editores de texto y entornos de desarrollo. Sirve para especificar reglas de formato, como la indentación, el tipo de sangría, el estilo de fin de línea (por ejemplo, Unix, Windows o macOS), el estilo de codificación de caracteres, entre otros.

Al utilizar EditorConfig, los desarrolladores pueden asegurarse de que el código fuente mantenga un estilo uniforme, independientemente del editor o IDE que estén utilizando. Esto es especialmente útil en proyectos colaborativos donde diferentes personas pueden estar trabajando con diferentes configuraciones de editor.

En resumen, EditorConfig ayuda a mantener la consistencia en el estilo de codificación dentro de un proyecto, lo que facilita la lectura y comprensión del código, así como la colaboración entre desarrolladores.

## Instalación

[https://editorconfig.org/#download](https://editorconfig.org/#download)

## Como iniciarlo

Si estamos usando como editor de código [VS Code](https://code.visualstudio.com/) podemos instalar una extension llamada [EditorConfig](https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig) esto nos permitira tenerlo activo una vez que se cree el archivo de configuración.

## Archivo de configuración

Tendremos que crear un archivo en la raiz de nuestro proyecto con este nombre ``.editorconfig``

```txt
📦Tu-Proyecto
 ┣ 📂src
 ┃ # Aqui tenemos nuestro archivo .editorconfig
 ┣ 📜.editorconfig
 ┗ 📜README.md
```

### Primeros pasos

Una vez tenemos nuestro archivo ``.editorconfig`` dentro de el pondremos el siguiente texto.

```conf
root = true
```

Con esa linea indicamos que estamos en la raiz de nuestro proyecto y ya puede empezar a formatear nuestras identaciones.

### Comandos

#### Selectores

| Comando     |¿Qué hace?                                                                           |
|-------------|-------------------------------------------------------------------------------------|
| [*]         | Afecta a todos los archivos.                                                        |
| [*.py]      | Afecta a todos los archivos con la terminación ``.py``.                             |
| [*.{js.py}] | Afecta a todos los archivos con las siguientes termianciones.                       |
| [lib/**.js] | Afecta a todos los archivos de la carpeta lib con la terminación ``.js``.           |
| {package.json,.travis.yml} | Afecta solamente a los archivos ``package.json`` y ``.travis.yml``. |

Una vez tengamos identificados los archivos que queremos editar podemos empezar a poder las reglas que queremos que se mantengan en nuestro equipo.

| Comando                  | ¿Qué hace?                                                             | Valores admitidos                            |
|--------------------------|------------------------------------------------------------------------|----------------------------------------------|
| ident_style              | Decimos que queremos usar como identación                              | space, tab, unset                            |
| ident_size               | Decimos el tamaño de la identación.                                    | 0...4...8, unset                             |
| end_of_line              | Decimos como sera representado el final de línea                       | lf, cr, crkf                                 |
| charset                  | Decimos que tipo de charset queremos usar.                             | latin1, utf-8, utf-8-bom, utf-16be, utf-16le |
| trim_trailing_whitespace | Deicmos si queremos eliminar los espacion vacios al final de una línea | true, false                                  |
| insert_final_newline     | Decimos si queremos que se inserte una nueva linea al final            | true, false                                  |

### Diferencias

Diferencias de las opciones.

#### end_of_line

- ``lf``: Esta opción indica que se utiliza un solo carácter de línea (LF, Line Feed) para representar el final de cada línea en el archivo.
- ``cr``: Indica que se utiliza solo el carácter de retorno de carro (CR, Carriage Return) al final de cada línea.
- ``crkf``:  Indica que se utiliza una combinación de retorno de carro y avance de línea (CRLF, Carriage Return + Line Feed) al final de cada línea.

Estas opciones determinan cómo se representan los finales de línea en un archivo de texto, y pueden ser útiles para asegurar la compatibilidad entre diferentes sistemas operativos y editores de texto, donde las convenciones de fin de línea pueden variar (por ejemplo, Unix utiliza LF, Windows utiliza CRLF).

#### Charset

- `latin1`: También conocida como ISO 8859-1, es una codificación de caracteres de un byte que cubre la mayoría de los caracteres latinos básicos y se utiliza comúnmente en sistemas europeos.

- `utf-8`: Es una codificación de caracteres de longitud variable que puede representar cualquier carácter Unicode. Es ampliamente utilizado en la web y en muchos sistemas operativos y aplicaciones.

- `utf-8-bom`: Es similar a UTF-8, pero incluye un marcador de orden de bytes (BOM, Byte Order Mark) al principio del archivo para indicar el orden de los bytes en la secuencia de caracteres Unicode. Algunos editores y aplicaciones pueden requerir esto para detectar correctamente la codificación UTF-8.

- `utf-16be`: Es una codificación de caracteres Unicode de 16 bits big-endian, donde los bytes más significativos se almacenan primero. Es menos común que UTF-8 pero se utiliza en algunos sistemas y aplicaciones.

- `utf-16le`: Es similar a UTF-16BE, pero utiliza el orden de bytes little-endian, donde los bytes menos significativos se almacenan primero. Esta codificación también se utiliza en sistemas y aplicaciones específicas.

En resumen, estas codificaciones de caracteres difieren en cómo representan los caracteres y en su compatibilidad con diferentes juegos de caracteres y aplicaciones. Es importante elegir la codificación correcta según los requisitos de tu proyecto y los sistemas en los que se utilizará el código.

## Archivo de configuración base con buenas practicas

```conf
root = true

[*]
# Es el que esta mas estandarizado.
charset = utf-8
trim_trailing_whitespace = true
insert_final_newline = true
indent_style = space

# Esto se puede cambiar a 2 si se prefiere ya
# que algunos linters tienen errores si se usa 4.
indent_size = 4

# Windows, si fuera Unix podemos cambiar a lf
end_of_line = crlf

[*.md]
indent_size = 2

```

---

Puedes visitar la página oficial para ver si tu editor cuenta con algunas funcionalidad nuevas.
