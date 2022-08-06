# Dungeonero

## Posibles ideas Capua

### Ordenar el codigo
Esto me parece vital. Por la escala que ha cogido el proyecto hay que planificar un poco como ordenar el codigo y hacerlo mejor.  
Index solo deberia tener html, el estilo, deberia estar en un css aparte (usando clases con sentido) y no copiado y pegado 20 veces entre elementos, y el js deberia estar tambien aparte.  
Ademas, el js habria que comentarlo mejor, organizar las funciones (dividiendo el codigo en dos o tres secciones indicadas con un comentario grande, y no como ahora que la que gestiona los tokens esta dentro de inputs por ejemplo) y en la medida de lo posible incluso dividirlo en un par o tres .js distintos para que sea mas facil navegar entre ellos.  
Cualquier mejora en esto va a venir bien, especialmente si se documenta en este archivo readme.

### Pasar el codigo a ingles.
Hay comentarios y palabras del codigo (algun nombre de variable o una id) puestas en español o pensadas para español, estaria MUY bien que TODO el codigo tuviese buena nomeclatura y fuese en ingles, los comentarios lo mismo.

### Empezar a gestionar mejor los inputs de los botones y de paso agregar jQuery.
La fumada de mil funciones y gestiones de eventos distintos que hay para gestionar los inputs, los botones de la barra de herramientas y demas es una locura, estoy bastante seguro de que con jQuery y eventos se puede hacer de forma mucho mas limpia y consistente.  
Supongo que sera tema de, entre otras cosas, en vez de tener en los botones llamando a funciones de js, pillarlos desde jQuery, y ya de paso, empezamos a utilizar jQuery, que nos vendra bien. 

### Convertir los cambiadores de color a colorpickers de verdad en vez de un guarro text input donde metes el hexadecimal.
Ahora mismo las herramientas para cambiar los colores del mapa son un text input donde tienes que meter el hexadecimal, molaria un boton que te desplegara el tipico colorpicker y que eso funcionara.  
Sospecho que html debe tener una utilidad para esto, pero no estoy seguro. Si no, la tendra jQuery, y si no, buscamos e importamos otra libreria que lo haga.  
No debe ser muy dificil modificar las funciones del js para que funcionen con el colorpicker que sea.

### Hacer un panelcito de tirar dados
Que tenga los dados normales en una barrita arriba, un historial de resultados en un texto sencillo abajo y se pueda arrastrar, abrir y cerrar.  
Crear un div en html con botones para d20, d12... (si quieres puedes fliparte y que sean simbolos con alguna fuente o algo) arriba y abajo un espacio en blanco.  
Cuando se pulsan los botones los pillas en el js, generas un numero al azar y lo agregas, junto con una coma, a lo que hubiera en el espacio en blanco de abajo.  
Molaria que el ultimo numero siempre estuviera en negrita o asi.  
Para cerrarlo metes otro boton con una X y en el js le cambias el display a none. Aunque habria que agregar en la barra de herramientas un boton que lo abriera cambiandolo a block o flex o lo que sea.  
Luego para hacerlo arrastrable, busca por mi codigo la funcion que hace arrastrable el de fullKeys, intenta entenderla y replica.

### Convertir los puñeteros array de mapa a arrays de verdad en vez de objetos raros de javascript.
Esta es jodida. Mucho. Como pone abajo, lo que yo llamo arrays de mapa son realmente objetos de javascript. Habria que hacer que lo fueran porque va a ser mas facil trabajar con ellos y es mas limpio.  
El primer problema es enterarse de como funcionan los arrays bidimensionales en js o el equivalente, si es que existen, porque normalmente nombreArray[x,y] deberia funcionar como un array  
Luego hay que ver si hacemos eso como afrontamos el problema de los objetos que estan entre dos casillas y no en una casilla concreta.  
Una alternativa puede ser crear una clase casilla que contenga una string "objeto", un bool "lleno", quiza gestione dos de sus aristas colindantes y algo asi, y asi podemos juntar los dos arrays en uno solo, un array de casillas (la clase) y no tendriamos problemas de objetos que estan en aristas.

