# Ejemplo 3: Clínica Médica

## Enunciado

Los pacientes solicitan citas; cada cita la atiende un médico a un paciente en fecha, hora y consultorio. De algunas citas se genera una receta que incluye medicamentos con dosis y duración. Cada médico pertenece a una especialidad.

## Diagrama Entidad-Relación

![Diagrama Entidad-Relación del ejercicio 03](imagenes/ejercicio03.png)

---
## Modelo Relacional 
![Modelo Relacional](<modelo relacional/MODELO RELACIONAL 3.jpg>)

---
---

## Codigo MySQL
```sql

Create Table Especialidad (
    id_especialidad Int Primary Key,
    nombre          Varchar(80) Not Null
);
 
Create Table Medico (
    id_medico       Int Primary Key,
    nombre          Varchar(100) Not Null,
    id_especialidad Int Not Null,
    Foreign Key (id_especialidad) References Especialidad (id_especialidad)
);
 
Create Table Paciente (
    id_paciente Int Primary Key,
    nombre      Varchar(100) Not Null
);
 
Create Table Cita (
    id_cita     Int Primary Key,
    fecha       Date Not Null,
    hora        Time Not Null,
    consultorio Varchar(20) Not Null,
    id_paciente Int Not Null,
    id_medico   Int Not Null,
    Foreign Key (id_paciente) References Paciente (id_paciente),
    Foreign Key (id_medico)   References Medico (id_medico)
);
 
Create Table Receta (
    id_receta Int Primary Key,
    dosis     Varchar(100) Not Null,
    duracion  Varchar(50)  Not Null,
    id_cita   Int Not Null Unique,
    Foreign Key (id_cita) References Cita (id_cita)
);
 
Create Table Medicamento (
    id_medicamento Int Primary Key,
    nombre         Varchar(100) Not Null
);
 
Create Table Incluye (
    id_receta      Int Not Null,
    id_medicamento Int Not Null,
    Primary Key (id_receta, id_medicamento),
    Foreign Key (id_receta)      References Receta (id_receta),
    Foreign Key (id_medicamento) References Medicamento (id_medicamento)
);



```

---

[Volver al índice de Modelos Entidad-Relación](README.md) · [Volver a Unidad 1](../README.md)
