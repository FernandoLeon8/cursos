
# Fundamentos de Bases de Datos

## Teoría general de Bases de Datos

- Las Bases de Datos surgen de la idea de tener un espacio dónde poder almacenar de una forma mucho más eficiente toda la información de nuestros proyectos. Anteriormente este almacenamiento era en papel, y aunque a la fecha algunas empresas por temas de regulación lo siguen haciendo en parte así, el tener una Base de Datos ha permitido tener mucho más control de la información.
- **Los datos no son información.** Solo en el momento que creamos un reporte que contenga ciertos datos, éstos se convierten en información.
- **DBMS** = Data Base Management System o **SGBD** = Sistemas de Gestión de Bases de Datos.

### Propósito general de las Bases de Datos
- **1950-1960**: Maquinas tabuladoras, tarjetas perforadas y cintas magnéticas.
- **1960-1979**: Modelos jerárquicos, discos duros, modelo de data relacional, transacciones en tiempo real.
- Un disco duro tiene **información persistente**, o sea que perdura en el tiempo.
- **1970-1980**: SQL, Sistemas SQL comerciales, bases de datos paralelas y distribuidas, bases de datos orientadas a objetos.
- **SQL es un estándar**, la mayoría de los comandos básicos, en cualquier tipo de datos que sea SQL deben funcionar (MariaDB, MySQL, etc).
- **1980-1990**: Data mining, data warehouse, e-commerce.
- **2000-Actualidad**: XML, administración automatizada, analytics, big data, No SQL, InMemory, Scale Out, Systems of Engagement.


### Tipos de Bases de Datos y sus aplicaciones en la industria

- Las **Bases de Datos** se pueden dividir en:
    - **Bases de Datos Relacionales**
    - **Bases de Datos no Relacionales**
- Bases de Datos Relacionales empresariales (más importantes)
    - **DB2**
    - **SQL Server**
    - **Oracle**
- Algunas **Bases de Datos Relacionales** comunes:
    - **MariaDB**: Es una distribución de Bases de Datos que deriva de MySQL.
    - **Redis**: Una Base de Datos que en la actualidad se trabaja mucho.
    - **neo4j**: Es una Base de Datos basada en nodos. Está centrada en grafos que nos va a permitir encontrar relaciones entre objetos. Muy común en eCommerce.
    - **Cassandra**: Es una Base de Datos muy importante del proyecto Apache. Trabaja con grandes volúmenes de datos.
    - **MongoDB**: Es una Base de Datos en NoSQL que se basa en trabajar en varias instancias.
    - **PostrgreSQL**: Esta es una Base de Datos comunitaria pero tiene una versión entreprise que tiene soporte.


### Visión general de los datos

**¿Qué es un dato?**
Un dato es algo que nos va a permitir describir un objeto. Ese objeto global lo vamos a poder llamar “Entidad”. Una entidad puede estar llena de datos.

**Entidad**: Abstracción de un objeto que tiene características.
**Relación**: Como se comportan los objetos con respecto a otros objetos.

Existen **3 niveles de Abstracción en las Bases de Datos:**
- **Conceptual**: Se tiene que empezar a modelar una Base de Datos dependiendo de lo que se quiere hacer basado en los conceptos de “entidad” y “relación”.
- **Lógico**: El diagrama lógico nos va a resolver ciertas dudas de consistencia, para evitar crear loops o evitar que tenga cosas que no tengan sentido en nuestro proyecto.
- **Físico**: Es finalmente cómo lo va a ver la Base de Datos.


### Tipos de Datos

