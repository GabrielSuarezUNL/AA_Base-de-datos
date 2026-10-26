# Ejemplo 4: Sistema de Aerolínea

## Enunciado

Una aerolínea opera vuelos (cada uno con número, fecha, origen y destino), cada vuelo lo realiza un avión. Los pasajeros realizan reservas para un vuelo específico, indicando asiento y tarifa pagada en el momento de la reserva.

## Diagrama Entidad-Relación

![Diagrama Entidad-Relación del ejercicio 04](imagenes/ejercicio04.png)

---
## Modelo Relacional 
![Modelo Relacional](<modelo relacional/MODELO RELACIONAL 4.jpg>)

---

## Codigo MySQL
```sql

Create Table Avion (
    id_avion Int Primary Key
);
 
Create Table Vuelo (
    numero   Varchar(10) Primary Key,
    fecha    Date Not Null,
    origen   Varchar(60) Not Null,
    destino  Varchar(60) Not Null,
    id_avion Int Not Null,
    Foreign Key (id_avion) References Avion (id_avion)
);
 
Create Table Pasajero (
    id_pasajero Int Primary Key,
    nombre      Varchar(100) Not Null
);
 
Create Table Reserva (
    id_pasajero Int Not Null,
    numero      Varchar(10) Not Null,
    asiento     Varchar(5)  Not Null,
    tarifa      Decimal(8,2) Not Null,
    Primary Key (id_pasajero, numero),
    Foreign Key (id_pasajero) References Pasajero (id_pasajero),
    Foreign Key (numero)      References Vuelo (numero)
);

```
---

[Volver al índice de Modelos Entidad-Relación](README.md) · [Volver a Unidad 1](../README.md)
