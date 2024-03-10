

# CURSO GRID CSS

## (1/17) Introducción y Conceptos Básicos

Grid CSS es la segunda herramienta  que tenemos para maquetar realmente, es el segundo sistema que nos ofrece el estandar CSS  para poder maquetar interfaces web, Flexbox css fue el primer sitema real de maquetacion que tuvimos en css toda las tecnicas que usabamos antes los diseñadores web como las tablas los marcos los floats  eran cosas que nosotros usabamos de css como para poder hacer una reticula y poder ir maquetando el contenido pero no es hasta flexbox css por alla del año 2014 2015  que se empesó a implementar en los navegadores entonces ya teniamos un primer sitema real de maquetacion en css ahora el detalle de flexbox es que es un sistema unidimencional, es decir si podemos tener filas y columnas pero no al mismo tiempo o tienes filas o tienes columnas.

**¿Que es Grid CSS?**
con Grid Css por fin tenemos un sistema bidimencional as de cuenta como una hoja de calculos donde tenemos columnas y filas lo podrias ver como un tablero de ajedres donde tu defines de que celdas a que celdas ocupan ciertas areas y entonces puedes maquetar estructuras.

**¿Grid viene a reemplazar a flexbox?**
Porsupesto que no! al contrario viene a complementarlo, Flexbox se pensó como para al acomodo interno de los elementos piensa en el cuerpo de un Post flexbox es mas como para alinear elementos internos de un componente de (Ui) (User Interface) eje: foto de la targeta, el titulo , la descripcion y el enlace estén bien alineados en cambio grid CSS al ser un sistema bi-dimencional nos va permitir saber de que espacio a que espacio.

Y estos dos sistemas de maquetacion nos vuelve una navaja Suiza para maquetar interfaces Web entonces la relacion entre Grid y Flexbox como 2 sistemas de maquetacion que sefucionana. xd.

en Grid CSS necesitamos comprender ciertos conceptos. 

> https://jonmircha.com/grid

si eres novato en esto de la maquetacion mejor aprende Flexbox.

## (2/17) Grid Explícita

¿Por que explícita? Por que explicitamente vamos a definir número de filas y columnas que queremos que nuestra grid tenga.

La propiedad como en flexbox para cambiar el comportamiento a que el contenedor sea una grid es con la propiedad:

> `display: grid`

Si vemos no sucede mucho ¿Por qué? por que aparte de utilizar display:grid, recuerda grid es un sistema bidimencional, entonces le debemos decir cuantas filas y columnas vamos a ocupar

>`grid-template-columns` me permite definir el número de columnas.

Tenemos diferentes manera de definir las columnas y podemos utilizar cualquier unidad de medida(rems, porcentajes pixeles y con flexbox viene una nueva propiedad llamada fraccion[fr]) una fraccion se defíne como el espacio sobrante
 
**si yo quisiera un sitema de 3 columnas por 3 filas** 

![imagen de la propieda explícita](/assets/explicita.JPG)

intencionalmente puse 19 items sí yo estoy formando una reticula de 3*3 pues me dá 9 celdas entonces muy importante, las otras 10 celdas se está alineado en base al formato de las 3 columnas y las filas se van generando implicitamente aunque yo no definí explicitamente, se van a comodando por ese flujo z(sic sac) qu ya trae Grid y Mantiene un tamaño definido por la altura que tiene cada uno de esos contenedores, apartir de la celda 10 que no está definida en esa reticula que yo formé de 3 columnas por 3 filas.


por que la celda 19 es mas delgada. por que GridItem 16 al estar en la misma fila que gridItem17 como gridItem17 tiene mas contenido en letra digamos gridItem17 es la que define la altura de la fila y como gridItem 19 está solito por eso es que se hizo mas pequeñito o una altura mas pequeña. osea apartir de la reticula 3*3 se adaptan al tamaño automático.

Cuando nosotros estemos inspeccionando el codigo, navegadores Firefox y Google chrome tiene la capacidad cuando un elementos está maquetado con grid nos muestra justamente la cuadrula resultante.

