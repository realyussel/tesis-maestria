# ¿Por qué no debes escribir un libro con un procesador de texto convencional?

En la actualidad los libros se distribuyen en múltiples formatos (HTML, PDF, MS Word y ePub) para diferentes propósitos, y un procesador de texto convencional no puede generar continuamente todos estos productos.

Ademas, en los procesadores de texto convencionales, formatear un texto puede ser algo tedioso y llevar mucho tiempo; como hacer que las figuras se vean bien y corregir los saltos de página rebeldes. 

Así que el `flujo de trabajo` más eficaz, consiste en realizar un solo manuscrito (usando código) para componer, compilar y publicar el libro de forma simultánea en todos los formatos que se desee.

Es decir, no es bueno usar Microsoft Word o similares (como OpenOffice) para crear un libro.
Lo mejor es usar un lenguaje de marcado (código), que nos permitá concentrarnos en el contenido "sin preocuparnos por aplicar formatos". Además de que nos ayudará a tener todo organizado y consistente, y trabajar en equipo.

# Lenguajes de marcado

Usted puede usar los siguientes "lenguajes de marcado" que facilitarán la redacción (hay más, pero estos son los 3 principales):

* Markdown,
* reStructuredText (RST),
* AsciiDoc.

Con ellos usted puede marcar el contenido (texto) según corresponda; para producir múltiples formatos de salida: HTML, PDF, Word, entre otros.

# Markdown

Para cualquier redacción rápida, pero **simple**. recomiendo usar Markdown, que es está muy bien representado por GitHub y otras herramientas de escritorio.

