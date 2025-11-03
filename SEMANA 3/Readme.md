## hecho por Yeison Moreno Kevin Larrota Juan Zacananbui Juan Cuadros 

## Base de Datos de Cine — MySQL

## Descripción general

Este proyecto forma parte de la Actividad 
Integradora: “Del Modelo al Script – Construcción de 
Bases de Datos Reales en SQL”.
El objetivo es diseñar e implementar una base de 
datos relacional completa en MySQL, aplicando los
conceptos aprendidos sobre modelado, normalización,
integridad referencial y manipulación de datos.


El sistema representa la gestión de un cine,
permitiendo administrar películas, salas, funciones,
clientes y boletos vendidos.

## Modelo conceptual y lógico

El diseño parte del modelo entidad–relación (E-R) que representa las entidades principales del negocio y sus relaciones.

![alt text](image.png)

-Entidades principales:
-Películas: información de las películas en cartelera.
-Salas: datos de las salas de proyección.
-Funciones: combina película, sala, fecha y hora.
-Clientes: datos de los compradores de boletos.
-Boletos: registro de las compras realizadas.

Relaciones principales:

-Una película puede tener muchas funciones.
-Una sala puede proyectar muchas funciones.
-Un cliente puede comprar varios boletos.
-Una función puede tener muchos boletos vendidos.

## Construcción física en MySQL

El modelo se implementó en MySQL utilizando sentencias DDL (CREATE, ALTER) y DML (INSERT)
 para definir las tablas, restricciones e insertar datos de ejemplo.

Tablas creadas:
-peliculas
-salas
-funciones
-clientes
-boletos

Cada tabla incluye su clave primaria (PK) y claves foráneas (FK) con las acciones ON DELETE 
CASCADE y ON UPDATE CASCADE para mantener la integridad referencial.

## Carga de datos de ejemplo

Se agregaron registros de muestra para validar la estructura y relaciones:
-3 películas
-3 salas
-3 funciones
-3 clientes
-3 boletos vendidos







# Sistema de Gestión de Biblioteca

## Descripción

Este proyecto consiste en el diseño e implementación de una base de datos relacional en 
PostgreSQL para gestionar el sistema de préstamos y reservas de una biblioteca pública. El
objetivo principal es permitir el registro de usuarios, la administración de libros y
autores, y el control de préstamos y reservas de ejemplares.
La base de datos está estructurada para reflejar las reglas de negocio típicas de una
biblioteca: cada usuario puede realizar múltiples préstamos y reservas, los libros pueden
tener varios autores, y cada ejemplar pertenece a una categoría específica. Además, se han
definido restricciones de integridad referencial, claves primarias y foráneas, índices para
optimizar consultas, y vistas para facilitar el acceso a información relevante.
Este sistema está diseñado para ser escalable, seguro y fácilmente integrable con
aplicaciones web o móviles que requieran acceso a la información bibliográfica y de usuarios.


## Diseño Conceptual
El diseño conceptual de la base de datos se realizó mediante un modelo entidad-relación 
(E-R), que permite representar de forma abstracta las entidades involucradas en el sistema 
de gestión de biblioteca, sus atributos, relaciones y reglas de negocio.
Entidades principales:

- Usuario: representa a los lectores registrados en la biblioteca.
- Libro: representa los ejemplares disponibles para préstamo o reserva.
- Autor: representa a los escritores de los libros.
- Categoría: clasifica los libros por temática o género.
- Préstamo: registra los libros que han sido prestados a los usuarios.
- Reserva: registra los libros que los usuarios han solicitado reservar.

Relaciones:

- Un usuario puede realizar múltiples préstamos y reservas.
- Un libro puede tener uno o varios autores (relación N:M).
- Cada libro pertenece a una única categoría (relación 1:N).
- Un préstamo está vinculado a un usuario y a un libro.
- Una reserva está vinculada a un usuario y a un libro.
Reglas de negocio:

- No se permite duplicidad en los correos electrónicos de los usuarios.
- Un libro no puede ser reservado si ya está prestado y activo.
- Las fechas de préstamo y reserva deben ser válidas y coherentes.
- El estado de los préstamos y reservas debe estar controlado mediante valores definidos 
('activo', 'devuelto', etc.).
Este modelo conceptual fue la base para el diseño lógico y físico de la base de datos,
 asegurando la integridad referencial y la normalización de los datos.



## Construcción Física

Durante el desarrollo del modelo de base de datos, se tomaron decisiones clave para 
garantizar la integridad, escalabilidad y claridad del sistema:

1. Normalización
Se aplicaron principios de normalización hasta la tercera forma normal (3FN) para evitar 
redundancias y asegurar la consistencia de los datos. Por ejemplo:
- La relación N:M entre libros y autores se resolvió mediante una tabla intermedia
 LibroAutor.
- Las categorías se separaron en una entidad independiente para facilitar su reutilización y 
clasificación.
2. Claves primarias y foráneas
Todas las entidades cuentan con claves primarias (id_*) autoincrementales para facilitar la 
identificación única. Las relaciones entre entidades se establecieron mediante claves 
foráneas, lo que permite mantener la integridad referencial.

3. Restricciones de integridad
Se definieron restricciones como:
- UNIQUE en el correo del usuario para evitar duplicados.
- CHECK en los campos de estado (estado) para limitar los valores permitidos.
- NOT NULL en campos obligatorios como nombres y fechas.
4. Índices
Se crearon índices en campos de búsqueda frecuente como titulo de libro y correo de usuario, 
con el objetivo de mejorar el rendimiento en consultas.
5. Vistas
Se implementó una vista vista_prestamos_activos para facilitar el acceso a los préstamos 
vigentes, combinando información de usuarios y libros en una sola consulta.
6. Escalabilidad
El modelo permite agregar nuevas funcionalidades como historial de préstamos, penalizaciones
por retraso, o integración con sistemas externos sin necesidad de modificar la estructura
 base.


## Evidencia del Diagrama E-R

![alt text](image-1.png)