Ese grid nos puede ir dando una idea ya a nivel de las herramientas de inspeccion de código como está formandose.

tenemos 19 Items, vamos a hacer una retícula de 5*4 que me permita tener los 19 elementos que yo formé dentro de seta grid.


> `repeat()` sirve para hacer patrones mas avanzados a la hora de formar nuestra cuadricula.

la función css vino con grid, recibe 2 parametros() imaginense que quiero una grid que toda sus columnas sean del mismo tamaño. si tengo el contenedor 100% lo divido entre 5  me dá 20% a cada una

> `repeat(5, 20%)` quiero una grid que tenga 5 columnas del mismo tamaño **no olvides la coma**


![desbordamiento](/assets/explicita-desbordamiento.JPG)

Aqui pueden empesar ir viendo lo que nos combiene cuando empesamos a trabajar con grid o con frameworks como bootstrap, materialcss, nos preucupamos por el sistema de columnas pero realmente las filas es muy rara la maquetación en la que realmente tengamos que darle un valor bien especifico a un elemento. 

> **generalmeente el tamaño de las filas siempre va depender en base al contenido que tenga nuestros elementos**

Imaginense que yo quiero una grid al reves de 4 columnas por 5 filas, las filas del medio van a ser del mismo tamaño y la de los extremos van asaer de diferente tamaño.

Nosotros podemos dar espaciados entre las celdas.

> `column-gap:4rem;         row-gap:2rem;           gap: 1vh 1vw; /*gap:row column;*/`


para que no haya desbordamiento tendria que hacer una resta del espaciado que le estoy considerarando.

```css
.grid-explicit{
  display: grid;

  /*Grid 3c*3r*/
  /*El rem está basada en la unidad tipografica que tenga  mi etiqueta html*/
  /*mi primera columna ocuma 2 rem la segunda columna va ocupar 20vh y la trecera columna ocuapa 30%*/
  grid-template-columns: 2rem 20vh 30%; /*simplemente separada por espacios*/
  /*primera fila es de 50% la 2da es de 100px y la tercera es de 1fr*/
  grid-template-rows: 50% 100px 1fr ; /*(fr) es el espacio sobrante*/ 
  grid-template-columns: 50% 100px 1fr;
  grid-template-rows: 3rem 20vh 30%;
  /*Grid 5c*4r*/
  grid-template-columns: repeat(5, 20%);/*Recibe 2 parametros */
  grid-template-rows: repeat(4, auto);/*quiero 4 filas y que el tamaño se adapte al al tamaño que tengan las columnas*/
  grid-template-rows: repeat(4, 25%); /*el texto se desborda*/
  grid-template-rows: repeat(4, auto);
  grid-template-columns: repeat(5, 1fr);
  grid-template-rows: repeat(4, 1fr);
  /*Grid 4c*5r*/
  grid-template-columns: 20% 30% 30% 20%;
  /*el repeat hay que ponerlo siempre y cuando las columnas o filas que van a tener en mismo tamaños sean CONTINUAS*/
  grid-template-columns: 20% repeat(2, 30%) 20%; /*Repiteme 2 del 30% .*/
  grid-template-rows: repeat(5, auto);/*Auto, para que se adapten en base a su contenido*/ 
  /*espaciado, Pero estas 3 propiedades están depreciadas por eso sale con las letras tachadas*/
  grid-column-gap:2rem;
  grid-row-gap:1rem;
  grid-gap: 100px 0px; /*El primer valor es para row y el segundo para columnas*/
  /*oficialmente*/
  column-gap:4rem;
  row-gap:2rem;
  gap: 1vh 1vw; /*gap:row column;*/
  gap: 0; /*Sin ningun espaciado*/

}
```

Hay otras maneras incluso de posecionar ya de manera muy particular cada uno de los elementos que tenemos en nuestra grid

##  (3/17) Posicionamiento con Grid Lines

Nosotros podemos establecer que un elemento se acomode en determinada coordenada de la cuadricula, existen diferentes formas de trabajarlo.

