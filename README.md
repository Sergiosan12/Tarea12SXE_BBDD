# Tarea12SXE_BBDD

<details>
    <br>
    <summary>Configuración inicial</summary>
    
En primer lugar se crea la base de datos con la demo activa y después se instalan las aplicaciones de "Contacto" y "Facturación" y saldrán datos aleatorios de demostración.

![contactcosdemo](https://github.com/user-attachments/assets/26671709-86bf-4b3c-85fb-115c0948cb80)

Para realizar las consultas se accede a Pg_admin y se hacen en la base de datos seleccionada.

![querysbbddd](https://github.com/user-attachments/assets/b2791988-6709-44b5-86d3-31acfa9e1bd0)

</details>

<details>
    <br>
    <summary>Apartado 1</summary>
    
Query:

```bash
CREATE TABLE EmpresasFCT (
    idEmpresa SERIAL PRIMARY KEY,
    nombre VARCHAR(40),
    quiereAlumnos BOOLEAN,
    numAlumnos INTEGER,
    fechaContacto DATE
);
```

La consulta salió correcta y se puede ver que se creó correctamente al refrescar las tablas:

![ap1querycorrecta](https://github.com/user-attachments/assets/85ed7398-41d9-4b59-8bd3-192949f5218f)

</details>

<details>
    <br>
    <summary>Apartado 2</summary>
    
Query:

```bash
INSERT INTO EmpresasFCT (nombre, quiereAlumnos, numAlumnos, fechaContacto) VALUES
('Imatia', TRUE, 3, '2024-01-15'),
('Bahia', FALSE, NULL, '2024-02-10'),
('Marine Instruments', TRUE, 5, '2024-03-05'),
('Optare', TRUE, 2, '2024-01-28'),
('Zara', FALSE, NULL, '2024-02-20');
```

Se insertaron los datos correctamente:

![ap2](https://github.com/user-attachments/assets/c897e1fb-5e07-4503-9609-7ec18d51db94)

</details>
