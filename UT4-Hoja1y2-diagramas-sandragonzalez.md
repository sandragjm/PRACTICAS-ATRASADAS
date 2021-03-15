# Ejercicios diagramas casos de uso y clases

## Hoja 1. Diagramas de casos de uso

### Ejercicio 1. Taller

En un taller mecánico se introducen los vehículos en un sistema que permite detectar los problemas que tiene el vehículo.
Con la ayuda de los operadores y con los informes que da el sistema del vehículo, el mecánico hará los arreglos pertinentes, mientras el gerente puede actualizar los costos y efectuar el cobro al cliente.

**Solución propuesta:**
~~~
@startuml taller
'https://plantuml.com/es/use-case-diagram

left to right direction
skinparam packageStyle rectangle

Empleado <|- Mecánico
Empleado <|-- Gerente
Empleado <|- Operador

rectangle Sistema {
    Operador -- (Introducir vehículo)
    (Detectar problema) .up.> (Introducir vehículo) : <<extend>>
    Mecánico -- (Reparar vehículo)
    (Reparar vehículo) ..> (Actualizar coste) : <<include>>
    Gerente -- (Efectuar cobro)
    (Efectuar cobro) ..> (Actualizar coste) : <<include>>
}
@enduml
~~~

**Vista previa:**
El código anterior se mostraría así en el documento:

```plantuml
@startuml taller
'https://plantuml.com/es/use-case-diagram

left to right direction
skinparam packageStyle rectangle

Empleado <|- Mecánico
Empleado <|-- Gerente
Empleado <|- Operador

rectangle Sistema {
    Operador -- (Introducir vehículo)
    (Detectar problema) .up.> (Introducir vehículo) : <<extend>>
    Mecánico -- (Reparar vehículo)
    (Reparar vehículo) ..> (Actualizar coste) : <<include>>
    Gerente -- (Efectuar cobro)
    (Efectuar cobro) ..> (Actualizar coste) : <<include>>
}
@enduml
```

### Ejercicio 2. Tienda

En una tienda, un comerciante dispone de un sistema para gestionar su almacén. El sistema incluye las siguientes funciones:
* Gestión de archivo de proveedores.
* Posibilidad de agregar un nuevo artículo (en este caso, el archivo de proveedores se actualiza automáticamente. Si el proveedor no existe, se puede crear).
* Gestión del inventario. Desde esta pantalla, se tiene la opción de imprimir el inventario, eliminar un artículo o editar el archivo de artículos).

**Solución propuesta:**
~~~
@startuml tienda
'https://plantuml.com/es/use-case-diagram

left to right direction
skinparam packageStyle rectangle


actor comerciante

rectangle Sistema {
    comerciante -- (Gestion de archivo)
    comerciante -- (Agregar artículo)
    comerciante -- (Gestión del inventario)

    (Agregar artículo) <.. (crear proveedor) : <<extend>>

    (Gestión del inventario) <.. (imprimir inventario) : <<extend>>
    (Gestión del inventario) <.. (elimitar articulo) : <<extend>>
    (Gestión del inventario) <.. (editar articulo) : <<extend>>
}
@enduml
~~~

**Vista previa:**
```plantuml
@startuml tienda
'https://plantuml.com/es/use-case-diagram

left to right direction
skinparam packageStyle rectangle


actor comerciante

rectangle Sistema {
    comerciante -- (Gestion de archivo)
    comerciante -- (Agregar artículo)
    comerciante -- (Gestión del inventario)

    (Agregar artículo) <.. (crear proveedor) : <<extend>>

    (Gestión del inventario) <.. (imprimir inventario) : <<extend>>
    (Gestión del inventario) <.. (elimitar articulo) : <<extend>>
    (Gestión del inventario) <.. (editar articulo) : <<extend>>
}
@enduml
```

### Ejercicio 3. Gestión de proyectos

La única persona que controla los proyectos es el administrador de proyectos, cuyas funciones son las siguientes:
* Puede agregar, eliminar y actualizar un proyecto, pero para eliminar y actualizar es necesario encontrar el proyecto en cuestión.
* A la hora de actualizar un proyecto se pueden dar dos situaciones:
  * Cambiar la información sobre las tareas del proyecto.
  * Cambiar los recursos asociados al proyecto.