### Mejor gestion de los tokens
Los tokens son lo ultimo que implemente y a penas tienen cosas. Solo se pueden poner 4, los colores estan predefinidos y no se pueden borrar.  
Agregar un colorpicker al lado de donde se mete la letra para el token y que se le aplique molaria.  
Alguna forma para borrarlos tambien estaria bien, una señalita de X al lado o algo asi.  
Tambien estaria flama poder crear y borrar los que quisieras. Un boton de "+" en la barra de herramientas que te copiara el elemento de html donde se introduce el texto para un token y te lo pegara abajo, de forma que tu le das a +, y sale otra fila con la que puedes poner otro token.  
Y en general todo lo que se te ocurra.


## El bug de que el escritor de keys se va
Si insertas una key en la parte baja del mapa, en vez de salirte la ventanita de escribir al lado y visible, se va a china, habria que ver que pasa y fixearlo, debe de ser algo de que en vez del canvas mide la ventana visible o a saber.


## TODO

### FASE 1
Hacer que Undo no bugee al arrastrar  
Con multiples casillas y scroll el bocadillo de keys se abre mal colocado  
Agregar escaleras de caracol  
Copiar y pegar y decidir trabajo multiplanta  
Default color styles  
Gestion de archivos (plantas?)  
Gestionar bien el transform scale  
Organizar codigo en js y css  
Comentar bien  
Refactorizar a un idioma  
Meter indicativos de carga  
Agregar herramienta de borde en caida (elimina el borde creado y mete uno de 1px)  
Agregar funcion para que las escaleras de varias casillas se distribuyan solas  
Agregar escaleras simples y borde estrecho para cambios leves de nivel  
Cambiar tamaño del canvas en vivo  
El downloader deberia incluir las keys  

### FASE 2
Herramienta para tirar dados  
Combinar canvas online  

### FASE 3
Conseguir mezcla de estilos en el mismo mapa, posiblemente estilo por casilla  
MEjorar interfaz en general  
Conseguir ruido para los muros y casillas  
Conseguir ruido extra para muros naturales  

## DONE
Publicar en git con versionado  
Herramienta para redactar las keys  
Tokens?  
Aplicar nuevas funciones de casillas a cargar dungeon  
Undo puede reworkearse en torno a casillas para mejor fluidez  
Acelerar el cargar dungeon al menos en cambos de ToggleGridLines  
Requerir wd files en importacion  
Agregar keys al importador  
Herramienta de borrado de objetos  
Herramienta de borrado de 3x3  
Afilar el sistema de trazados  
Paint background on start  
Pintar escaleras  
Pulir pintado de textos  
Borrar objetos cuando pintas otro  
Actualizar fullkeys al agregar una  
El small eraser no borra muros  
El importador no importa las keys y deberia  
Key -100 es creada  
Puertas en cerrado no se  


## Notas de funcionamiento

La app esta grosso modo, en cuanto a su funcionamiento, dividida en 5 partes: 
 - **El html:** Html que se encarga de visualizarlo todo y recibir el input.
 - **Los inputs:** Javascript que se encarga de gestionar los inputs del html y llamar a las funciones pertinentes.
 - **Acciones y herramientas:** Funciones de javascript que "pintan las cosas" cuando son llamadas por el punto anterior.
 - **Arrays de mapa:** Javascript que almacena como datos logicos el estado de todo el mapa y se ve modificado por el punto anterior cuando algo se pinta.
 - **Gestion de archivos:** Funciones que se relacionan con archivos como las de importar, exportar y convertir a imagen.

### El html

El html esta picado a cholon (nisiquiera tiene un css para los estilos) en el porincipio del archivo.

La parte mas importante es la del final, los canvas. Los canvas son elementos de html donde podemos pintar con el javascript y cada uno esta estilado para ser transparente y pintarse uno sobre otro.  
Dungeon C se utiliza para pintar la base del mapa (las casillas vacias o no), sobre el en objects se pintan los objetos, y entre casillero y cuadraditos se pintan el cuadrado celeste que representa el cursor y la posible cuadricula que puede activarse. Tambien hay uno que pinta los tokens.

El div editKeys basicamente es el panel que se muestra y se oculta cuando insertamos una clave para que podamos escribir su contenido.

El div allKeysDiv es el que muestra todas las claves con su contenido para poder leerlo, a traves e javascript lo hacemos una ventana arrastrable.

Por ultimo, el div sin id de despues es el panel de herramientas. Las herramientas con subopciones las tienen por defecto ocultas pero ahi estan.

### Los inputs

