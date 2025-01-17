https://docs.google.com/presentation/d/17GdWdk_hdPkQEr9CPAkV1JcscTy22Z8I246_8AraV3A/edit?usp=sharing

La Programación Orientada a Objetos (POO u OOP según sus siglas en inglés)
es un paradigma de programación en el que los conceptos del mundo real
relevantes para nuestro problema se modelan a través de clases y objetos, y en
el que nuestro programa consiste en una serie de interacciones entre estos
objetos.

## Clases y Objetos
Para entender este paradigma primero tenemos que comprender qué es una
clase y qué es un objeto. Un objeto es una entidad que agrupa un estado y una
funcionalidad relacionadas. El estado del objeto se define a través de variables
llamadas atributos, mientras que la funcionalidad se modela a través de
funciones a las que se les conoce con el nombre de métodos del objeto.

Un ejemplo de objeto podría ser un coche, en el que tendríamos atributos como
la marca, el número de puertas o el tipo de carburante y métodos como arrancar
y parar. O bien cualquier otra combinación de atributos y métodos según lo que
fuera relevante para nuestro programa. Una clase, por otro lado, no es más que
una plantilla genérica a partir de la cuál instanciar los objetos; plantilla que es la
que define qué atributos y métodos tendrán los objetos de esa clase. Volviendo
a nuestro ejemplo: en el mundo real existe un conjunto de objetos a los que
llamamos coches y que tienen un conjunto de atributos comunes y un
comportamiento común, esto es a lo que llamamos clase. Sin embargo, mi coche
no es igual que el coche de mi vecino, y aunque pertenecen a la misma clase de
objetos, son objetos distintos.

En Python las clases se definen mediante la palabra clave class seguida del
nombre de la clase, dos puntos (:) y a continuación, indentado, el cuerpo de la
clase. Como en el caso de las funciones, si la primera línea del cuerpo se trata
de una cadena de texto, esta será la cadena de documentación de la clase o
docstring.

