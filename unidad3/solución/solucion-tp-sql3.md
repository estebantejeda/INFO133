### 2. Consultas

1. Mostrar el 'firstname' y 'lastname' de los clientes activos
 (_active_).
 
~~~mysql
SELECT first_name, last_name 
FROM customer 
WHERE active=true;
~~~
 
2. Contar el número de clientes activos por paises

~~~mysql
SELECT country, COUNT(*) 
FROM customer 
INNER JOIN address 
USING (address_id) 
INNER JOIN city 
USING (city_id) 
INNER JOIN country 
USING (country_id) 
WHERE active=true 
GROUP BY country;
~~~

3. Mostrar los paises dónde hay al menos 10 clientes activos, ordenados del número más grande al más pequeño.

~~~mysql
SELECT country, COUNT(*) AS Active_Users 
FROM customer 
INNER JOIN address 
USING (address_id) 
INNER JOIN city 
USING (city_id) 
INNER JOIN country 
USING (country_id) 
WHERE active=true 
GROUP BY country 
HAVING Active_Users>=10
ORDER BY Active_Users DESC;
~~~

4. Mostrar los titulos y descripción de peliculas que contienen la palabra "dog" en du descripción.

~~~mysql
SELECT title, description 
FROM film 
WHERE description 
LIKE '%dog%';
~~~

5. Mostrar los titulos y descripción de peliculas que más fueron arrendadas, ordenadas de del número más grande al más pequeño.

~~~mysql
SELECT title, description, COUNT(*) AS arriendos 
FROM inventory 
INNER JOIN rental 
USING (inventory_id) 
INNER JOIN film 
USING (film_id) 
GROUP BY film_id 
ORDER BY arriendos DESC;
~~~

6. Mostrar las peliculas que nunca fueron arrendadas entre dos fechas.

~~~mysql
~~~

7. Mostrar el volumen de negocio (ver tabla Payment) asociado a cada pelicula entre dos fechas, ordenado del volumen de negocio más grande al más pequeño.

~~~mysql
~~~

8. Mostrar título de la pelicula que generó más volumen de negocio.

~~~mysql
SELECT title, SUM(amount) AS Total 
FROM payment 
INNER JOIN rental 
USING (rental_id) 
INNER JOIN inventory 
USING (inventory_id) 
INNER JOIN film 
USING(film_id) 
GROUP BY film_id 
ORDER BY Total DESC 
LIMIT 1;
~~~

9. Mostrar los títulos de pelicula que generaron más de cierto valor de volumen de negocio.

~~~mysql
SELECT title, SUM(amount) AS Total 
FROM payment 
INNER JOIN rental 
USING (rental_id)
INNER JOIN inventory 
USING (inventory_id) 
INNER JOIN film 
USING(film_id) 
GROUP BY film_id 
HAVING Total > 200;
~~~

10. Contar cuántos Staff distintos han arrendados la pelicula que generó más volumen de negocio.

~~~mysql
~~~

11. Mostrar la pelicula más arrendada (titulo) por un Staff particular.

~~~mysql
~~~

12. Mostrar la pelicula más arrendada (titulo) por cada uno de los miembros del Staff.

~~~mysql
~~~

13. Mostrar la evolución del volumen de negocio mensual de una tienda dada

~~~mysql
~~~

14. ¿Cuáles son los actores que más generan volumen de negocio?

~~~mysql
~~~

15. ¿Cuáles son los actores que jugaron más en pelicula de tipo "Sci-Fi"?

~~~mysql
~~~

16. ¿Cuáles son los actores que nunca jugaron en pelicula de tipo "Sci-Fi"?

~~~mysql
~~~

17. ¿Cuáles son los actores que jugaron en peliculas con 'Russell Close'?

~~~mysql
~~~

18. Contar el número de peliculas promedio por actores

~~~mysql
~~~

19. Mostrar la pelicula más larga (_length_)

~~~mysql
~~~

20. Mostrar las tres categorias de pelicula favoritas de un cliente dado

~~~mysql
~~~

21. Mostrar la categoría de pelicula favorita de cada cliente (firstname y lastname).

~~~mysql
~~~

22. Mostrar cuál categoría de pelicula no es la favorita de nadie.

~~~mysql
~~~

23. Mostrar cuál categoría genera al menos 3 arriendos por semana en promedio.

~~~mysql
~~~