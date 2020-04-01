# Gabinete de abogados.

* Se quiere diseñar una base de datos relacional para almacenar información sobre los asuntos que lleva un gabinete de abogados. Cada asunto tiene un número de expediente que lo identifica, y corresponde a un solo clientve. Del asunto se debe almacenar el período (fecha de inicio y fecha de archivo o finalización), su estado (en trámite, archivado, etc.), así como los datos personales del cliente al que  ertenece (DNI, nombre, dirección, etc.). Algunos asuntos son llevados por uno o varios procuradores, de los que nos interesa también los datos personales.

## Justificación.

Se realizará una base de datos para así poder llevar a cabo un control del número de expedientes que se van a realizar, así como se podrá organizar por fecha de archivo, numero de folio, etc.

## DATABASE.

```sql
    CREATE DATABASE IF NOT EXISTS Procurador;    
 ```

 ## Tablas.

 ```sql
    CREATE TABLE IF NOT EXISTS procurador (
    DNI int,
    Direccion varchar(20),
    Nombre varchar(20),
    Apellido varchar(20),
    PRIMARY KEY (id_procurador),
    FOREIGN KEY (apellido) REFERENCES apellido(id_apellido)
    )Engine=InnoDB default charset=latin1;

  CREATE TABLE IF NOT EXISTS asuntos (
    num_expediente int,
    Estado varchar(20),
    num_archivo int,
    nombre_archivo varchar (20),
    periodo int,
    fecha_inicio int,
    fecha_fin int,
    PRIMARY KEY (id_asuntos)
    )Engine=InnoDB default charset=latin1;

  Create table if not exists cliente(
    apellido varchar (20),
    DNI int,
    direccion varchar(20),
    nombre varchar(20)
    )Engine=InnoDB default charset=latin1;0
```

## Diccionario de datos.

* Procurador.
 
 |        Campo        |          Dominio       |  Tipo de dato  |
 |---------------------|------------------------|----------------|
  |      Dirección      |Direccion del procurador|    varchar     |
 |       Nombre        |Nombre completo del procurador| Varchar  |
 |  Apellido   |    Apellido materno y paterno del procurador   |  varchar  |
 

* Asuntos.

|   Campo   |   Dominio   |   Tipo de dato   |
|-----------|-------------|------------------|
| num_expediente  | Número de folio del expediente  |  int  |
|  Estado  |  Nombre del estado del archivo  | varchar  |
| num_archivo  |  Numero del folio del archivo  |  int  |
| nombre_archivo  |  Nombre que le asignaron al archivo  |  varchar  |
| periodo  |  Periodo en el que se hizo el tramite  |  int  |
| fecha_inicio  |  Fecha de inicio del tramite  |  int  |
| fecha_fin |  fecha en que se termino el tramite  |  int  |


* Cliente.

|  Campo  |  Dominio  |  Tipo de dato  |
|---------|-----------|----------------|
| apellido  | ambos apellidos del cliente  |  varchar  |
| DNI  |  Identificación vigente del cliente  |  int  |
| direccion |  Direccion completa del cliente  |  varchar  |
| nombre  |  nombre completo del cliente  |  varchar  |


