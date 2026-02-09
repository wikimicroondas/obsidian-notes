### Introducción
En este documento se almacena el texto con el que posteriormente se resolverán los ejercicios propuestos por la página

`https://www.tutorialesprogramacionya.com/sqlserverya/`

### Crédito
Alejandro C. Paredes

## Ejercicio 1: Objetivos y alcances

En este apartado el autor de la página expresa su opinión acerca de Microsoft SQL Server y; motivos por los cuales hace un página dedicada a la divulgación de estos conocimientos.

Microsoft SQL Server es una extensión corporativa de SQL, principalmente enfocada a trabajar con la suite de dicha compañía.

## Ejercicio 2: Crear una tabla

En este ejercicio se introduce el concepto de tablas, aunque no habla de la importancia de las bases de datos frente a otros métodos de gestión de datos. Por ahora solo presentará los fundamentos de los sistemas gestores de bases de datos relacionados.

```SQL
 if object_id('agenda') is not null
  drop table agenda;

 create table /agenda(
  apellido varchar(30),
  nombre varchar(20),
  domicilio varchar(30),
  telefono varchar(11)
 );

 create table agenda(
  apellido varchar(30),
  nombre varchar(20),
  domicilio varchar(30),
  telefono varchar(11)
 );

 create table agenda(
  apellido varchar(30),
  nombre varchar(20),
  domicilio varchar(30),
  telefono varchar(11)
 );

 exec sp_tables @table_owner='dbo';

 exec sp_columns agenda;

 drop table agenda;

 drop table agenda;
```