*  Para informar a todos los miembros del equipo sobre los avances en el proyecto se procede emitiendo un documento, que se envía vía e-mail o que se publica en un sitio web conocido por todos.
  
**Solución propuesta:**
~~~
@startuml proyectos
'https://plantuml.com/es/use-case-diagram

left to right direction
skinparam packageStyle rectangle

actor administrador

rectangle Proyectos {

    administrador <-- (Agregar)

    administrador <-- (Eliminar)
    (Eliminar) <.. (Encontrar proyecto) : include

    administrador <-- (Actualizar)
    (Actualizar) <.. (Encontrar proyecto) : include
    (Actualizar) <.. (Cambiar informacion) : extend
    (Actualizar) <.. (Cambiar recursos) : extend

    administrador -- (Emitir documento)
    (Emitir documento) <.. (E-mail) : extend
    (Emitir documento) <.. (Sitio Web) : extend

}
@enduml
~~~

**Vista previa:**
```plantuml
@startuml proyectos
'https://plantuml.com/es/use-case-diagram

left to right direction
skinparam packageStyle rectangle

actor administrador

rectangle Proyectos {

    administrador <-- (Agregar)

    administrador <-- (Eliminar)
    (Eliminar) <.. (Encontrar proyecto) : include

    administrador <-- (Actualizar)
    (Actualizar) <.. (Encontrar proyecto) : include
    (Actualizar) <.. (Cambiar informacion) : extend
    (Actualizar) <.. (Cambiar recursos) : extend

    administrador -- (Emitir documento)
    (Emitir documento) <.. (E-mail) : extend
    (Emitir documento) <.. (Sitio Web) : extend

}
@enduml
```


## Hoja 2. Diagramas de clases

### Ejercicio 1. Empresa

Una aplicación necesita tener información sobre empresas, empleados y clientes. Estos dos últimos se caracterizan por su nombre y edad.
Los empleados tienen un sueldo bruto y los que son directivos tienen una categoría y un conjunto de empleados subordinados.
De los clientes además se necesita saber su teléfono de contacto. 
La aplicación necesita mostrar los datos de empleados y clientes.

**Solución propuesta:**

~~~
@startuml empresa
'https://plantuml.com/class-diagram

Empleado *-- Directivo
Empleado "0..1" -- "0..1" Directivo

Empleado "1..*" --* "1" Empresa
Cliente "0..*" --o "1..*" Empresa


class Empleado {
    - nombre : String
    - edad : int
    - sueldoBruto : float
    + mostrar()
}

class Cliente {
    - nombre : String
    - edad : int
    - telefono : String
    + mostrar()
}

class Directivo {
    - categoría : int
    + mostrar()
}

class Empresa {
    - nombre : String
}
@enduml
~~~

**Vista previa:**
```plantuml
@startuml empresa
'https://plantuml.com/class-diagram

skinparam classAttributeIconSize 0

Empleado *-- Directivo
Empleado "0..1" -- "0..1" Directivo

Empleado "1..*" --* "1" Empresa
Cliente "0..*" --o "1..*" Empresa


class Empleado {
    - nombre : String
    - edad : int
    - sueldoBruto : float
    + mostrar()
}

class Cliente {
    - nombre : String
    - edad : int
    - telefono : String
    + mostrar()
}

class Directivo {
    - categoría : int
    + mostrar()
}

class Empresa {
    - nombre : String
}
@enduml
```

### Ejercicio 2. Biblioteca

Una aplicación necesita tener información sobre una biblioteca. Realiza el diagrama de clases y añade los métodos necesarios para realizar el préstamo y devolución de libros.
La biblioteca tiene copias de libros. Estos últimos se caracterizan por su nombre, tipo (novela, teatro, poesía, ensayo), editorial, año y autor.
Los autores se caracterizan por su nombre, nacionalidad y fecha de nacimiento.
Cada copia tiene un identificador, y puede estar en la biblioteca, prestada, con retraso o en reparación.
Los lectores pueden tener un máximo de 3 libros en préstamo.
Cada libro se presta un máximo de 30 días, por cada día de retraso se impone una multa de dos días sin posibilidad de coger un nuevo libro.

**Solución propuesta:**

~~~
@startuml biblioteca
'https://plantuml.com/class-diagram


