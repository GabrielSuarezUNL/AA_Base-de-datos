# Ejemplo 2: Pedidos de Restaurante

## Enunciado

Los clientes realizan pedidos que contienen varios platos con distinta cantidad. Los platos se agrupan en categorías. Cada pedido lo atiende un único mesero. El precio del plato debe registrarse tal como estaba al momento del pedido, aunque luego cambie.

## Diagrama Entidad-Relación

![Diagrama Entidad-Relación del ejercicio 02](imagenes/ejercicio02.png)

---
## Modelo Relacional 
![Modelo Relacional](<modelo relacional/MODELO RELACIONAL 2.jpg>)

---
## Codigo MySQL
```sql
Create Table Cliente (
    id_cliente Int Primary Key,
    nombre     Varchar(100) Not Null
);
 
Create Table Mesero (
    id_mesero Int Primary Key,
    nombre    Varchar(100) Not Null
);
 
Create Table Pedido (
    id_pedido  Int Primary Key,
    id_cliente Int Not Null,
    id_mesero  Int Not Null,
    Foreign Key (id_cliente) References Cliente (id_cliente),
    Foreign Key (id_mesero)  References Mesero (id_mesero)
);
 
Create Table Categoria (
    id_categoria Int Primary Key,
    nombre       Varchar(60) Not Null
);
 
Create Table Plato (
    id_plato     Int Primary Key,
    nombre       Varchar(100) Not Null,
    precio       Decimal(8,2) Not Null,
    id_categoria Int Not Null,
    Foreign Key (id_categoria) References Categoria (id_categoria)
);
 
Create Table Detalle_pedido (
    id_pedido       Int Not Null,
    id_plato        Int Not Null,
    cantidad        Int Not Null,
    precio_unitario Decimal(8,2) Not Null,
    Primary Key (id_pedido, id_plato),
    Foreign Key (id_pedido) References Pedido (id_pedido),
    Foreign Key (id_plato)  References Plato (id_plato)
);

 
```

---
[Volver al índice de Modelos Entidad-Relación](README.md) · [Volver a Unidad 1](../README.md)
