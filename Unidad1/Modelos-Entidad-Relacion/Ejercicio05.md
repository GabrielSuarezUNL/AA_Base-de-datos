# Ejercicio 5: Empresa Discográfica

## Enunciado

Una empresa discográfica necesita modelar los datos sobre sus diferentes recursos según las siguientes características:

- **Manager:** de cada mánager se almacena un identificador de manager y su nombre. Un manager representa a una serie de artistas.
- **Artista:** un artista es representado por un manager. De los artistas se almacena su nombre completo (usando un único atributo) y su NIF.
- **Evento de promoción:** los artistas participan en eventos de promoción para dar a conocer sus trabajos. En un evento de promoción pueden participar varios artistas. De un evento se almacena un identificador único, la fecha de celebración y el número de asistentes.

## Diagrama Entidad-Relación

![Diagrama Entidad-Relación del ejercicio 05](imagenes/ejercicio05.png)

---
## Modelo Relacional 
![Modelo Relacional](<modelo relacional/MODELO RELACIONAL 5.jpg>)

---
## Codigo MySQL
```sql

Create Table Manager (
    identificador Int Primary Key,
    nombre        Varchar(100) Not Null
);
 
Create Table Artista (
    NIF        Varchar(9) Primary Key,
    nombre     Varchar(120) Not Null,
    id_manager Int Not Null,
    Foreign Key (id_manager) References Manager (identificador)
);
 
Create Table Evento_promocion (
    identificador     Int Primary Key,
    fecha_celebracion Date Not Null,
    numero_asistentes Int  Not Null
);
 
Create Table Participa (
    NIF       Varchar(9) Not Null,
    id_evento Int Not Null,
    Primary Key (NIF, id_evento),
    Foreign Key (NIF)       References Artista (NIF),
    Foreign Key (id_evento) References Evento_promocion (identificador)
);
 


```

---
[Volver al índice de Modelos Entidad-Relación](README.md) · [Volver a Unidad 1](../README.md)
