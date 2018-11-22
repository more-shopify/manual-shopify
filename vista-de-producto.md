## Vista de producto
La vista de producto por defecto tiene la información y características esenciales de cada producto, sin embargo, el tipo de producto en ocasiones requiere de información y elementos adicionales para complementar la descripción del mismo y para ello se crea un **template de producto alternativo.**

Para crear un nuevo template de producto, podemos seguir los pasos de [este tutorial oficial de Shopify](https://help.shopify.com/en/themes/customization/store/create-alternate-templates)

A modo de ejemplo, supongamos lo siguiente:	
	• Nuestro nuevo **template** tiene como nombre: `product.alternate`
	• Nuestra nueva **sección** tiene como nombre: `product-alternate-template`.

El siguiente paso es copiar el código de la sección `product-template.liquid` a nuestra nueva sección, esto con el fin de tener un punto de partida avanzado.

> *Nota: Si el diseño del nuevo template de producto es radicalmente diferente al original es mejor comenzar en blanco e ir tomando fragmentos del original en caso de ser necesario.*  

Lo siguiente es asignar el nuevo template a uno o más productos, esto se puede hacer fácilmente siguiendo los pasos de [este tutorial](https://help.shopify.com/en/themes/customization/store/create-alternate-templates#assign-your-template-in-the-admin-sectioned-themes-specific)

Una vez asignado el nuevo template, se puede comenzar a editar la nueva sección.

La información que vaya a quedar fija y se repita en cada producto puede ser maquetada directamente en la nueva sección.

La información que necesite ser autoadministrable debe ser introducida en la descripción del producto y requiere del siguiente proceso:

A modo de ejemplo, supongamos lo siguiente:
	• El diseño a maquetar es: 
![](Tesis%20Shopify/Captura%20de%20pantalla%202018-11-22%20a%20la(s)%2013.56.53.png)
	• La información de **salidas** y **regreso** debe ser autoadministrable.
	
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