¿Como acomodar elementos ocupando cierto número de celdas y tambien con la ayuda de las grid lines? _Grid-lines dividen las filas y las columnas_

Imaginense que voy a posicionar el elmento número 10

Hay 2 propiedades que se llaman:

`grid-row-start: ; grid-row-end: ; grid-column-start: ; grid-column-end: ;`

Estas propiedades me dicen de que linea a que linea yo quiero  que este elemento ocupe.

Miren como item 6 se empujó, esto tiene que ver con el flujo de la grid, pero como yo explicitamente estoy posicionando mediante las lineas ese gri Item 10 por eso es que se recorieron. Ahora estas propiedades tiene un atajo. ` grid-row: 2/3;  grid-column: 3/4;`

¿Como combino celdas? así:

> `grid-row: 2/3;  grid-column: 3/4;`

Otra manera de posicionar elmentos diciendole que ocupe varios espacios dependiendo de la posicion donde se encuentre y para eso vamos a utilizar una palabra Span ¡No, es html! 

Yo quiero que el Item 12 ocupe 3 celdas en columna y en filas 2.

Si yo a partir de la posicion donde se encuentra el elemento quisiera que barcara ciertos elementos enfilas y columnas podemos hacer lo siguiente.

> ` grid-row: span 2; grid-column: span 3;`

![Span](/assets/grid-span.JPG)

Fijense que nuestra cuadricula es de cuatro columnas por cinco rows a partir del grid item 15  hasta el 19  ya están fuera de esa grid explicita que puse, pero si inspeccionamos codigo podemos ver que Grid es lo suficientemente inteligente para seguir generando esas cuadriculas de manera automatica con estó ya estamos acomodando los elementos de manera explicita **¿Por que Explicita?** por que ya lo estoy definiendo de tal linea a tal linea

Ahora tambien podriamos hacer una mescla de estos 3 elementos.

vea que todo los elementos se reacomodan.

 ![espacios-vacios](/assets/span-espacios-vacios.JPG)
 
¿por que hay espacios sobrantes? por las areas que hemos definido, pues estos no caven entonces se van colocando hacia abajo 

Cuando nosotros veamos el tema del flujo de la grir, ahi vamos a poder aprovechar los espacios sobrantes para que los ocupen celdas que si podrian caber ahi.

Si ya empesaste a definir explicitamente tus elementos ya sea con lineas, a las lineas nosotros le podemos dar nombres particulares para que se llamen y apartir de ahi nombrar las lineas y posicionarlas, tambien podemos posicionar con nombres de areas,  particularmente, me gusta alinear mis elementos ya sea yo conociendo las lineas  o definiendo areas. pero todas estas formas que nos ofrece grid pues es que tu elijas con la que mejor te sientas cómodo.

Para evitar este tipo de problemas que estábamos viendo que la grid del Item 10 desaparecia aparentemente de la reticula lo que te recomiendo es:

> _Si tu ya empesaste a definir las posiciones de tus elementos que van a formar parte de tu areas de maquetacion yo te suguiero que explicitamente **tu vayas definiendo toda las areas explicitamente**  y no dejes que el flujo de la Grid posicione en base a su algoritmo lo elementos a los que tu explicitamente no le hayas dicho de que linea a que linea van_ 

> _Es decir  si tu ya empesaste a linear 3 Items lo ideal es que aliniemos todos Explicitamente para que así los elementos se vayan posicionando en las areas que tu hayas definido por que luego muchas veces el dejar que algunos elementos se acomoden por el flujo de Grid nos va dar ese tipo de comportamientos extraños y hasta que tu no entiendas el funcionamiento del flujo de Grid te puede dar resultados horribles_

## (4/17) Posicionamiento con nombres de Grid Lines

Tenemos lineas y a esas lineas nosotros le podemos dar nombres _(Ponle nombres que tenga sentido)_ 

Si tengo una reticula de 3*3 eso significa que voy a tener 4 linas de columna por 4 lineas de fila.

quiero que el Item 3 ocupe todo el espacio de la última fila.

