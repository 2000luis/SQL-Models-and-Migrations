# SQL-Models-and-Migrations

Con carpetas en los directorios que tengan espacio se usa un guion y no se usan espacios para acceder a una carpeta que tenga espacios en git bash



DATA
-------------------------------------------------------------
Database Management Systems
_____________________________________________________________

*MySQL
_____________________________________________________________
*PostgreSQL
_____________________________________________________________
    Tiene una amplia variedad de tipos de datos que soporta
_____________________________________________________________


    *CHAR(size)
    _________________________________________________________
        Un limitado numero de caracteres que puedes especificar


    *VARCHAR(size)
    _________________________________________________________
        Con este tipo de dato puedes especificar un rango del tamaño de caracteres que vas a usar


    *SMALLINT(size)
    _________________________________________________________
        Para un numero pequeño


    *INT
    _________________________________________________________
        Para un numero mediano


    *BIGINT
    _________________________________________________________
        Para un numero demasiado grande


    *FLOAT
    _________________________________________________________
        Para numeros decimales 


    *DOUBLE
    _________________________________________________________
        Numeros decimales mas 
_____________________________________________________________

*SQLite
_____________________________________________________________
    Tiene una lista corta de tipos de datos que soporta
_____________________________________________________________


    *TEXT
    _________________________________________________________
        texto simple, Strings


    *NUMERIC
    _________________________________________________________
        boolean operaciones


    *INTEGER

    _________________________________________________________
        Cualquier numero entero mas los numeros negativos


    *REAL
    _________________________________________________________
        numeros decimales


    *BLOB
    _________________________________________________________
        Cualquier numero binario que con tenga 0s y 1s que podria ser musica, fotos, videos, etc.
_____________________________________________________________

<!-- Ejemplo de como Escribir una table de vuelos -->

    <!-- Se con la palabra clave CREATE TABLE despues se le da un nombre a esa tabla en este caso Flight -->
    CREATE TABLE flights (
        id INTEGER PRIMARY KEY AUTOINCREMENT,
        origin TEXT NOT NULL,
        destination TEXT NOT NULL,
        duration INTEGER NOT NULL
    );

    <!-- Despues se especifica todas las columnas que van a estar presentes en la tabla -->

    <!-- En este caso son id, origin, destination, duration.
    Despues se especifica que tipo de dato va hacer en este caso INTEGER, TEXT, TEXT, INTEGER. -->

    <!-- Despues esta la forma en la que se va a poder ubicar algo en especifica de esa columnas usando PRIMARY KEY. -->

    <!-- El NOT NULL especifica que ese parametro no puede estar vacio siempre debe contener informacion -->

    <!-- El AUTOINCREMENT asegura que ya no sera nesecario escribir un nuevo id  -->
_____________________________________________________________

Constraints
-------------------------------------------------------------
*CHECK
_____________________________________________________________
    revisar que se cumpla una cierta condicion
*DEFAULT
_____________________________________________________________
    agregar un valor por defecto
*NOT NULL
_____________________________________________________________
    Que el resultado no puede estar vacio
*PRIMARY KEY
_____________________________________________________________ 
    Es para saber de que columna ubicar los elementos
*UNIQUE
_____________________________________________________________
    para asegurar que todos los valores sean unicos y que no alla repeticion
_____________________________________________________________

INSERT
-------------------------------------------------------------
<!-- Para insertar algo en la tabla se neesecita usar e commando INSERT INTO seguido de el nombre de la tabla. -->

Despues especificaras entre parentesis el nombre de las columnas en las cuales se agregaran un elemento y el mismo orden en el que se encuentren, asi deberas agregar tu elementos con el argumento VALUES()
_____________________________________________________________
 INSERT INTO flights
    (origin, destination, duration)
    VALUES("New York", "London", 415)

_____________________________________________________________

<!-- Para seleccionar todo de la tabla se escribe -->
SELECT * FROM flights;

<!-- Para seleccionar solo las columnas necesarias -->
SELECT origin, destination FROM flights;

<!-- Para seleccionar solo una fila de la tabla -->
SELECT * FROM flights WHERE     id = 3;

<!-- Para buscar el elemento de una columna con un cierto nombre-->
SELECT * FROM flights WHERE origin = "New York";
_____________________________________________________________

Funciones
-------------------------------------------------------------

    *AVERAGE
    _____________________________________________________________
    Encontrar un porcentaje de alguna categoria

    *COUNT
    _____________________________________________________________
    Puedes contar ciertos elementos 
    
    *MAX
    _____________________________________________________________
    Encontrar el maximo de algo
    
    *MIN
    _____________________________________________________________
    Encontrar el minimo de algo
    
    *SUM
    _____________________________________________________________
    Puedes sumar distintos elementos
    
_____________________________________________________________

UPDATED
-------------------------------------------------------------
El commando UPDATE especifica que quieres actualizar un elemento, despues agregas el nombre del elemento que quisieras actualizar, de ahi especificas que elemento se va a actualizar con SET enseguida el nombre de el elemento que se va actualizar y las condiciones que deben cumplir los elementos para ser actualizados
_____________________________________________________________

UPDATE flights
    SET duracion = 400
    WHERE origin = 'New York'
    AND destino = 'London';
_____________________________________________________________

SELECT * FROM flights;
id  origin    destino  duracion
--  --------  -------  --------
1   New York  London   415
2   New York  London   415
3   Actopan   Ixmi     30
4   Tepa      Rosario  160
_____________________________________________________________

UPDATE flights
SET duracion = 400
WHERE origin = 'New York'
AND destino = 'London';
SELECT * FROM flights;

_____________________________________________________________
Este es el cambio
_____________________________________________________________
id  origin    destino  duracion
--  --------  -------  --------
1   New York  London   400
2   New York  London   400
3   Actopan   Ixmi     30
4   Tepa      Rosario  160
_____________________________________________________________

DELETE
-------------------------------------------------------------

DELETE FROM flights WHERE destino = 'Rosario';

Other Clauses

-------------------------------------------------------------
    *Limit
    _____________________________________________________________
        SELECT * FROM LIMIT 3
    
    *ORDER BY
    _____________________________________________________________
        SELECT * FROM ORDER BY destino
    
    *GROUP BY
    _____________________________________________________________
        SELECT * FROM GROUP BY origin
    
    *HAVING
    _____________________________________________________________
        SELECT * FROM GROUP BY origin HAVING COUNT 3    

JOIN
----------------------------------------------------------------

Se especifica cuales son los elementos de cada tabla
que se va a tomar en cuanta despues se dice de con de son esos elementos con From despues Con JOIN especificas con que otra tabla lo quieres juntar
Y ahora con ON Se especifica co cuales se van a juntar 
_____________________________________________________________
SELECT first, origin, destino
FROM flights JOIN passengers
ON passengers.flight_id = flights.id;
_____________________________________________________________

    *JOIN / INNER JOIN 
    *LEFT OUTER JOIN
    *RIGHT OUTER JOIN
    *FULL OUTER JOIN

CREATE INDEX
----------------------------------------------------------------

CREATE INDEX name_index ON passengers (last);