Pero, para algo más complejo (como la creación un artículo o libro completo) recomiendo usar [`RMarkdown`](https://rmarkdown.rstudio.com/), es decir, el ‘sabor’ de Markdown para la sintaxis de R.

> No es necesario que sea un experto en el lenguaje R.

Aunque R es uno de los principales lenguajes utilizados para la ciencia de datos, con `RMarkdown` y empleando el paquete `bookdown` podemos escribir un libro que se pueda compilar facilmente a direferentes formatos.

# Bookdown

Bookdown, gestionará todo el formato por usted; Bookdown puede manejar automáticamente toda la numeración de sus secciones, figuras y tablas, así como generar automáticamente páginas de contenido y listas de tablas y figuras.

## Instalación

1. Primero hay que descargar e instalar [`R`](https://cran.r-project.org/).
	Haga clic en "install R for the first time"...
1. Aunque no es necesario, se recomienda utilizar el IDE [`RStudio`](https://rstudio.com/products/rstudio/download/) que hará que R sea más fácil de usar.
1. Una vez que abra RStudio, instale el paquete `bookdown` de R, ejecutando el siguiente comando en la consola de R.

```
install.packages('bookdown')
```

## Primeros pasos

Para comenzar un libro empleando RStudio, solo se debe crear un nuevo proyecto, mediante el menú `File > New Project > New Directory > Book project using bookdown`.

Lo cual creará un proyecto por defecto que se puede ir modificando (añadiendo o eliminando).

## Uso

Cada capítulo de **bookdown** es un archivo `.Rmd`, mismo que *debe* comenzar con un encabezado de primer nivel: `# Un buen capítulo`.

Cada archivo puede contener un (y solo uno) encabezado de primer nivel.

Use encabezados de segundo nivel y superiores dentro de los capítulos como: `## Una sección corta` o `### Una sección aún más corta`.

Se requiere el archivo `index.Rmd`, mismo que será es el primer capítulo de su libro.

## PDF

4. Para compilar los libros en pdf `bookdown` emplea `XeLaTeX`.
* En windows es recomendable instalar [MiKTeX](https://miktex.org/download), o actualizarlo (ejecutando MiKTeX Update) si ya está instalado.

	Hay una opción que dice Puede elegir si los paquetes faltantes se instalarán automáticamente (sobre la marcha). Asegúrese de que esté configurado en Siempre para permitir que se instalen los archivos de estilo necesarios.

* En Mac OS X se puede instalar [MacTeX](http://www.tug.org/mactex/) y en Linux [TeXLive](http://www.tug.org/texlive).


### ERROR

! Sorry, but ...\xelatex.exe did not succeed.

Solo fui a la configuración de la consola MiKTeX y elegí SIEMPRE los paquetes que faltan para que se instalen automáticamente.

## Configuración

* [Escritura de libros con bookdown](https://rubenfcasal.github.io/bookdown_intro/)

Bookdown / LaTeX puede ajustar automáticamente sus márgenes para la impresión a doble cara, todo lo que tiene que hacer, es agregar a su encabezado YAML:

```
geometry: "left=4cm, right=3cm, top=2.5cm, bottom=2.5cm"
```

En el encabezado YAML también puede controlar cosas como el tamaño de fuente y el interlineado (`linestretch`) , así como si desea una tabla de contenido (`toc`), una lista de figuras (`lof`) y de tablas (`lot`), 

# Ajustes

Puedes definir ajustes de salida para documentos HTML ó PDF

output:
   html_document:
      ...

output:
   pdf_document:
      ...

# Dependencias externas

De forma predeterminada, RMarkdown produce archivos HTML independientes sin dependencias externas, utilizando datos: URI para incorporar el contenido de scripts, hojas de estilo, imágenes y videos vinculados. Esto significa que puede compartir o publicar el archivo del mismo modo que comparte documentos de Office o PDF. Si prefiere mantener las dependencias en archivos externos, puede especificar `self_contained: false`.

En el caso de servir varios documentos de RMarkdown, es posible que también desee consolidar los archivos de la biblioteca dependiente (por ejemplo, Bootstrap y MathJax, etc.) en un solo directorio compartido por varios documentos. Con `lib_dir`.

output:
   html_document:
      self_contained: false
      lib_dir: libs

# Markdown

Cuando knitr procesa un archivo de entrada RMarkdown, crea un archivo Markdown (*.md) que posteriormente es transformado en HTML por Pandoc. Si desea conservar una copia del archivo Markdown después de la renderización, puede hacerlo usando la opción `keep_md`:

output:
   html_document:
      keep_md: true

# Encabezados

Puede agregar numeración a los encabezados usando la opción `number_sections`

output:
   pdf_document:
      number_sections: true

# Tabla de contenido

Puede controlar si desea una tabla de contenido (`toc`) y especificar la profundidad de los encabezados que desea aparezcan en esta (`toc-depth`):

> Si no se especifica explícitamente la profundidad de TOC, el valor predeterminado es 2 (lo que significa que todos los encabezados de nivel 1 y 2 se incluirán en el TOC)

output:
   pdf_document:
      toc: true
      toc_depth: 2

Puede hacer flotar la tabla de contenido a la izquierda del contenido (`toc_float`). La tabla de contenido flotante siempre estará visible incluso cuando se desplaza el documento.

output:
   html_document:
      toc: true
      toc_float: true

Opcionalmente, puede especificar una lista de parámetro a `toc_float` para controlar su comportamiento.

# Tablas

Puede mejorar la visualización predeterminada de las tablas a través de la opción `df_print`:

output:
   pdf_document:
      df_print: kable

# Pandoc

Si hay características de Pandoc que desea usar pero carecen de equivalentes en las opciones de YAML descritas anteriormente, aún puede usarlas pasando `pandoc_args` personalizados.

output:
   html_document:
      pandoc_args: [
         "--title-prefix", "Foo",
         "--id-prefix", "Bar"
      ]

# `_output.yml`

Si desea especificar un conjunto de opciones predeterminadas para que sean compartidas por varios documentos dentro de un directorio, puede incluir un archivo llamado `_output.yml` dentro del directorio.

> Tenga en cuenta que en este archivo no se debe incluir el delimitador `output:`

## Estilo Gitbook

install.packages("downlit")
install.packages("bslib")
install.packages("xml2")