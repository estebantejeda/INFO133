### 1. SELECT vs. SELECT DISTINCT
 
1.1 Mostrar en qué ciudades viven los clientes.

~~~mysql
SELECT city 
FROM customers;
~~~

1.2 Misma pregunta pero de evitando mostrar varias veces la misma ciudad.

~~~mysql
SELECT DISTINCT city 
FROM customers;
~~~

### 2. ORDER BY 

2.1 Mostrar la lista de los productos ordenados por el stock disponible del más grande al más pequeño.

~~~mysql
SELECT * 
FROM products 
ORDER BY quantityInStock DESC;
~~~

2.2 Mostrar los 3 últimos pedidos (orders)

~~~mysql
SELECT * 
FROM orders 
ORDER BY orderDate DESC 
LIMIT 3;
~~~

### 3. WHERE

3.1 Mostrar los productos que corresponden a una linea de productos que contiene la palabra "Cars" en su nombre.

~~~mysql
SELECT * 
FROM productlines 
WHERE productLine 
LIKE '%cars%';
~~~

3.2 Mostrar los productos que no son de tipo "Planes" y "Motorcycles".

~~~mysql
SELECT * 
FROM products 
WHERE productLine 
NOT IN ('Planes','Motorcycles');
~~~

### 4. JOIN

4.1 Mostrar los nombres y apellidos de las personas que compraron productos de tipo "Planes".

~~~mysql
SELECT DISTINCT contactLastName, contactFirstName
FROM customers c 
INNER JOIN orders o 
ON c.customerNumber = o.customerNumber 
INNER JOIN orderdetails od 
ON o.orderNumber = od.orderNumber 
INNER JOIN products p 
ON od.productCode = p.productCode 
WHERE productLine='Planes';
~~~

4.2 Mostrar los nombres y appellidos de las personas que NO compraron productos de tipo "Planes".

~~~mysql
SELECT DISTINCT contactLastName, contactFirstName 
FROM customers c 
INNER JOIN orders o 
ON c.customerNumber = o.customerNumber 
INNER JOIN orderdetails od 
ON o.orderNumber = od.orderNumber 
INNER JOIN products p 
ON od.productCode = p.productCode 
WHERE productLine 
NOT IN ('Planes');
~~~

### 5. GROUP BY

5.1 Mostrar cuántos productos existen según linea de productos.

~~~mysql
SELECT productLine, COUNT(*)  AS Cantidad
FROM products 
GROUP BY productLine;
~~~

5.2 Mostrar cuáles son los clientes que realizarón más de 3 pedidos (orders)

~~~mysql
SELECT customerName, COUNT(*) AS Pedidos 
FROM customers 
INNER JOIN orders 
USING (customerNumber) 
GROUP BY customerName 
HAVING pedidos > 3;
~~~

### 6. Subconsultas

6.1 Mostrar qué día se vendió el producto más carro del catalogo.

~~~mysql
~~~

6.2 Mostrar qué empleado realizó más volumen de negocio que los otros empleados.

~~~mysql
~~~

### 7. Consultas adicionales:

7.1 Mostrar el numeros de empleados por oficinas

~~~mysql
SELECT officeCode AS Departamento, COUNT(employeeNumber) AS Empleados
FROM employees 
GROUP BY officeCode;
~~~

7.2 Mostrar cómo evoluciona el volumen de negocio por mes

~~~mysql
~~~

7.3. Mostrar el volumen de negocio agrupado según el producto

~~~mysql
~~~

7.4 Mostrar qué productos nunca se vendieron

~~~mysql
~~~

7.5 Mostrar los productos que contienen las palabras "red", "blue" y "amarillo" en su descripción.

~~~mysql
SELECT productName, productDescription 
FROM products 
WHERE productDescription 
LIKE '%red%' 
OR productDescription 
LIKE '%blue%' 
OR productDescription 
LIKE '%yellow%';
~~~

7.6 Mostrar el volumen de negocio realizado agrupado por los productos que contienen la palabra "red" y los productos que contienen la palabra "azul".

~~~mysql
~~~