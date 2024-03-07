

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

## 