```css
  /*GRID LINE NAMES*/
   /* Grid 3C x 3R reticula*/
  .grid-line-names{
     display: grid;
     grid-template-columns: repeat(3, 1fr);
     grid-template-rows: repeat(3, 1fr);
    /*para nombrar las lineas*/
    grid-template-columns: [linea-c1]1fr [linea-c2]1fr [linea-c3]1fr [linea-c4];
    grid-template-rows: [linea-r1]1fr [linea-r2]1fr [linea-r3]1fr [linea-r4];
  }

  .grid-line-names .item:nth-child(3){
    color: cyan;
    grid-row: linea-r3 / linea-r4;
    grid-column: linea-c1 / linea-c4;
  }
```

![nombre-linea](/assets/nombre-linea.JPG)

el item 8 y 9 ya se salieron de esa grid explicita ahora , ¿por que el tamaño del Grid Item 8 y Grid Item 9 es mas pequeño?  recuerda que el valor por defecto de las filas es el valor automático es decir el valor que la altura que tenga de contenido y recuerden que aquí lo que yo defini explicitamente que las primeras 3 filas van a tener una fraccion. 

Si yo quisiera que todo esto fuera proporcional pues en lugar de ponerle el valor de fraccion `1fr`  vamos a decirle que tengan el valor `auto` y el valor automático está definido  por la altura de contenido que tengan y tambien recalcula para que toda las filas tengan el mismo espacio, _Recuerda, nuestro contenedor es del 80% del tamaño del viewport_ así 

> `grid-template-rows: [linea-r1]auto [linea-r2]auto [linea-r3]auto [linea-r4];`

![tamaño-proporcional](/assets/tamaño-proporcional.JPG)

Vean que a cada fila le estan tocando 25%.

Particularmente esto es complicarnos la existencia, por que  si tu ya sabes que al principio defines tus filas  y tus columnas y que si quieres posicionar los elementos con la tecnica de los `Grid-lines` creo que la tecnica de ponerle nombre a las lineas que nos ofrece grid  lo único que hace es generar mas texto complicarnos más la existencia a la hora ya de definir las maquetaciones,

recuerda que tenemos un atajo que se llama grid area que nos permite definir los valores en una sola instruccion de grid row y de grid column, **Eso no funciona cuando estamos usando los grid-lines (nombres a lineas)**

## (5/17) Posicionamiento con Grid Areas 

Te voy a enseñar podemos asignar nombres de areas. vamos hacer el típico Holy Grail 3 Column Responsive Layout.

![Holy_Grail_Layout](/assets/holy-grail-layout-diagram.png)

una tipica maquetación de blod de principio de este siclo, nos permite dar nombres semánticos a las regiones es com figma o cualquier software de IU O UX, definiendo tu los wiframes los cuadritos los espación las regiones donde van a ir tus contenidos

¿Cúantas columnas tengo?
![figma](/assets/figma.JPG)

tengo 2 columas

¿Cúantas filas tengo?

Tengo 3 filas.

```css
  .grid-areas{
    display: grid;
    /*Grid de 2c x 3r*/
    grid-template-columns: 1fr 200px;
    grid-template-rows: 100px repeat(2, 1fr) 60px; /* la primera de 100px  las segundas 2 de una fraccion y la 3ra de 60px*/
    /*les suguiero que cada fila lo manejen en distintas lineas de código */
    grid-template-areas: 
    "header header" /*no es el nombre de la clase, es el nombre original del elemento*/
    "content sidebar"
    "content ."/*Si yo quiero dejar una celda en blanco dejamos un (punto)*/
    "footer footer";
    /*no pasó absolutamente nada*/
  }

.header{
  grid-area: header;/* lo pones sin comillas dobles.*/
}

.content{
  grid-area: content;
}


.sidebar{
  grid-area: sidebar;
}

.footer{
  grid-area: footer;
}

```

cuando tengamos LAYOUTS mas complejos esta tecnica de las grid areas cuando temgamos que hacerlo responsivo va hacer que tengamos que escribir menos código.

