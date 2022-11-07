# ¿Por qué no debes escribir un libro con un procesador de texto convencional?

En la actualidad los libros se distribuyen en múltiples formatos (HTML, PDF, MS Word y ePub) para diferentes propósitos, y un procesador de texto convencional no puede generar continuamente todos estos productos.

Así que el `flujo de trabajo` más eficaz, consiste en realizar un solo manuscrito (usando código) para componer, compilar y publicar el libro de forma simultánea en todos los formatos que se desee.

Ademas, en los procesadores convencionales, formatear tu texto, hacer que se vean bien las figuras  y corregir los saltos de página rebeldes puede ser tedioso y llevar mucho tiempo.

> **En conclusión**: si quiere tener todo organizado y consistente, o si necesita trabajar en equipo, Microsoft Word y similares (como OpenOffice) NO es lo que se necesita para crear un libro. Lo mejor es usar un lenguaje de marcado (código), que nos permitá concentrarnos en el contenido "sin preocuparnos por aplicar formatos".

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

¿Por qué Bookdown?

Con bookdown, todo el formato se gestiona por usted; Bookdown puede manejar automáticamente toda la numeración de sus secciones, figuras y tablas, así como generar automáticamente páginas de contenido y listas de tablas y figuras.

## Instalación

1. Primero hay que descargar e instalar [`R`](https://cran.r-project.org/).
	Haz clic en "install R for the first time"...
1. Aunque no es necesario, se recomienda utilizar el IDE [`RStudio`](https://rstudio.com/products/rstudio/download/) que hará que R sea más fácil de usar.
1. Una vez que abra RStudio, instale el paquete `bookdown` de R, ejecutando el siguiente comando en la consola de R.

```
install.packages('bookdown')
```

También puede optar por instalar todos los paquetes opcionales, si no le importa demasiado si estos paquetes se utilizarán realmente para compilar su libro (como htmlwidgets):

```
install.packages("bookdown", dependencies = TRUE)
```

Los paquetes R también se actualizan constantemente en CRAN o GitHub, por lo que es posible que desee actualizarlos de vez en cuando:

```
update.packages(ask = FALSE)
```

4. Para compilar los libros en pdf `bookdown` emplea `XeLaTeX`.
* En windows es recomendable instalar [MiKTeX](https://miktex.org/download), o actualizarlo (ejecutando MiKTeX Update) si ya está instalado.
* En Mac OS X se puede instalar [MacTeX](http://www.tug.org/mactex/) y en Linux [TeXLive](http://www.tug.org/texlive).

## Primeros pasos

Para comenzar un libro empleando RStudio, solo se debe crear un nuevo proyecto, mediante el menú `File > New Project > New Directory > Book project` using bookdown.

Lo cual creará un proyecto por defecto que se puede ir modificando (añadiendo o eliminando) los ficheros `.Rmd` correspondientes a los distintos capítulos.

> Referencia: https://bookdown.org/
> https://yihui.org/knitr/