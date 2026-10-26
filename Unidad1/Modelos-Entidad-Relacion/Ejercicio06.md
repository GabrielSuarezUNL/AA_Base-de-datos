# Ejercicio 6: Tienda Informática

## Enunciado

Se desea crear una aplicación para la gestión de una tienda informática. La tienda dispone de una serie de productos que se venden a los clientes. De cada producto informático se desea guardar el código, descripción, precio y número de existencias. De cada cliente se desea guardar el código, nombre, apellidos, dirección y número telefónico. Un cliente puede comprar varios productos en la tienda y un mismo producto puede ser comprado por varios clientes. Cada vez que se compre un artículo quedará registrada la compra en la base de datos junto con la fecha en la que se compró el artículo. La tienda tiene contactos con varios proveedores que son los que suministran los productos. Un mismo producto puede ser suministrado por varios proveedores. De cada proveedor se desea guardar el código, nombres, apellidos, dirección, provincia y número de teléfono.

## Diagrama Entidad-Relación

![Diagrama Entidad-Relación del ejercicio 06](imagenes/ejercicio06.png)

---
## Modelo Relacional 
![Modelo Relacional](<modelo relacional/MODELO RELACIONAL 6.jpg>)

---
## Codigo MySQL
```sql

Create Table Cliente (
    codigo    Int Primary Key,
    nombre    Varchar(60) Not Null,
    apellidos Varchar(80) Not Null,
    direccion Varchar(150),
    telefono  Varchar(15)
);
 
Create Table Producto (
    codigo      Int Primary Key,
    descripcion Varchar(200) Not Null,
    precio      Decimal(10,2) Not Null,
    existencias Int Not Null
);
 
Create Table Compra (
    id_compra       Int Primary Key,
    codigo_cliente  Int  Not Null,
    codigo_producto Int  Not Null,
    fecha           Date Not Null,
    Foreign Key (codigo_cliente)  References Cliente (codigo),
    Foreign Key (codigo_producto) References Producto (codigo)
);
 
Create Table Proveedor (
    codigo    Int Primary Key,
    nombres   Varchar(60) Not Null,
    apellidos Varchar(80) Not Null,
    direccion Varchar(150),
    provincia Varchar(60),
    telefono  Varchar(15)
);
 
Create Table Suministra (
    codigo_producto  Int Not Null,
    codigo_proveedor Int Not Null,
    Primary Key (codigo_producto, codigo_proveedor),
    Foreign Key (codigo_producto)  References Producto (codigo),
    Foreign Key (codigo_proveedor) References Proveedor (codigo)
);


```

---

[Volver al índice de Modelos Entidad-Relación](README.md) · [Volver a Unidad 1](../README.md)
