# sistema de almacenamiento  de informacion 

## Necesidad
Se requiere  desarrollar un sistema que permita almacenar informacion sobre categorias de carros, autos, persona y la relacion entre autos y persona. se necesitan almacenar los siguientes atributos:

- Categoría de Carros: 4 atributos
- Autos: 6 atributos
- Personas: 6 atributos
- Autos_Persona: 4 atributos

## Requerimientos Funcionales
### RF 1 : Categorias de carros
 En las categorias de carros se nesecitan almacenar el suguiente conjunto de atributos:
- id
- categoria
- tipo de vehiculo
- descripcion

### RF 2 : Autos
 En las categorias de carros se nesecitan almacenar el suguiente conjunto de atributos:
- id
- marca
- precio
- cilindraje
- id_categoria_carros(referencia a categorias carros)
- descripcion 

Referencias:
- se requiere tener informacion alamacenada en la entidad Categoría_de_Carros

### RF 3 : Personas
 En las categorias de carros se nesecitan almacenar el suguiente conjunto de atributos:
- id
- nombre
- telefono
- direccion
- documento


### RF 4 : Auto_Persona
 En las categorias de carros se nesecitan almacenar el suguiente conjunto de atributos:
- id
- id_Autos(referencia de autos)
- id_Persona(referencia a persona)
- descripcion

 Referencias:
- se requiere tener informacion almacenada en las entidades autos y persona.

## Diseño de la Base de Datos
### Categorías de Carros

| id | categoría        | tipo_vehículo | descripción               |
|----|------------------|---------------|---------------------------|
| 1  | alto cilindraje  | deportivo     | comodo y velocidad        |
| 2  | alto cilindraje  | trocha        | ideal para carreteras feas|
| 3  | bajo cilindraje  | deportivo     | comodo y menos velocidad  |
 
- id: Identificador único de la categoría de carro.
- categoría: Nombre de la categoría de carro.
- tipo_vehículo: Tipo de vehículo al que pertenece la categoría.
- descripción: Breve descripción de la categoría de carro.

### Autos

| id | marca   | precio   | cilindraje | id_categorias_de_carros | descripción |
|----|---------|----------|------------|-------------------------|-------------|
| 1  | ferrari | 100.000  | 5000       | 1                       | velociad    |
| 2  | mazda   | 50.000   | 1000       | 2                       | comodadida  |
| 3  | porsche |  75.000  | 4000       | 3                       | velocidad   |

- id: Identificador único del auto.
- marca: Marca del auto.
- garantía: Duración de la garantía del auto en años.
- cilindraje: Cilindraje del motor del auto.
- id_categorias_de_carros: Identificador de la categoría de carro a la que pertenece el auto.
- descripción: Breve descripción del auto.


### Personas

| id | nombre   | apellido | teléfono  | dirección      | documento |
|----|----------|----------|-----------|----------------|-----------|
| 1  | Yeison   | Scarpeta | 3205788679| cr 5#6-30      | 1007258220|
| 2  | Sebastian| Andres   | 3585885588| cr 7#6-40      | 1008458221|
| 3  | sergio   | Calderon | 8585858585| cr 8#6-25      | 1005495564|

- id: Identificador único de la persona.
- nombre: Nombre de la persona.
- apellido: Apellido de la persona.
- teléfono: Número de teléfono de la persona.
- dirección: Dirección de residencia de la persona.
- documento: Número de documento de identidad de la persona.

### Autos_Persona

| id | id_autos | id_persona | descripción |
|----|----------|------------|-------------|
| 1  | 1        | 1          | idal        |
| 2  | 2        | 2          | idal        |
| 3  | 3        | 3          | idal        |

- id: Identificador único de la relación entre auto y persona.
- id_autos: Identificador del auto relacionado.
- id_persona: Identificador de la persona relacionada.
- descripción: Breve descripción de la relación entre el auto y la persona.


### Base de datos script

```sql
    DROP DATABASE IF EXISTS parcial;

    CREATE DATABASE parcial;

    USE parcial;

    CREATE table categorias_de_carros (
        id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
        categoria VARCHAR1(150) NOT NULL UNIQUE,
        tipo_vehiculo VARCHAR(150) NOT NULL,
        descripción VARCHAR(150) NOT NULL
        
    ); 

    CREATE table autos (
        id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
        marca VARCHAR(150) NOT NULL,
        precio int NOT NULL,
        cilindraje INT NOT NULL,
        FOREIGN KEY (id_categorias_de_carros) REFERENCES categorias_de_carros(id),
        descripciónVARCHAR(150) NOT NULL
    ); 

    CREATE table persona (
        id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
        nombre VARCHAR1(150) NOT NULL UNIQUE,
        apellido VARCHAR(150) NOT NULL,
        telefono INT NOT NULL,
        dirección VARCHAR(150) NOT NULL,
        documento INT NOT NULL
    ); 

    CREATE table Autos_persona  (
        id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
        FOREIGN KEY (id_autos) REFERENCES autos(id),
        FOREIGN KEY (id_persona) REFERENCES persona(id),
        descripción VARCHAR(150) NOT NULL
        
    ); 
```