Igual que en cualquier lenguaje de programación, existen **variables** en las **Bases de Datos**:
    - **Caracteres**: Pueden ser desde letras hasta caracteres especiales.
    - **Numérico**: Del 0 al 9 pero con una longitud especial.
    - **Varchar**: Caracteres con un formato más variable.
    - **Imagen** Para manejar images no se recomienda BD relacional, se recomiendan **BD Mongo SQL**, el **concepto HDFS con Hadoop** y **JPFS**
    - **Fecha**: Generalmente van acompañadas de una hora.
    - **Moneda**: esto facilita todo si se trabaja con diferentes denominaciones.
    - **Texto**: Variables que tienen mayor tamaño que un char o que un varchar.
    - **Bit**: Se puede trabajar con 1 y 0 o también con verdadero y falso.
    - **Decimal**

**Esquema** = Es la estructura lógica que va a tener una Base de Datos.
**Instancia** = Contenido de partículas que tiene una Base de Datos en un instante de tiempo.

¿Qué debemos esperar para modelar una **Base de Datos**?
    - Los datos.
    - La relación que existe entre los datos.
    - Restricciones de los datos.

Existen 3 cosas para poder hacer la descripción de una **Base de Datos**:
    - **DML** = Data Manipulation Language o Lenguaje de Manipulación de Datos.
    - **DDL** = Data Definition Language o Lenguaje de Definición de Datos.
    - **SQL** = Structured Query Language o Lenguaje de Consulta Estructurada.

**Otros tipos de Bases de Datos:**
    - Bases de Datos Relacionales
    - Basadas en Objetos Relacionales
    - XML
    - NoSQL
    - In-Memory


### Diferentes tipos de Bases de Datos

**Características de Bases de Datos SQL:**
    - Es un lenguaje estructurado.
    - Tiene un esquema de tablas.
    - Tiene integración con otros tipos de archivos.
    - Tiene indexación por medio de árboles.
**Características de Bases de Datos NoSQL**:
    - Se puede trabajar con un lenguaje estructurado o con uno no estructurado.
    - Tiene diferente tipo de indexación. Se utiliza normalmente Json.
    - Tiene un crecimiento horizontal.
**Características de Bases de Datos Analíticas y de Bigdata**:
    - Son de lenguaje no estructurado.
    - Tiene integración de muchos sistemas.
    - Tiene integración también a sistemas tradicionales y sistemas de engagement.
    - Principio “divide y vencerás”
    - Se basa en esquemas Scale Out.
    - Crecimiento horizontal.
**Características de Bases de Datos basadas en aceleración**:
    - Normalmente basadas in Memory.
    - Uso de aceleradores como GPU, flash cards, FPGAs.
    - Tienen estructuras diferentes, por ejemplo, basadas en nodos.
    - Uso frecuente de ambientes empresariales productivos y de datawarehouse.

**Bases de datos SQL**
    - La indexación funciona como un indice de un libro o de un temario, nos dice donde encontramos un tema y en que pagina.
    - La indexación en SQL se hace por medio de una estructura de arbol, esta nos permite hacer busquedas.
    - Existe el problema que cuando se buscan tipos de datos que no estan necesariamente estructurados en una estructura de datos se busca desde el primer dato hasta el ultimo.
    - Ejemplos; PostgreSQL, MariaDB.

**Bases de Datos No SQL**
    - La indexación funciona con objetos JSON, no necesariamente funciona como un arbol, se pueden hacer indices dividiendo los objetos por sus caracteristica y particularidades.
    - Ejemplos; MongoDB, Cassandra.

**Bases de datos Analíticas y de Bigdata**
    - Lenguaje no estructurado, Integración de muchos sistemas, Sistemas tradionales y de segagement, principio de divide y venceras, basado en esquemas Scale Out
    - Ejemplos; Hadoop, Hortonworks, Spark

**Bases de datos basadas en aceleración**
    - Normalmente basadas "*In Memory*", Uso de aceleradores como GPU, Flash cards, FPGAs, Estructuras diferentes por ejemplo basadas en nodos, uso frecuente en ambientes empresariales productivos y de datawerehouse
    - Son bases de datos muy rápidas que sin embargo no tienen persistencia.
    - Ejemplos; Redis, neo4j, Kinetica.