En el codigo hay segun que funciones que sirven solo de enlace entre los elementos interactivos (como todos los inputs de la caja de herramientas) y el javascript.  
A 06/08/22 estan casi todos tras la linea 1105, tras un comment que pone Interface button functions.  
La mayoria sencillamente llama a otras funciones que hacen el trabajo de verdad, haciendo alguna comprobacion o guardando o pasando alguna variable antes.

Ademas, entre las lineas 294 y 386 (misma fecha) esta la logica mas importante de los inputs, la que detecta en que casilla esta el cursor, si el raton se esta moviendo y si hace clic, y luego llama a la funcion de pintar cosas.  
Se registran tambien los eventos de mouseup y mousedown para cancelar el pintado, para que no siga pintando cuando ya hemos levantado el boton del raton o si hemos salido del mapa.

Para saber sobre que casilla esta el cursor hacemos una regla de tres entre el ancho y alto de el canvas, la posicion del cursor, y el numero de casillas: Si el canvas mide 100px de ancho, el cursor esta en el px 50 y hay 10 casillas, debe de estar en la casilla 5. O algo asi.  
Despues comprobamos si hay alguna herramienta que pueda pintar en las aristas de las casillas y si es asi devidimos cada casilla entre el centro y los bordes para ver donde esta el cursor.

Por ultimo en relacion a los inputs, al final del javascript hay una funcion y una llamada a document.onkeydown que registra todas las teclas que se pulsen en el teclado para poder comprobarlas con un if.  
Ahora mismo solo tenemos un if que comprueba si estan pulsadas ctrl y z y activa el deshacer.

### Acciones y herramientas

Esto esta por hacer.

### Los array de mapa

Nota: La idea es que sea un mapper de dungeons, y por tanto, bajo tierra. De forma que todas las casillas empiezan llenas (de piedra) y tu las vas vaciando paraconstruir la dungeon.

Para poder jugar con las casillas que hay en los mapas, asignarles contenido y luego saber que hay en ellas para borrarlas y demas, todo el contenido del mapa se guarda en tres arrays.  
El array dungeonFilled es un array de booleanos que guarda true or false en funcion de si la casilla esta "vacia o llena".  
El array de dungeonObject guarda un entero que nosotros tenemos asignado a un tipo de "cosa" que hay en la casilla
El array de fullKeys se usa para guardar el contenido de las keys (o claves) del dungeon, es un array de strings y cada indice equivale a una key.

De esta forma, virtualmente tenemos en un array toooooodas las casillas del mapa y si estan vacias (son transitables) o no (son muro de piedra), en otro array el contenido de cada casilla (escaleras, un numero, una columna...) y en un ultimo array los textos

A los arrays de filled y de object se accede con la coordenada de la casilla, por ejemplo dungeonFilled[0,0] seria la casilla de arriba a la izquierda del todo.  
Y luego, y esto hay que arreglarlo en algun momento, para los objetos que estan entre dos casillas como las paredes, se usan incrementos de 0,5. Por ejemplo, dungeonFilled[1.5,0] sería de la fila de casillas superior, el muro que hay entre la segunda casilla y la tercera.

Nota: Con respecto a los muros: Ya se pintan muros alrededor de las paredes propias del dungeon segun lo estas vaciando, el objeto de muro es para otros muros.

Nota importante: Los arrays no son arrays de verdad, por la maldad de javascript y mi pereza, son objetos raros.

#### A que equivalen los enteros de dungeonObject

1: puerta
2: puerta secreta
3: muro
4: trampa
5: columna
6: ventana
7: stairs up north
8: stairs up right
9: stairs up south
10: stairs up left
11: stairs down north
12: stairs down right
13: stairs down south
14: stairs down left
100: Los enteros que son mayores a 100 estan reservados para las keys, equivaliendo 102 a la key 1, 102 a la key 2 y asi...

### Gestion de archivos

Son las funciones Download, Exporter e Importer.

La funcion de download no la entiendo bien ni yo, pero basicamente plasma los dos canvas apropiados en un png y te lo descarga.

Las funciones de exporter e importer tienen como objetivo que puedas guardar el mapa para poder recuperarlo o pasarselo a alguien, en un futuro estaria bien que fuera en la nube, pero por sencillez lo que hace ahora mismo es crear un archivo .wd o leer de un archivo .wd  
La funcion de exportar convierte en un json los arrays de mapa y el de claves y eso lo junta en uns tring que guarda en un txt (aunque luego le ponga .wd), separando cada array por muchos guiones para luego con el importer diferenciarlos, el importer hace lo opuesto.

