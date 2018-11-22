## Home
El homepage es la primera página que aparece cuando ingresamos al sitio.  Está compuesta normalmente por secciones como *menu, cover, featured collection, collection list y footer.*

### Menú
El menú, como en la mayoría de los sitios web se sitúa en la parte superior de todas las páginas del sitio.

El archivo donde se puede editar la estructura de esta sección se encuentra en `sections/header.liquid`. Los estilos de esta sección pueden ser asignados en `shopify-workflow/sass/layout/header.scss`.

La configuración de la posición (fija o relativa), la transparencia, color, acomodo de elementos y demás opciones se hace desde el panel de administración. Para cada una de estas opciones existen flujos y condicionales de código en el mismo archivo `header.liquid`.

Existen dos listas de enlaces: 
	• Desktop: está dentro del contenedor `<header class="site-header">`
	• Móvil: está en un *snippet* que se puede consultar en `snippets/mobile-nav.liquid`

Cada uno con estilos diferentes tanto en estructura como en los enlaces.

Elementos como el menú móvil, la lista de enlaces y la lista de íconos están dentro de *snippets* para facilitar la lectura del código.

### Cover
Es una sección alta, que ocupa el 100% del ancho de la ventana, tiene una imagen de fondo, texto en tamaño grande y un botón que contiene un enlace.

El archivo donde se puede editar la estructura de esta sección se encuentra en `sections/cover.liquid`. Los estilos de esta sección pueden ser asignados en `shopify-workflow/sass/sections/home/cover.scss`

Si la cover, aparte de tener estas características, cuenta con un slider, se le denomina ***slideshow*** y su estructura se puede encontrar en `sections/slideshow.liquid`. Sus estilos pueden escribirse en el mismo archivo de `cover.scss`.

### Featured collection
Esta sección se caracteriza por mostrar productos pertenecientes a una colección, esta colección se selecciona desde el panel de administración, además, la cantidad de filas de productos a mostrar y la cantidad de productos por fila

El archivo donde se puede editar la estructura de esta sección se encuentra en `sections/collection.liquid`. Los estilos de esta sección pueden ser asignados en `shopify-workflow/sass/sections/home/collections.scss`.

### Collection list
En esta sección, en lugar de mostrar productos, muestra un mosaico de enlaces directos a colecciones de la tienda. Estos enlaces se muestran con el nombre de la colección y su respectiva imagen de fondo.

El archivo donde se puede editar la estructura de esta sección se encuentra en `sections/collection-list.liquid`. Los estilos de esta sección pueden ser asignados en `shopify-workflow/sass/sections/home/collections.scss`.

Si esta lista de colecciones se muestra como un slider, la estructura pertenece al archivo `sections/collection-list-carousel.liquid`.

### Footer
El pie de página por defecto contiene un formulario para newsletter, una lista de enlaces que funciona como mapa de sitio, links a redes sociales e información legal. El acomodo de estos elementos se determina en el panel de administración, por ejemplo tener el formulario de newsletter centrado. Para cada una de estas opciones existen flujos y condicionales de código en el archivo ubicado en `sections/footer.liquid`.

 Los estilos de esta sección pueden ser asignados en `shopify-workflow/sass/layout/footer.scss`.

Elementos como la lista de enlaces, el formulario del newsletter y los iconos de redes sociales se encuentran dentro de *snippets* para facilitar la lectura del código.