Copia "0..3" -- "0..1" Lector
Lector "0..1" -- "0..1" Multa

Copia "1..*" -- "0..1" Libro
Libro "0..1" -- "0..1" Autor

enum tipo {
    novela
    teatro
    poesía
    ensayo
}

enum Estado {
    biblioteca
    prestada
    Retrasado
    En reparación
}


class Libro {
    + Nombre : String
    + Tipo : String
    + Editorial : String
    + Año : int
    + Autor : String
}

class Autor {
    + Nombre : String
    + Nacionalidad : String
    + Fecha Nacimiento : Date
}

class Copia {
    + Identificador : int
    + Estado : String

}

class Lector {
    + Identificador : int
    + Estado : String

}

@enduml
~~~


**Vista previa:**
```plantuml
@startuml biblioteca
'https://plantuml.com/class-diagram

skinparam classAttributeIconSize 0

Copia "0..3" -- "0..1" Lector
Lector "0..1" -- "0..1" Multa

Copia "1..*" -- "0..1" Libro
Libro "0..1" -- "0..1" Autor

enum tipo {
    novela
    teatro
    poesía
    ensayo
}

enum Estado {
    biblioteca
    prestada
    Retrasado
    En reparación
}


class Libro {
    + Nombre : String
    + Tipo : String
    + Editorial : String
    + Año : int
    + Autor : String
}

class Autor {
    + Nombre : String
    + Nacionalidad : String
    + Fecha Nacimiento : Date
}

class Copia {
    + Identificador : int
    + Estado : String

}

class Lector {
    + Identificador : int
    + Estado : String

}

@enduml
```

### Ejercicio 3. Viajes

Especificar un diagrama de clases que describa los vuelos que oferta una compañía de viajes según la siguiente especificación:
* La compañía oferta una serie de vuelos para unas fechas concretas y con un número de plazas.
* La compañía dispone de una flota de aviones con una capacidad que da soporte a los vuelos ofertados.
* Las personas compran billetes para los vuelos que le interesan. Para emitir el billete es necesario conocer el nombre, apellidos y edad del pasajero.
* Los billetes identifican el número de asiento que ocupan.
  
~~~
@startuml biblioteca
'https://plantuml.com/class-diagram

skinparam classAttributeIconSize 0


Compañia -- Avion
Vuelo "0..*" -- "0..*" Persona
(Vuelo, Persona) -- Billete
Vuelo "0..*" --- "1" Avion

enum Genero {
    hombre
    mujer
}

class Compañia{
    - List<Avion>
}

class Avion {
    - modelo : String
    - capacidad : Integer
}

class Vuelo {
    - plazas : Integer
    - fecha: Date
}
class Persona {
    - nombre : String
    - apellidos : String
    - fechaNacimiento : Date
    - sexo : Genero
}
class Billete {
    - asiento : Integer
}

@enduml
~~~


**Vista previa:**
```plantuml
@startuml biblioteca
'https://plantuml.com/class-diagram

skinparam classAttributeIconSize 0

enum Genero {
    hombre
    mujer
}

class Compañia{
    - List<Avion>
}

class Avion {
    - modelo : String
    - capacidad : Integer
}

class Vuelo {
    - plazas : Integer
    - fecha: Date
}
class Persona {
    - nombre : String
    - apellidos : String
    - fechaNacimiento : Date
    - sexo : Genero
}
class Billete {
    - asiento : Integer
}


Compañia -- Avion
Vuelo "0..*" -- "0..*" Persona
(Vuelo, Persona) -- Billete
Vuelo "0..*" --- "1" Avion

@enduml
```

### Ejercicio 4. Proyectos

Especificar un diagrama de clases que describa la gestión de proyectos informáticos siguiendo el proceso unificado:
* Un proyecto requiere de una serie de ciclos de desarrollo.
* Todo ciclo de desarrollo concluye con una versión ejecutable y son necesarias cuatro fases
para completarlo: inicio, elaboración, construcción y transición.
* A su vez las fases requieren varias iteraciones.
* Las iteraciones son una secuencia de actividades, las cuales tienen una duración y necesitan unos recursos (materiales y humanos).
* Las iteraciones pueden producir artefactos de muy distinto tipo (documentación, resultados de pruebas, software).
* Es importante medir el estado de avance del proyecto.