![image](https://user-images.githubusercontent.com/91554777/176511639-25c1a33a-7744-4c09-9eac-0526c8920ada.png)

Lo primero que llama la atención en el ejemplo anterior es el nombre tan curioso
que tiene el método __init__. Este nombre es una convención y no un capricho.
El método __init__, con una doble barra baja al principio y final del nombre, se
ejecuta justo después de crear un nuevo objeto a partir de la clase, proceso que
se conoce con el nombre de instanciación. El método __init__ sirve, como
sugiere su nombre, para realizar cualquier proceso de inicialización que sea
necesario. Como vemos el primer parámetro de __init__ y del resto de métodos
de la clase es siempre self. Este mecanismo es necesario para poder acceder a
los atributos y métodos del objeto diferenciando, por ejemplo, una variable local
mi_var de un atributo del objeto self.mi_var.

Si volvemos al método __init__ de nuestra clase Coche veremos cómo se utiliza
self para asignar al atributo gasolina del objeto (self.gasolina) el valor que el
programador especificó para el parámetro gasolina. El parámetro gasolina se
destruye al final de la función, mientras que el atributo gasolina se conserva (y
puede ser accedido) mientras el objeto viva. Para crear un objeto se escribiría el
nombre de la clase seguido de cualquier parámetro que sea necesario entre
paréntesis. Estos parámetros son los que se pasarán al método __init__, que
como decíamos es el método que se llama al instanciar la clase.

Entonces, cómo es posible que a la hora de crear nuestro primer objeto pasemos
un solo parámetro a __init__, el número 3, cuando la definición de la función
indica claramente que precisa de dos parámetros (self y gasolina). Esto es así
porque Python pasa el primer argumento (la referencia al objeto que se crea)
automáticamente. Ahora que ya hemos creado nuestro objeto, podemos acceder
a sus atributos y métodos mediante la sintaxis objeto.atributo y objeto.
método():

![image](https://user-images.githubusercontent.com/91554777/176511788-7d22e8c2-18be-43af-b543-0e26d76e1a72.png)

### Herencias

Hay tres conceptos que son básicos para cualquier lenguaje de programación
orientado a objetos: el encapsulamiento, la herencia y el polimorfismo.
En un lenguaje orientado a objetos cuando hacemos que una clase (subclase)
herede de otra clase (superclase) estamos haciendo que la subclase contenga
todos los atributos y métodos que tenía la superclase. No obstante al acto de
heredar de una clase también se le llama a menudo “extender una clase”.
Supongamos que queremos modelar los instrumentos musicales de una banda,
tendremos entonces una clase Guitarra, una clase Batería, una clase Bajo, etc.
Cada una de estas clases tendrá una serie de atributos y métodos, pero ocurre
que, por el mero hecho de ser instrumentos musicales, estas clases compartirán
muchos de sus atributos y métodos; un ejemplo sería el método tocar().

Es más sencillo crear un tipo de objeto Instrumento con las atributos y métodos
comunes e indicar al programa que Guitarra, Batería y Bajo son tipos de
instrumentos, haciendo que hereden de Instrumento. Para indicar que una clase
hereda de otra se coloca el nombre de la clase de la que se hereda entre
paréntesis después del nombre de la clase:

![image](https://user-images.githubusercontent.com/91554777/176511945-328ad757-4d55-4ebf-8591-c2737ff75e3f.png)

Cómo Batería y Guitarra heredan de Instrumento, ambos tienen un método
tocar() y un método romper(), y se inicializan pasando un parámetro precio. Pero,
¿qué ocurriría si quisiéramos especificar un nuevo parámetro tipo_cuerda a la
hora de crear un objeto Guitarra? Bastaría con escribir un nuevo método __init__
para la clase Guitarra que se ejecutaría en lugar del __init__ de Instrumento.
Esto es lo que se conoce como sobreescribir métodos. Ahora bien, puede ocurrir
en algunos casos que necesitemos sobreescribir un método de la clase padre,
pero que en ese método queramos ejecutar el método de la clase padre porque
nuestro nuevo método no necesite más que ejecutar un par de nuevas
instrucciones extra.

En ese caso usamos la sintaxis SuperClase.metodo(self, args) para llamar al
método de igual nombre de la clase padre. Por ejemplo, para llamar al método
__init__ de Instrumento desde Guitarra usamos Instrumento.__init__(self,
precio)

Observa que en este caso si es necesario especificar el parámetro self.

### Herencias Múltiples
En Python, a diferencia de otros lenguajes como Java o C#, se permite la
herencia múltiple, es decir, una clase puede heredar de varias clases a la vez.
Por ejemplo, podríamos tener una clase Cocodrilo que heredara de la clase
Terrestre, con métodos como caminar() y atributos como velocidad_caminar y
de la clase Acuatico, con métodos como nadar() y atributos como
velocidad_nadar. Basta con enumerar las clases de las que se hereda
separándolas por comas:

![image](https://user-images.githubusercontent.com/91554777/176512054-05753f3c-1b60-413d-9aa6-76924ea57d02.png)

En el caso de que alguna de las clases padre tuvieran métodos con el mismo
nombre y número de parámetros las clases sobrescribirá la implementación de
los métodos de las clases más a su derecha en la definición. En el siguiente
ejemplo, como Terrestre se encuentra más a la izquierda, sería la definición de
desplazar de esta clase la que prevalecerá, y por lo tanto si llamamos al método
desplazar de un objeto de tipo Cocodrilo lo que se imprimiría sería “El animal
anda”.

![image](https://user-images.githubusercontent.com/91554777/176512107-3e3cb006-07d4-405a-9106-5f3fd4485a65.png)

### Polimorfismo
El polimorfismo es uno de los pilares básicos en la programación orientada a
objetos, por lo que para entenderlo es importante tener las bases de la POO y la
herencia bien asentada. El término polimorfismo tiene origen en las palabras poly
(muchos) y morfo (formas), y aplicado a la programación hace referencia a que los
objetos pueden tomar diferentes formas. ¿Pero qué significa esto? Pues bien,
significa que objetos de diferentes clases pueden ser accedidos utilizando el mismo
interfaz, mostrando un comportamiento distinto (tomando diferentes formas) según
cómo sean accedidos. En lenguajes de programación como Python, que tiene tipado
dinámico, el polimorfismo va muy relacionado con el duck typing.

El término polimorfismo visto desde el punto de vista de Python es complicado de
explicar sin hablar del duck typing, por lo que te recomendamos la lectura. Al ser
un lenguaje con tipado dinámico y permitir duck typing, en Python no es necesario
que los objetos compartan un interfaz, simplemente basta con que tengan los
métodos que se quieren llamar.

![image](https://user-images.githubusercontent.com/91554777/176512793-0e30ecf3-42fc-4ca3-ad8b-6ba7e00aa537.png)

Por otro lado tenemos otras dos clases, Perro, Gato que heredan de la anterior.
Además, implementan el método hablar() de una forma distinta.

![image](https://user-images.githubusercontent.com/91554777/176512865-1a137b00-571d-4cd9-8c6c-d9ae1da7e75c.png)

A continuación creamos un objeto de cada clase y llamamos al método hablar().
Podemos observar que cada animal se comporta de manera distinta al usar
hablar().

![image](https://user-images.githubusercontent.com/91554777/176512927-1c1c5cd6-3196-422c-881d-fac86cdbb4f3.png)

### Encapsulación
La encapsulación se refiere a impedir el acceso a determinados métodos y
atributos de los objetos estableciendo así qué puede utilizarse desde fuera de la
clase.

Esto se consigue en otros lenguajes de programación como Java utilizando
modificadores de acceso que definen si cualquiera puede acceder a esa función
o variable (public) o si está restringido el acceso a la propia clase (private).
En Python no existen los modificadores de acceso, y lo que se suele hacer es
que el acceso a una variable o función viene determinado por su nombre: si el
nombre comienza con dos guiones bajos (y no termina también con dos guiones
bajos) se trata de una variable o función privada, en caso contrario es pública.
Los métodos cuyo nombre comienza y termina con dos guiones bajos son
métodos especiales que Python llama automáticamente bajo ciertas
circunstancias.

En el siguiente ejemplo sólo se imprimirá la cadena correspondiente al método
público(), mientras que al intentar llamar al método __privado() Python lanzará
una excepción quejándose de que no existe (evidentemente existe, pero no lo
podemos ver porque es privado).

![image](https://user-images.githubusercontent.com/91554777/176513028-0ff1e388-6d9a-4daa-8ff9-996d58083b99.png)

Este mecanismo se basa en que los nombres que comienzan con un doble guión
bajo se renombran para incluir el nombre de la clase (característica que se
conoce con el nombre de name mangling). Esto implica que el método o atributo
no es realmente privado, y podemos acceder a él mediante una pequeña trampa:

![image](https://user-images.githubusercontent.com/91554777/176513144-1e62d04f-0022-4d00-9d04-e60c7a01af62.png)

En ocasiones también puede suceder que queramos permitir el acceso a algún
atributo de nuestro objeto, pero que este se produzca de forma controlada. Para
esto podemos escribir métodos cuyo único cometido sea este, métodos que
normalmente, por convención, tienen nombres como getVariable y setVariable;
de ahí que se conozcan también con el nombre de getters y setters.

![image](https://user-images.githubusercontent.com/91554777/176513217-0e66c465-4756-471b-a9ef-615a6b1299bf.png)

Esto se podría simplificar mediante propiedades, que abstraen al usuario del
hecho de que se está utilizando métodos entre bambalinas para obtener y
modificar los valores del atributo:

![image](https://user-images.githubusercontent.com/91554777/176513280-c6457cf9-997e-426e-b1c2-5728c7973387.png)

Esto se podría simplificar mediante propiedades, que abstraen al usuario del
hecho de que se está utilizando métodos entre bambalinas para obtener y
modificar los valores del atributo.


# RESUMIENDO

### NOTA: Antes de adentrarte en la programación orientada a objetos, DEBEMOS REFORZAR los conocimientos básicos de Python, realiza ejercicios, establece metas medibles y alzanzables, exígete cada vez más.

Hasta hoy  hemos visto de forma básica pero ya funcional:

* Variable: son "etiquetas" que permiten hacer referencia a los datos
* Operadores aritméticos: Suma (+), resta (-), multiplicación (*), división (/), división entera (//), módulo (%).
* Tipos de datos: Numéricos (enteros, flotantes, complejos), Secuencias (cadenas, listas, tuplas), Booleanos (Verdadero, Falso), Diccionarios.
* Expresiones booleanas: Expresiones en las que el resultado es True o False.
* Condicional: Evalúa una expresión booleana y realiza algún proceso dependiendo del resultado. Se maneja mediante sentencias if/else.
* Bucle: Ejecución repetida de bloques de código. Pueden ser bucles for o while.
* Funciones: Bloque de código organizado y reutilizable. Se crean con la palabra clave def.
* Argumentos: Objetos que se pasan a una función. Por ejemplo: sum([1, 2, 4])

Además conocemos como y donde escribir Python y como ejecutarlo
* Ejecutar un script de Python desde la consola.
* Cuadernillos Jupyter en VSCode
* Página de jupyter
* Google colab

## ¿Qué es la programación orientada a objetos en Python?
La programación orientada a objetos (POO) es un paradigma de programación en el que podemos pensar en problemas complejos como objetos.

Un paradigma es una teoría que proporciona la base para resolver problemas.

Así que cuando hablamos de POO, nos referimos a un conjunto de conceptos y patrones que utilizamos para resolver problemas con objetos.

Un objeto en Python es una colección única de datos (atributos) y comportamiento (métodos). Puedes pensar en los objetos como cosas reales que te rodean:
  
Los datos (atributos) son siempre sustantivos, mientras que los comportamientos (método) son siempre verbos.
  
Esta compartimentación es el concepto central de la programación orientada a objetos. Se construyen objetos que almacenan datos y contienen tipos específicos de funcionalidad.
  
## ¿Por qué utilizamos la programación orientada a objetos en Python?

  La POO permite crear software seguro y fiable. Muchos marcos y bibliotecas de Python utilizan este paradigma para construir su código base. Algunos ejemplos son Django, Kivy, pandas, NumPy y TensorFlow.

Veamos las principales ventajas de usar OOP en Python.

Ventajas de la POO de Python
Las siguientes razones te harán optar por utilizar la programación orientada a objetos en Python.

Todos los lenguajes de programación modernos utilizan la POO
Este paradigma es independiente del lenguaje. Si aprendes POO en Python, podrás utilizarlo en lo siguiente:

* Java
* PHP 
* Ruby
* Javascript
* C#
* Kotlin
  
Todos estos lenguajes están orientados a objetos de forma nativa o incluyen opciones para la funcionalidad orientada a objetos. Si quieres aprender cualquiera de ellos después de Python, será más fácil: encontrarás muchas similitudes entre los lenguajes que trabajan con objetos.

#### La POO te permite codificar más rápido
  Codificar más rápido no significa escribir menos líneas de código. Significa que puedes implementar más funciones en menos tiempo sin comprometer la estabilidad de un proyecto.

La programación orientada a objetos te permite reutilizar el código mediante la implementación de la abstracción. Este principio hace que tu código sea más conciso y legible.

Como ya sabrás, los programadores pasan mucho más tiempo leyendo código que escribiéndolo. Es la razón por la que la legibilidad es siempre más importante que sacar características lo más rápido posible.
  
#### La OOP te ayuda a evitar el código espagueti

La programación orientada a objetos nos da la posibilidad de comprimir toda la lógica en objetos, evitando así largos trozos de if’s anidados.
  
#### La POO mejora el análisis de cualquier situación
  
## Programación estructurada frente a la programación orientada a objetos
La programación estructurada es el paradigma es la forma más sencilla de construir un pequeño programa.

Se trata de ejecutar un programa Python de forma secuencial. Eso significa que le das al ordenador una lista de tareas y luego las ejecutas de arriba a abajo.

  ![image](https://user-images.githubusercontent.com/91554777/177200456-2f43b1f6-3710-4077-b286-be4de9e8558f.png)
  
* Ninguno de los dos paradigmas es perfecto (la POO puede resultar abrumadora en proyectos sencillos).
* Estas son solo dos formas de resolver un problema; hay otras por ahí.
* La POO se utiliza en grandes bases de código, mientras que la programación estructurada es principalmente para proyectos sencillos.

En Python, todo es un objeto.

Recuerda la definición de objeto: Un objeto en Python es una única colección de datos (atributos) y comportamiento (métodos).

Esto coincide con cualquier tipo de datos en Python.

Una cadena es una colección de datos (caracteres) y comportamientos (upper(), lower(), etc.). Lo mismo ocurre con los enteros, los flotantes, los booleanos, las listas y los diccionarios.
  
Una clase es como una plantilla. Te permite crear objetos personalizados basados en los atributos y métodos que definas.
  
  ![image](https://user-images.githubusercontent.com/91554777/177216427-c5ba2d4f-f8f0-4b37-863d-ba7f572f662d.png)
  
Para definir una clase en Python, se utiliza la palabra clave class, seguida de su nombre.
  
Nota: En Python, utilizamos la convención de nombres en mayúsculas para nombrar las clases.
 
El método __init__() también se llama «constructor». Es llamado por Python cada vez que instanciamos un objeto.
  
### 1. Abstracción
  
La abstracción oculta al usuario la funcionalidad interna de una aplicación. El usuario puede ser el cliente final u otros desarrolladores.


Podemos encontrar abstracción en nuestra vida cotidiana. Por ejemplo, sabes cómo usar tu teléfono, pero probablemente no sepas exactamente lo que ocurre dentro de él cada vez que abres una aplicación.

### 2. Herencia
  
La herencia nos permite definir múltiples subclases a partir de una clase ya definida.
  
Puedes pensar en ello como el concepto de herencia genética en la vida real. Los hijos (subclases) son el resultado de la herencia entre dos padres (superclases). Heredan todas las características físicas (atributos) y algunos comportamientos comunes (métodos).
La herencia nos permite definir múltiples subclases a partir de una clase ya definida.

  
### 3. Polimorfismo
El polimorfismo nos permite modificar ligeramente los métodos y atributos de las subclases previamente definidas en la superclase.

El significado literal es «muchas formas«. Esto se debe a que construimos métodos con el mismo nombre pero con diferente funcionalidad.
  
### 4. Encapsulación
La encapsulación es el proceso en el que protegemos la integridad interna de los datos en una clase.
  
Existen métodos especiales llamados getters y setters que nos permiten acceder a atributos y métodos únicos.

Imaginemos una clase Humana que tiene un único atributo llamado _altura. Este atributo solo se puede modificar dentro de ciertas restricciones (es casi imposible ser más alto que 3 metros).
  
  
Se define como el “ocultamiento del estado” osea de “los datos miembros de un objeto”. Hablamos de ocultar los datos de atributos o métodos, más específicamente de protegerlos para que solo puedan ser cambiados mediante “operaciones definidas” para ello. Esto nos asegura por ejemplo que “no podremos modificar un atributo si no es a través de un método que hallamos creado específicamente para ello” y aquí es donde nacen los famosos “Getter, Setter, Deleter”

Anteriormente creamos clases con sus atributos y métodos públicos, es decir, que son accesibles desde su instancia. Basta con crear un objeto a partir de esa clase y podremos acceder y modificar libremente sus atributos. Y no solo desde su instancia sino también desde otra clase que herede de la anterior, por lo que un atributo que almacena información sensible puede ser modificado fácilmente.

      class Usuario ():
          def __init__(self, nombre, folio):
              self.nombre = nombre
              self.folio = folio

      Usuario1 = Usuario ("Roberto", "12345")
      print (Usuario1.nombre, Usuario1.folio)
      
  salida
 
      (‘Roberto’, ‘12345’)

* Atributos protegidos en Python (“_”)

      class Usuario ():
          def __init__(self, nombre, folio):
              self.nombre = nombre
              self._folio = folio

      Usuario1 = Usuario ("Roberto", "12345")
      print (Usuario1.nombre, Usuario1._folio)
      
 salida
 
      (‘Roberto’, ‘12345’)
      
Como ves el atributo clave esta precedido por un guión bajo, lo que indica que es un atributo protegido. Lo cual establece que solo puede ser accedido por esa clase y sus sub-clases, es decir, aquellas que hereden de la clase padre. Se suele ver muy a menudo como una buena practica para atributos o métodos de uso interno y también para evitar la colisión de los mismos nombres de métodos o atributos causado por herencia. 

* Atributos privados en Python (“__”)

En el caso de un atributo privado estamos indicando que este solo podrá ser accedido o modificado si se especifica la clase precedida por un guión bajo seguida del atributo precedido por doble guión bajo.

     class Usuario ():
              def __init__(self, nombre, clave):
                  self.nombre = nombre
                  self.__folio = folio

          Usuario1 = Usuario ("Roberto", "12345")
          print (Usuario1.nombre, Usuario1.__folio)
      
 salida
 
      AttributeError: ‘usuario’ object has no attribute ‘__folio’
      
La forma correcta de acceder a el sería especificando primero la clase a la que pertenece de la siguiente manera:

      class Usuario ():
          def __init__(self, nombre, folio):
              self.nombre = nombre
              self.__folio = folio

      Usuario1 = Usuario ("Roberto", "12345")
      print (Usuario1.nombre, Usuario1._Usuario__folio)
      
salida

      (‘Roberto’, ‘12345’)
      
      
Podemos acceder desde la misma clase pero desde fuera

          class Usuario (object):
              def __init__(self, nombre, folio):
                  self.__nombre = nombre
                  self.__folio = folio

              def imprimir(self):
                return self.__folio + ' ' + self.__nombre

              def pedir(self,nombreFolio):
                self.__nombre, self.__folio = nombreFolio.split(' ')

          Usuario1 = Usuario ("Roberto", "12345")
          Usuario1.imprimir()
          Usuario1.pedir='juan d5f4f'
          print(Usuario1.pedir)

Como ves podemos acceder igualmente a un atributo por más que sea privado y modificarlo de la misma manera. Pero no es lo que se “considera correcto”. Por lo que para ello si deseamos implementar métodos que nos permitan modificar estos atributos de la forma que se suele hacer en otros lenguajes donde se aplica “encapsulamiento” podemos hacerlo utilizando Getter, Setter, Deleter mediante el uso del decorador @Property

En python dentro de las clases podríamos decir que todo son atributos, incluso los métodos podríamos definirlos como “atributos llamables” y las propiedades “atributos personalizables”. Por ende ahora:

Las propiedades son atributos que “manejamos” mediante Getter, Setter y Deleter.

“Atributos manejables” que nos permiten invocar código personalizado al ser creados, modificados o eliminados.

### @Property en python

La función integrada property() nos permitirá interceptar la escritura, lectura, borrado de los atributos y ademas nos permiten incorporar una documentación sobre los mismos. La sintaxis para invocarla es la siguiente:

          @property

Si nosotros no pasamos alguno de los parámetros su valor por defecto sera None.

Getter: Se encargará de interceptar la lectura del atributo. (get = obtener)

Setter : Se encarga de interceptar cuando se escriba. (set = definir o escribir)

Deleter : Se encarga de interceptar cuando es borrado. (delete = borrar)

doc :  Recibirá una cadena para documentar el atributo. (doc = documentación)

