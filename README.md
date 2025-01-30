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

<details>
    <br>
    <summary>Apartado 3</summary>
    
Query:

```bash
 SELECT * FROM empresasfct ORDER BY fechacontacto DESC;
```
Al realizar este consulta se mostrarán los datos ordenados de la manera especificada:

![ap3](https://github.com/user-attachments/assets/b90d23b2-f43c-47a0-be74-f2b565f31095)

</details>

<details>
    <br>
    <summary>Apartado 4</summary>
    
Query:

```bash
 SELECT name AS Nombre, city AS Ciudad, 
       commercial_company_name AS Nombre_Comercial_Empresa
FROM res_partner 
WHERE is_company = FALSE 
AND city = 'Tracy'
ORDER BY commercial_company_name ASC;
```
Al realizar este consulta se mostrarán los datos deseados de la tabla res_partner (tabla por defecto de Odoo) ordenados por el nombre de la empresa y cuya ciudad sea Tracy:

![ap4b](https://github.com/user-attachments/assets/bda33f0e-4ca1-41ca-9a13-036462540392)

</details>

<details>
    <br>
    <summary>Apartado 5</summary>
    
Query:

```bash
SELECT DISTINCT
    invoice_partner_display_name AS Nombre_Empresa,
    name AS Numero_Factura,
    invoice_date AS Fecha_Factura,
    amount_untaxed AS Total_Factura_Sin_Impuestos
FROM account_move
WHERE move_type = 'in_refund'
ORDER BY invoice_date DESC;
```
Al realizar este consulta se mostrarán las facturas con reembolso activo ("in_refund") de la tabla account_move con los campos especificados ordenadas por la fecha de factura:

![ap5b](https://github.com/user-attachments/assets/7673bb3a-2d13-4762-9c69-77d38c1a5d89)

</details>

<details>
    <br>
    <summary>Apartado 6</summary>
    
Query:

```bash
SELECT 
    invoice_partner_display_name AS Nombre_Empresa,
    COUNT(DISTINCT name) AS Numero_Facturas,
    SUM(DISTINCT amount_untaxed) AS Total_Facturado_Sin_Impuestos
FROM account_move 
WHERE move_type = 'out_invoice'  
AND state = 'posted'
GROUP BY invoice_partner_display_name
HAVING COUNT(DISTINCT name) > 2;
```
Al realizar este consulta se mostrarán las empresas clientes que tienen más de 2 facturas de venta emitidas, con el numero de facturas y la suma de lo facturado sin impuestos, agrupado por empresa:

![ap6b](https://github.com/user-attachments/assets/a66f2317-284a-48a9-8b9d-6a13b66e4ee6)

</details>

<details>
    <br>
    <summary>Apartado 7</summary>
    
Query:

```bash
UPDATE res_partner
SET email = REPLACE(email, '@bilbao.example.com', '@bilbao.bizkaia.eus')
WHERE email LIKE '%@bilbao.example.com';
```
Al realizar esta consulta se cambian los dominios por el seleccionado, manteniendo el nombre de antes del dominio tal y como estaba.

![ap7](https://github.com/user-attachments/assets/9d92b5bc-c24b-4dc7-a21a-3b173113ad3d)

</details>