~~~
@startuml proyectos
'https://plantuml.com/class-diagram

skinparam classAttributeIconSize 0

Proyecto o-- "2..*" Ciclo
Ciclo -- VersionEj

Ciclo o-- "4" Fase
Fase  o-- "2..*" Iteración

Iteración <|--"1..*" Artefacto
Artefacto <|-- Documento
Artefacto <|-- Software
Artefacto <|-- Resultado

Iteración o-- "1..*" Actividad
Actividad "0..*" o-- "0..*" Recurso
Recurso <|-- Humano
Recurso <|-- Material

class Proyecto {
    - nombre : String
    - estado_avance
}

class VersionEj {
    - bytes
}

class Fase {
    - tipo : TipoFase
}

enum TipoFase {
    inicio
    elaboración
    construcción
    transición
}

class Iteración {
    - comienzo : Date
}

class Artefacto {}

class Documento {
    - nombre : String
    - ubicación : String
}

class Resultado {
    - nombre : String
}

class Software {
    - bytes : Integer
}

class Actividad {
    - duración : Integer
    - avance : Float
}

class Recurso {}

class Humano {
    - nombre : String 
}

class Material {
    - inventario : String
}
@enduml
~~~

**Vista previa:**
```plantuml
@startuml proyectos
'https://plantuml.com/class-diagram

skinparam classAttributeIconSize 0

Proyecto o-- "2..*" Ciclo
Ciclo -- VersionEj

Ciclo o-- "4" Fase
Fase  o-- "2..*" Iteración

Iteración <|--"1..*" Artefacto
Artefacto <|-- Documento
Artefacto <|-- Software
Artefacto <|-- Resultado

Iteración o-- "1..*" Actividad
Actividad "0..*" o-- "0..*" Recurso
Recurso <|-- Humano
Recurso <|-- Material

class Proyecto {
    - nombre : String
    - estado_avance
}

class VersionEj {
    - bytes
}

class Fase {
    - tipo : TipoFase
}

enum TipoFase {
    inicio
    elaboración
    construcción
    transición
}

class Iteración {
    - comienzo : Date
}

class Artefacto {}

class Documento {
    - nombre : String
    - ubicación : String
}

class Resultado {
    - nombre : String
}

class Software {
    - bytes : Integer
}

class Actividad {
    - duración : Integer
    - avance : Float
}

class Recurso {}

class Humano {
    - nombre : String 
}

class Material {
    - inventario : String
}
@enduml
```

### Ejercicio 5. Instalaciones deportivas

Un centro de instalaciones deportivas quiere hacer una aplicación de reservas. En el centro existen instalaciones deportivas (piscinas, frontones, gimnasios y pistas de tesis). El centro en cuestión tiene socios, de los cuales se almacenan su nombre, dirección, ciudad, provincia, teléfono y cuota. Además, existen una serie de artículos que se pueden reservar si el socio lo requiere (balones, redes y raquetas). Cada instalación es reservada por un socio en una fecha dada desde una hora de inicio hasta una hora de fin. Cada reserva puede tener asociada uno o varios artículos deportivos que se alquilan a parte. Por ejemplo, si yo quiero hacer una reserva para jugar al tenis, tengo que reservar una instalación polideportiva y si lo necesito, las raquetas.

~~~
@startuml instdepor
'https://plantuml.com/class-diagram

skinparam classAttributeIconSize 0

Reserva <|-- ReservaArticulo
Reserva <|- ReservaInstalacion
Centro "1"-up- "1..*" Instalacion
Socio  "1..*" -- "1" Centro
Socio "1..*" -- "0..*" Reserva
Articulo "1" -up- "0..*" ReservaArticulo 
Instalacion "1" -up- "0..*" ReservaInstalacion 

enum TipoInstalacion{
    Piscina
    Frontón
    Gimnasio
    PistaTenis
}

enum TipoArticulo {
    Balón
    Red
    Raqueta
}

class Centro {
    - nombre : String
}

class Instalacion {
    - nombre : String
    - tipo : TipoInstalacion
}

class Socio {
    - nombre : String
    - direccion : String
    - ciudad : String
    - provincia : String
    - telefono : String
    - cuota : Float
}

class Articulo {
    - codigo : Integer
    - descripcion : String 
    - tipo : TipoArticulo
}