**Formas de usos en las bases de datos:**
    - On premise open source, bases de datos de formato empresarial u opensource instalada en nuestra maquina sin una gran infraestructura.
    - Licenciamiento por cores o sockets, se paga dependiendo de ciertas características; como el hardware en el que va a correr.
    - Licenciamiento modular, se paga por funcionalidades o modulos para necesidades diferentes.
    - Pago por uso a través de SAAS(Software As A Service) o PAAS (Platform As A Service). Es como adquirir una renta y pagar por usar una base de datos.
    - Suscripción de nodos de computo, funciona para plataformas como Hadoop el cual no es centralizado y trabaja de forma distribuida, se paga por nodo utilizado.


### Reto ¿Hadoop y Blockchain podrían cambiar una Base de Datos tradicional?


## Bases de Datos Relacionales
### ¿Qué es una Entidad?

**Entidad** = Es una abstracción del mundo real.
**Barker** = Aquí una entidad se representa como una caja, es una caja que va a tener atributos. Estos atributos van a poder ser obligatorios u opcionales.

[Barker’s Notation](http://www.vertabelo.com/blog/technical-articles/barkers-erd-notation)

**Recomendación**:
El formato para trabajar con los ID debe ser “number”. No siempre va a poder ser así, pero es lo más recomendable.


### ¿Qué es una Relación?

Para definir una **Relación** tenemos que tener en cuenta los siguientes puntos:
    - **La obligatoriedad**. Ésta se denota con una línea continua.
    - **Opcional**. Se representa con una línea punteada.
**Datos importantes**:
El símbolo con el que representamos la característica “de uno a muchos” es con la llamada pata de gallo, que gráficamente es una línea continua con dos líneas en 45 grados en cada lado.
```
0 - 1 ----------- (cero a uno: es obligatorio pero solo se puede tener uno)
1 - 1 _______ (uno a uno: es obligatorio y solo se puede tener uno)
0 - M ----------- ≡ (cero a muchos: no es obligatorio y se puede tener muchos)
1 - M _______ ≡ (uno a muchos: es obligatorio y se puede tener muchos)
M - M ≡ ----------- ≡ (muchos a muchos: no es obligatorio y se puede tener muchos)
```

### Características o datos de una Entidad

eje:
Se recomienda que sean de tipo **numérico** porque estos tipos de datos son mas **rápidos** de encontrar por medio de una **búsqueda**, ya que solo hay 10 posibilidades (0 a 9) de comparación a diferencia de un tipo de dato **caracter** donde hay que hacer al rededor de 70 comparaciones.


### ¿Ya aparecieron las llaves?
- Las llaves nos dan acceso a los datos de una entidad, su notación es la de numeral **#.**
- Las llaves tienen que ser **irrepetibles y obligatorias**, por lo tanto el ID puede ser una llave.
- Una llave puede ser **compuesta**, esta se compone de 2 numeros, entre ID y Numero de seguro social. (Como un numero de teléfono móvil).
- Las llaves **foráneas** son llaves que van a estar en nuestra tabla, que no necesariamente son nuestras llaves primarias pero van a permitir acceder a otra tabla donde ahí sean llaves primarias.
- Una llave **foranea** tiene que ser llave **primaria** de una tabla (entidad).
- Las llaves son fundamentales por que son obligatoriamente **índices**, los cuales permiten encontrar los datos cuando se necesitan de una forma rápida y ordenada.


### Índices e Indexación
#### Para tomar en cuenta:
- Las llaves primarias obligatoriamente van a ser índices.
- Las Bases de Datos indexan con un algoritmo llamado:Árboles B+
- Los Árboles B+ son una estructura que va a tener un tronco, tres raíces, de las cuales se van a ir derivando tres raíces más por cada una, hasta donde sea necesario.
- Por defecto todas las Bases de Datos están indexadas, así no le pongamos índices. Lo que sucede es que la Base de Datos siempre obliga a indexar porque siempre tienen un atributo que está oculto, este atributo es RowID.

Representa una dirección de la base de datos, ocupada por una única fila. El ROWID de una fila es un identificador único para una fila dentro de una base de datos. No hay dos filas con el mismo ROWID. Este tipo de dato sirve para guardar punteros a filas concretas. El ROWID se compone de:
- Número de datafile donde se almacena la fila
- Dirección del bloque donde está la fila
- Posición dentro del bloque
Siempre que queramos obtener una fila de la forma más rápida posible, debemos hacerlo a través de su ROWID. Un uso típico suele ser obtener un listado de ROWIDs con un SELECT, y después acceder a cada una de las filas directamente con la condición del ROWID.
```
                                            |
                                            |
                                -------------------------
                                |           |           |
                                |J          |K          |L
                            ---------   ---------   ---------
                            |   |   |   |   |   |   |   |   |
                            |   |   |   |   |   |   |   |   |
                            |   |   |   |   |   |   |   |   |
                            A   B   C   D   E   F   G   H   I
```

### Constrains o Restricciones
- Las restricciones se pueden trabajar desde la Base de Datos. Normalmente las validaciones con restricciones se hacen desde la aplicación, pero es importante tener en cuenta que podemos hacerlo de igual forma desde la Base de Datos.
- Las llaves primarias y las llaves foraneas no solamente tienen la restricción Not null, sino que además tienen la restricción unique, no puede haber otra igual.
- Con check, las validaciones que podemos hacer son: Igual, mayor o igual, menor o igual, mayor qué o menor qué.


### Capas de abstracción del modelo Entidad-Relación
- **Capa Conceptual**: En esta capa vamos a tener varias entidades, aún sin nombre definido. Las entidades van a tener cada una sus laves primarias y sus atributos, además van a tener relaciones.
- Para que existan las relaciones “muchos a muchos” se necesitan llaves foráneas en las entidades.
- **Capa Lógica**: El modelo Entidad-Relación para poder procesar las relaciones “muchos a muchos” las va a partir en entidades que se llaman: Entidades Débiles.
- **Capa Física**: Este modelo va a ser el paso del modelo lógico hacia la representación que ya va a tener la Base de Datos. En esta capa, ya cada uno de los datos empieza a entrar en las clasificaciones según su tipo de dato.

![Capas de abstraccion del modelo Entidad-Relacion](https://github.com/macknilan/Cuaderno/blob/master/Fundamentos_de_BD/img/Capas_de_abstraccion_del_modelo_Entidad_Relacion.jpg "E-R")


### Metodología básica de 9 pasos con Barker (Paso 1)

**Paso 1**: Vamos a identificar cuáles son las entidades que van a resolver nuestros problema.
**Recomendación**: Documentarse muy bien acerca del problema que se va a resolver.
Entidades en PLURAL.


### Metodología básica de 9 pasos con Barker (Paso 2)

**Paso 2**: Identificación de las relaciones de las entidades.
**Para tomar en cuenta**: Pueden existir relaciones entre entidades que se relacione entre ellas mismas.

   ---       | Avion | Aerolinea | Ruta | Tripulante | Piloto | Aeropuerto | Pais | Ciudad | Pasajero 
-----        | ----- | -----     | -----| -----      | -----  | -----      | -----| -----  | -----      |
Avion         |  :x: :black_small_square:  |     1:1   |  1:M |    1:M     |   1:M  |     1:M    | :x:  |  :x:   |    1:M     |
Aerolinea    |   1:M |    :x: :black_small_square:    |  1:M |    1:M     |   1:M  |     1:M    | :x:  | :x:    |    1:M     |
Ruta         | :x:   |     1:M   | :x: :black_small_square:  |  :x:       |  :x:   |     1:M    |  1:1 |   1:1  |  :x:       |
Tripulante   | :x:   |     1:1   | :x:  |   :x: :black_small_square:      |  :x:   |    :x:     |:x:   | :x:    |  :x:       |
Piloto       |   1:M |     1:1   |  1:M |   :x:      |  :x: :black_small_square:   |    :x:     |:x:   | :x:    |  :x:       |
Aeropuerto   |   1:M |     1:M   |  1:M |   :x:      |  :x:   |    :x: :black_small_square:     |  1:1 |   1:1  |    1:M     |
Pais         | :x:   |   :x:     |  0:M |   :x:      |  :x:   |      0:M   | :x: :black_small_square:  |   1:M  |   :x:      |
Ciudad       | :x:   |   :x:     |  0:M |   :x:      |  :x:   |      0:M   |  1:1 |  :x: :black_small_square:   |   :x:      |
Pasajero     | :x:   |     1:M   |  1:M |   :x:      |  :x:   |      1:M   | :x:  |  :x:   |   :x:  :black_small_square:     |

**NOTA** Las que estan en diagonal no se relacionan, _regularmente_


### Metodología básica de 9 pasos con Barker (Paso 3)

Entidades y Relaciones en el diagrama conceptual

![Entidad-Relacion](https://github.com/macknilan/Cuaderno/blob/master/Fundamentos_de_BD/img/di_er_fun_bd_platzi.png "E-R")


### Metodología de Diseño (Corrección de paso 2 y 3)

Se tienen que buscar que las relariones sean equivalentes/complementarias NO deben de ser iguales.
La relacion debe de ser en dos sentidos, al menos de 0:1.


   ---       | Avion | Aerolinea | Ruta | Tripulante | Piloto | Aeropuerto | Pais | Ciudad | Pasajero 
-----        | ----- | -----     | -----| -----      | -----  | -----      | -----| -----  | -----      |
Avion        |  :x::black_small_square:  |     1:1   |  :x: |    :x:     |   1:M  |     1:M    | :x:  |  :x:   |    :x:     |
Aerolinea    |   1:M |     :x::black_small_square:   |  1:M |    1:M     |   1:M  |     1:M    | :x:  | :x:    |    1:M     |
Ruta         | :x:   |     1:M   | :x::black_small_square:  |  :x:       |  :x:   |     1:M    |  :x: |   :x:  |  :x:       |
Tripulante   | :x:   |     1:1   | :x:  |   :x::black_small_square:      |  :x:   |    :x:     |:x:   | :x:    |  :x:       |
Piloto       |   1:M |     1:1   |  :x: |   :x:      |  :x::black_small_square:   |    :x:     |:x:   | :x:    |  :x:       |
Aeropuerto   |   1:M |     1:M   |  1:M |   :x:      |  :x:   |    :x::black_small_square:    |  :x: |   1:1  |    :x:     |
Pais         | :x:   |   :x:     |  :x: |   :x:      |  :x:   |      :x:   | :x::black_small_square:  |   1:M  |   :x:      |
Ciudad       | :x:   |   :x:     |  :x: |   :x:      |  :x:   |      0:M   |  1:1 |  :x::black_small_square:   |   :x:      |
Pasajero     | :x:   |     1:M   |  :x: |   :x:      |  :x:   |      :x:   | :x:  |  :x:   |   :x::black_small_square:      |


![Diagrama Entidad-Relacion](https://github.com/macknilan/Cuaderno/blob/master/Fundamentos_de_BD/img/di_er_fun_bd_platzi_1.png "E-R")


### Metodología de Diseño (Paso 4)

**Paso 4**: Asignar atributos a las entidades.

Para hacer un buen ejercicio hay que pensar en:
- ¿Que atributos voy a necesitar?
- ¿Cual va a ser la codificación que voy a utilizar?
- ¿Como los voy a trabajar dependiendo del tipo de dato?

Hasta este punto no nos vamos a fijar en que motor de base de datos vamos a correr.
El **tipo de dato** va a ser **obligatorio** o no **obligatorio**, dando la posibilidad de que sea nulo o no nulo (**Null o Not Null en SQL**).
Vamos a tener **un identificador único** de cada tabla, una **llave primaria**. Mínimo una por tabla.
Para hacer mas **fácil** las consultas hay que tener una **nomenclatura** para cada tabla (como AV_ para avión) y así poder referirnos a los atributos que se repiten en varias tablas (como nombre).
Hay que **revisar el tipo de dato** que vamos a usar, los identificadores se pueden trabajar como serial, así la misma base de datos se va a encargar de que el valor de ese **identificador sea único e irrepetible.**
Definimos la **obligatoriedad** de los datos, las **llaves primarias tienen que ser obligatorias**.


### Metodología de Diseño (Solución del paso 4): Terminando de Aseignar Atributos a las Entidades

__Avion__

Atributo|Tipo|Obligatorio|PK
--------|----|-----------|---|
AV_ID|serial|:x:|:x:
AV_matricula|varchar(8)|:x:|:x:
AV_placa|Varchar(6)|:x:|
AV_nom|Varchar(15)|:x:|
AV_tipo|Varchar(20)|:x:|
AV_marca|Varchar(30)||

__Aerolinea__

|Atributo|Tipo|Obligatorio|PK
--------|----|-----------|---|
|AE_ID|serial|:x:|:x:
|AE_nombre|varchar(20)|:x:|
|AE_fechainicio|timestamp||

__Ruta__

|Atributo|Tipo|Obligatorio|PK
--------|----|-----------|---|
|RU_ID|serial|:x:|:x:
|RU_millas|Number(5,2)|:x:|
|RU_frecuanciaMes|Number(3)||

__Tripulante__

|Atributo|Tipo|Obligatorio|PK
--------|----|-----------|---|
|TP_ID|serial|:x:|:x:
|TP_pasaporte|Varchar(15)|:x:|
|TP_nombre|Varchar(30)|:x:|
|TP_fechaNac|timestamp||
|TP_fechaInicio|timestamp||
|TP_alergias|Varchar(120)|:x:|

__Piloto__

|Atributo|Tipo|Obligatorio|PK
--------|----|-----------|---|
|PI_ID|:x:|:x:|:x:
|PI_pasaporte|Varchar(15)|:x:|:x:
|PI_permisoNavega|Varchar(20)|:x:|:x:
|PI_nombre|Varchar(40)|:x:|
|PI_fechaNac|timestamp||
|PI_fechaInicio|timestamp||
|PI_alergias|Varchar(120)|:x:|

__Aeropuerto__

|Atributo|Tipo|Obligatorio|PK
--------|----|-----------|---|
|AP_ID|serial|:x:|:x:
|AP_nombre|Varchar(40)|:x:|
|AP_numeroPistas|Number(2)|:x:|
|AP_capacidadPasajeros|Number(5)||
|AP_fechainicio|timestamp||

__Pais__

|Atributo|Tipo|Obligatorio|PK
--------|----|-----------|---|
|PA_ID|serial|:x:|:x:
|PA_nombre|Varchar(30)|:x:|

__Ciudad__

|Atributo|Tipo|Obligatorio|PK
--------|----|-----------|---|
|CI_ID|serial|:x:|:x:
|CI_nombre|Varchar(30)|:x:|
|CI_tipoClima|Varchar(50)|:x:|

__Pasajero__

|Atributo|Tipo|Obligatorio|PK
--------|----|-----------|---|
|PS_ID|serial|:x:|:x:
|PS_nombre|Varchar(30)|:x:|
|PS_pasaporte|Varchar(15)||
|PS_contactoEmergencia|Varchar(40)|:x:|



### Metodología de Diseño (Pasos 5, 6 y 7):

#### 5. Generar un diagrama conceptual (entidades, relaciones y atributos).
Las relaciones siempre van en **dos sentidos**:
- A->B
- B->A
- **Identificadores**:
    - ```#``` --> PK (Pimary Key)
    - ```*```(asterisco) --> Obligatorio
    - ```O```(circulo) --> Opcional

#### 6. Modelo lógico.

Las relaciones se hacen por medio de **entidades débiles**, entre las entidades relacionadas, esto es porque no podemos generar muchas **llaves foráneas** en ambas entidades (fuertes).
En estas entidades debiles se usan **ambas llaves primarias** de las entidades (fuertes) que tenían relación.
En las entidades debiles no debería haber tipos de **datos seriales**, estas tendrían que ser **integer**, ya que las entidades debiles no tienen forma de tener consistencia con esa serialidad.


#### 7. Identificar nuevos atributos que generan nuestras entidades débiles.

En las entidades nuevas (ó tablas nuevas), se pueden generar nuevos atributos, que solo se pueden manegar en las nuevas entidades, y que **no son sencillos de manejar en una relación de muchos a muchos.**

## Metodología de Diseño (Paso 8): Construir el Diagrama del Modelo Físico

![Diagrama Entidad-Relacion](https://github.com/macknilan/Cuaderno/blob/master/Fundamentos_de_BD/img/metodologia_de_diseno_paso_8_construir_el_diagrama_del_modelo_fisico.jpg "Paso 8")

Las lineas de las relaciones van a ser **lineas rectas** y **no lineas curvas**, en la relación **uno a muchos** vamos a crear una linea con un sentido que **termina en cabeza de flecha**. Las lineas **1 a 1** ó **0 a 1** se mantienen como antes.
Las llaves foráneas en **entidades debiles** refieren o **apuntan** hacia su **llave primaria** en entidades fuertes.

En el modelo fisico hay que poner el tipo de dato de acuerdo a la base de datos en la que vamos a trabajar.

Los motores de base de datos tienen diferentes implementaciones de los tipos de datos, hay que revisar a que se traducen dependiendo de la base de datos.

### Metodología de Diseño (Paso 9)
### Reto con el paso 4 de la Metodología de Diseño

## Bases de Datos NO Relacionales y Otros tipos de Bases de Datos
### Atomicidad y consistencia
### Aislamiento y durabilidad
### Bases de Datos In-Memory (Cambio de árboles a columnar)
### Otros tipos de Bases de Datos en la industria
### Bases de Datos In-Memory con indexación de columnar
### Proyecto (Paso 1 y 2)
### Proyecto (Paso 3 y 4)
### Proyecto (Continuación del paso 4)
### Metodología de Diseño (Paso 5)
### Metodología de Diseño (Paso 6 y 7)
### Solución de atributos de entidad del proyecto - Atributos adicionales a entidad débil creada
### Metodología de Diseño (Paso 8)
### Llevando nuestro proyecto a SQL (Paso 9)
### Metodología de Diseño (Paso 9)
### Dependencias funcionales
### Normalización, llevando el proyecto hasta tercera forma normal (primera forma normal)
### Normalización, llevando mi proyecto hasta tercera forma normal (segunda forma normal)
### Normalización, llevando mi proyecto hasta tercera forma normal (Cuarta y quinta forma normal)
### Comenzando con SQL
### Comenzando con SQL 2
### ACID desde lo no relacional
### CAP
### Scale Out y Scale Up
### ¿Scale out o Scale up?
### DBMS en nube para poder iniciar una aplicación propia
### Estructura básica del Query 1
### Estructura básica del Query 2
### Estructura básica del Query con más de una tabla
### Estructura básica del Query con más de una tabla 2
### Tuplas y más tuplas
### Insertar registros
### Joins
### Aplicando noSQL 1
### Aplicando noSQL 2
### Aplicando noSQL 3
### Aplicando noSQL 4








































































































































































































































