# Vista de producto
La vista de producto por defecto tiene la información y características esenciales de cada producto, sin embargo, el tipo de producto en ocasiones requiere de información y elementos adicionales para complementar la descripción del mismo y para ello se crea un **template de producto alternativo.**

Para crear un nuevo template de producto, podemos seguir los pasos de [este tutorial oficial de Shopify](https://help.shopify.com/en/themes/customization/store/create-alternate-templates)

* A modo de ejemplo, supongamos lo siguiente:	
	* Nuestro nuevo **template** tiene como nombre: `product.alternate`
	* Nuestra nueva **sección** tiene como nombre: `product-alternate-template`.

El siguiente paso es copiar el código de la sección `product-template.liquid` a nuestra nueva sección, esto con el fin de tener un punto de partida avanzado.

> *Nota: Si el diseño del nuevo template de producto es radicalmente diferente al original es mejor comenzar en blanco e ir tomando fragmentos del original en caso de ser necesario.*  

Lo siguiente es asignar el nuevo template a uno o más productos, esto se puede hacer fácilmente siguiendo los pasos de [este tutorial](https://help.shopify.com/en/themes/customization/store/create-alternate-templates#assign-your-template-in-the-admin-sectioned-themes-specific)

Una vez asignado el nuevo template, se puede comenzar a editar la nueva sección.

Hay diferentes tipos de template alternativos, hay algunos a los que, por ejemplo solo se les añade un campo de formulario extra (input, textarea, select, etc) a los que llamaremos **Templates básicos** y otros que requieren toda una serie de secciones y apartados de información extra, a los que denominaremos como **Templates avanzados**.



## Templates básicos

Los templates básicos están basados en el template por defecto y generalmente solo se añaden banners y/o elementos de formulario extras.

En caso de que se agregasen banners o elementos estáticos, éstos se maquetan en el lugar necesario para ser mostrados por los productos que tengan asignado nuevo template, normalmente la información que contienen es fija.

En caso de que se agregasen elementos de formulario extras es recomendable que se generen con [esta herramienta](https://ui-elements-generator.myshopify.com/pages/line-item-property), la cual provee de una interfaz gráfica para generar el código nuevos elementos e integrarlos a nuestro nuevo template y así evitar complicaciones y, sobre todo, errores. 

Lo único que se tiene que hacer después de generar el código es copiarlo y pegarlo en el formulario del nuevo template de producto.

Comúnmente estos campos de formulario extras son opciones de producto adicionales a las variantes y es importante que se estas opciones se muestren en los correos electrónicos que llegan al usuario y en el correo que llega al vendedor de la tienda.

A continuación se describe el procedimiento para mostrar esta información.


#### Mostrar información de campos de formulario extras en correos electrónicos

A las opciones extra que se añaden en el formulario de producto se les denomina por parte de Shopify como *Line Item properties* y ofrecen la posibilidad de especificar fácilmente el producto que desees comprar.

Es importante que estas opciones se integren en el correo electrónico que recibe el usuario al completar su orden.

En el panel de administración de la tienda, en el apartado `Settings > Notifications > Order confirmation` se encuentra el código *liquid* con los datos que se envían al usuario al realizar una compra.

Si seguimos al pie de la letra [este artículo oficial de Shopify](https://help.shopify.com/en/themes/customization/products/features/get-customization-information-for-products#show-customizations-in-email-templates-sectioned-themes-specific), podremos lograr que todos los valores de los campos extra de formulario se muestren en este correo electrónico.



## Templates avanzados
Los templates avanzados contienen módulos y subvenciones de información que necesitan ser autoadministrables y cuyo contenido debe ser introducido en la descripción del producto y requiere del siguiente proceso:

* A modo de ejemplo, supongamos lo siguiente:
	* El diseño a maquetar es: 
![](Tesis%20Shopify/Captura%20de%20pantalla%202018-11-22%20a%20la(s)%2013.56.53.png)
	* La información de **salidas** y **regreso** debe ser autoadministrable.
	
Como primer paso, en la descripción del producto escribiremos como *Heading 1* el título del bloque de información, en este caso el título del bloque sería **Horarios**. A continuación ingresaremos la información correspondiente a ese bloque (en este caso salidas y llegadas).
![](Tesis%20Shopify/Captura%20de%20pantalla%202018-11-22%20a%20la(s)%2014.28.23.png)


Lo siguiente es importar [este script](https://gist.github.com/UbaldoRosas/9ec2519525753e366307cbf24cd68594) al archivo `main.js`, está escrito en Javascript y contiene el código necesario para que funcione nuestro template. Mas adelante detallaremos su funcionamiento.

En el documento `product-alternate-template` ingresamos un `<div id="data-sections">`y, por medio de liquid, imprimimos la descripción del producto: `{{ product.description }}`. 

El `<div>` debe estar oculto, el script obtendrá de aquí toda la descripción para después hacer bloques de contenido a partir de cada *Heading 1 (o `h1`)*.

Para imprimir el contenido de los **Horarios** crearemos un `<div>` al que le añadiremos un atributo `data-horarios`. Al añadirlo, el script sabrá que en este contenedor deberá colocar la información que está a partir del *Heading 1* que concuerda con el nombre del atributo. 
Es decir que si nuestro *Heading 1* dice **Horarios**, el atributo `data` deberá decir `data-horarios`.

> *Nota: Si el Heading 1 tiene acentos o caracteres especiales, el script ya cuenta con una función que los reemplaza*  

Con esta metodología es posible ejecutar diseños personalizados en la vista de producto sin perder la característica de autoadministrar la información.

[Aquí un ejemplo de una vista de producto personalizada](https://vagandopormexico.myshopify.com/products/sierra-gorda)