class Reserva {
    - id : Integer
    - fecha : Date
    - horaInicio : Date
    - horaFin : Date
}

class ReservaArticulo {
    - cantidad : Integer
}

class ReservaInstalacion {
}

@enduml
~~~



**Vista previa:**
```plantuml
@startuml instdepor
'https://plantuml.com/class-diagram

skinparam classAttributeIconSize 0

Reserva <|-- ReservaArticulo
Reserva <|- ReservaInstalacion
Centro "1"-up- "1..*" Instalacion
Socio  "1..*" -- "1" Centro
Socio "1..*" -- "0..*" Reserva
Articulo "1" -up- "0..*" ReservaArticulo 
Instalacion "1" -up- "0..*" ReservaInstalacion 

enum TipoInstalacion{
    Piscina
    Frontón
    Gimnasio
    PistaTenis
}

enum TipoArticulo {
    Balón
    Red
    Raqueta
}

class Centro {
    - nombre : String
}

class Instalacion {
    - nombre : String
    - tipo : TipoInstalacion
}

class Socio {
    - nombre : String
    - direccion : String
    - ciudad : String
    - provincia : String
    - telefono : String
    - cuota : Float
}

class Articulo {
    - codigo : Integer
    - descripcion : String 
    - tipo : TipoArticulo
}


class Reserva {
    - id : Integer
    - fecha : Date
    - horaInicio : Date
    - horaFin : Date
}

class ReservaArticulo {
    - cantidad : Integer
}

class ReservaInstalacion {
}

@enduml
```

### Ejercicio 6. Sistema operativo

Hacer el Diagrama de Clases que modele el siguiente sistema: Un directorio puede contener muchos otros directorios y puede estar contenido opcionalmente dentro de otro directorio. Todo directorio posee exactamente un usuario que sea su propietario y hay muchos usuarios que están autorizados para utilizar el directorio.

~~~
@startuml ssoo
'https://plantuml.com/class-diagram

'left to right direction
skinparam classAttributeIconSize 0

Directorio "0..1" o-- "1..*" Directorio : tiene

Usuario "1" --- "0..*" Directorio : posee <
Directorio "0..1" -- "1..*" Usuario : autoriza <

class Directorio {
    - nombre : String
}

class Usuario {
    - nombre : String
}

@enduml
~~~

**Vista previa:**
```plantuml
@startuml ssoo
'https://plantuml.com/class-diagram

'left to right direction
skinparam classAttributeIconSize 0

Directorio "0..1" o-- "1..*" Directorio : tiene

Usuario "1" --- "0..*" Directorio : posee 
Directorio "0..1" -- "1..*" Usuario : autoriza 

class Directorio {
    - nombre : String
}

class Usuario {
    - nombre : String
}

@enduml
```


### Ejercicio 7. Compañía de seguridad

Una compañía de seguridad tiene una serie de centrales de alarma distribuidas por zonas dentro de una ciudad. Cada central de alarma está conectada con una serie de edificios. Dentro de cada edificio se dispone de dos tipos de alarmas: alarma de incendios y alarma de robo. Cada alarma está conectada con una serie de sensores (de robo y de fuego). Cuando se activa un sensor de fuego, la alarma correspondiente suena y la compañía de seguridad avisa a los bomberos y a la policía, mientras que si se activa un sensor de robo se avisa únicamente a la policía.

~~~
@startuml seguridad
'https://plantuml.com/class-diagram

'left to right direction
skinparam classAttributeIconSize 0

Central "1" -- "1..*" Edificio
Edificio "1" - "1..*" Alarma : tiene
Edificio "1" - "0..*" Sensor : tiene
Alarma "1" -- "1..*" Sensor 
Alarma <|-- AlarmaFuego
Alarma <|-- AlarmaRobo
AlarmaFuego "0..*" -- "1" Edificio 
AlarmaRobo "0..*" -- "1" Edificio 

class Central {
    - nombre : String
}

class Edificio {
    - nombre : String
    - direccion : String
}

class Alarma {
    + sonar() 
    + avisar()
}

class AlarmaFuego {
}

class AlarmaRobo {
}

class Sensor {
    - estado : Boolean
    - tipo : TipoSensor
}
enum TipoSensor {
    Robo
    Fuego
}
enum estado {
    Activado
    Desactivado
}