Cuando tus selectores de maquetación le des nombre de area ese nombre de area lo va tener durante todo el flujo de maquetacíon.

Todas esas maquetaciones que tu hacias en photoshop ilustrator, etc. Vé como esos espacios de maquetacíon los puedes pasar muy facilmente con esta tecnica de las  ``Grid-areas`` esta es la solucion ganadora para definir las estructuras de tus maquetaciones.

> Grid no reemplaza a Flexbox, lo complementa, grid fue pensado para diseñar la maquetacion,  la estructura de tus regiones flexbox te va servir para alinear los elementos ya internos de tus componentes  como: una ventana modal, elementos de una targeta como los elementos de un menú


## (6/17) Grid Implícita. Grids de bloque y de línea

En la clase enterior te mostraba como generar estructuras de maquetacíon(layout) zonas de contenido como wiframes.

El navegador tiene la capacidad de que grid siga apilando elmentos en esa cuadricula aunque ya no esté definida pero que despues se vayan desbordando los elementos.

  fijate, como todo se recorio a la izquierda, esto pasa porque display: grid; está ocupando
  todo el ancho disponible y el container le está dando margenes automatico a los lados
  y tiene el 80% de la pantalla entonces por eso se está centrando.

  ![inline-grid](/assets/inline-grid.jpg)

  en el momento que le pongo display: inline-grid;  está ocupando el 80 % no le podemos aplicar
  margenes laterales y ese 20% sobrante lo está reflejando hacia la derecha.

  Cuando tenemos un elemento con display: inline-grid;  si yo tengo 2 elementos contenedore
  que trabajan con el modelo de grid y tienen suficiente espacio para estár en el mismo bloque
  a lo ancho de contenido, pueden compartir espacio.

  imaginate que vamos a poner 3 cuadriculas y que cada cuadricula va tener una galeria temá-
  tica y queremos que compartan el mismo espacio en lugar de aplicar display: grid;
  aplicamos display: inline-grid;

  ![2 cuadriculas](/assets/inline.JPG)

/*
  puedo tener hasta 12 celdas y 12 items, pero recuerda, que en el navegador 
  tengo 19 Items entonces del 13 al 19 ya no estaría dentro de esa cuadricula
  implícita, sin envargo grid tiene la capacidad de seguir acomodando los elementos.
  Cuando es maquetacion dinamica, el contenido va depender de una solicitud
  que app haga a una API y a una base de datos entonces ahi la cuadricula se
  va ir formando dinamicamente, este comportamiento lo tiene cualquier red
  social, entonces ahi nos ayuda este tema de la grid implícita.
  */


¿Que pasa con los elementos posteriores?
pues el valor por defecto que van a tener los elemenos en fila que se vayan
despues de esa grid explicita, van a tomar el valor AUTO.
A partir del elemento 13 se trataron de ajustar  al tamaño que tenia el contenedor padre
y cuando ya no empiezan acaver van desbordando el contenedor del grid
y tienen el valor AUTOMÁTICO(la altura de la fila va depender del contenido de los elementos)
y si le pones un parrafo a un item, la altura de toda da fila se adapta
a ese item
Grid explicita:
es cuando tu defines las filas y las columnas que estás esperando recibir
apartir de ahi si por las necesidades de tu aplicacion como la cuadricula de instagram no vas a 
saber cuantos elementos se van a ir acomodando en tu grid eso podria servir en una galeria
de imágenes o portafolios pues ahi se van a ir acomodando, es importante entender el por que
van a ir variando los tamaños de las alturas de las celdas  cuando ya no estamos considerando
las celdas que no entran en la grid explícita.



> `display: inline-grid;` el modelo de grid CSS  se aplica en modo inline

> `display: grid;` es commo la filosofia de display bock bloque(envidioso) se comportan como elementos de bloque genera saltos de linea


```css
  .grid-implicit{
/*Grid de 4c x 3r*/
width: 40%;

display: grid; /**/ 
display: inline-grid;
grid-template-columns: repeat(4, 1fr);
grid-template-rows: repeat(3, 200px);

}
```





