@enduml
~~~

**Vista previa:**
```plantuml
@startuml ssoo
'https://plantuml.com/class-diagram

'left to right direction
skinparam classAttributeIconSize 0

Central "1" -- "1..*" Edificio
Edificio "1" - "1..*" Alarma : tiene
Edificio "1" - "0..*" Sensor : tiene
Alarma "1" -- "1..*" Sensor 
Alarma <|-- AlarmaFuego
Alarma <|-- AlarmaRobo
AlarmaFuego "0..*" -- "1" Edificio 
AlarmaRobo "0..*" -- "1" Edificio 

class Central {
    - nombre : String
}

class Edificio {
    - nombre : String
    - direccion : String
}

class Alarma {
    + sonar() 
    + avisar()
}

class AlarmaFuego {
}

class AlarmaRobo {
}

class Sensor {
    - estado : Boolean
    - tipo : TipoSensor
}
enum TipoSensor {
    Robo
    Fuego
}
enum estado {
    Activado
    Desactivado
}

@enduml
```



### Ejercicio 8. Universidad
Se trata de modelizar un sistema que gestiona las matriculas de los estudiantes en una universidad. Una persona viene caracterizada por su dni, nombre, dirección y estado civil, y ésta puede convertirse en estudiante al darse de alta como tal en la universidad.

 Como estudiante podrá matricularse de las asignaturas que se imparten en la universidad, que tendrán un código, un nombre, un profesor responsable y un curso asignado. Una vez matriculado, el estudiante podrá recibir una beca, y en su nueva condición de becario tendrá asignado un nuevo código y se conocerá el importe de la misma; al finalizar el curso, la condición de becario acabará. 
 
 Una vez el estudiante se matricula, tanto si recibe beca como si no, deberá examinarse de las asignaturas en las que se encuentra matriculado hasta que finalice el curso y vuelva a matricularse de nuevo, o bien deje la universidad y con ello deje de ser estudiante.
 
  Además, convendrá tener una serie de aplicaciones tales como dar de alta a nuevas personas y asignaturas, llevar a cabo la matriculación de estudiantes en asignaturas, registrar las notas obtenidas por los estudiantes al examinarse de cualquier asignatura en la que están matriculados y una serie de listados tales como los alumnos matriculados en una asignatura, las asignaturas en las que se ha matriculado un alumno y el listado de notas por asignatura (actas).

~~~
@startuml universidad
'https://plantuml.com/class-diagram

'left to right direction
skinparam classAttributeIconSize 0

Persona <|-- Estudiante
Persona <|-- Profesor
Estudiante "1" -- "0..1" Beca
Profesor "1" -- "1..*" Asignatura
Estudiante "1..*" -- "1..*" Asignatura
(Estudiante, Asignatura) .. Matricula
Curso "1..*" -- "1..*" Asignatura


class Persona {
    - dni : String
    - nombre : String
    - direccion : String
    - estadocivil : String
}

class Estudiante {
    - matricula : Matricula
    + lista<Asignaturas>
}

class Profesor {
}

class Asignatura {
    - codigo : Integer
    - nombre : String
    + Lista<Estudiante>
}

class Curso {
    - nombre : String
}

class Beca {
    - importe : Float
}

class Matricula {
    -Lista<calificacion>
    - calificacion : Float
}


@enduml
~~~

**Vista previa:**
```plantuml
@startuml universidad
'https://plantuml.com/class-diagram

'left to right direction
skinparam classAttributeIconSize 0

Persona <|-- Estudiante
Persona <|-- Profesor
Estudiante "1" -- "0..1" Beca
Profesor "1" -- "1..*" Asignatura
Estudiante "1..*" -- "1..*" Asignatura
(Estudiante, Asignatura) .. Matricula
Curso "1..*" -- "1..*" Asignatura


class Persona {
    - dni : String
    - nombre : String
    - direccion : String
    - estadocivil : String
}

class Estudiante {
    - matricula : Matricula
    + lista<Asignaturas>
}

class Profesor {
}

class Asignatura {
    - codigo : Integer
    - nombre : String
    + Lista<Estudiante>
}

class Curso {
    - nombre : String
}

class Beca {
    - importe : Float
}

class Matricula {
    -Lista<calificacion>
    - calificacion : Float
}


@enduml
```