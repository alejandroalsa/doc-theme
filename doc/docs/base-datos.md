---
title: Base de Datos 
---

# Base de Datos

Toda la aplicación esta deasarollada para la el gestor de bases de datos MySQL en su version mas reciente.

## Tablas

A continuacion se desarrollan todas las tablas creadas y sus funciones:

### `users`

Esta tabla tiene como funcion almacenar todos los valores y datos personales de los usuarios como:

```sql
id INT AUTO_INCREMENT PRIMARY KEY NOT NULL
```

*  `id` Es el nombre de la columna. Se pueden usar diferentes nombres para las columnas, pero `id` es comúnmente utilizado para una columna que contiene un identificador único para cada fila en la tabla.
*  `INT` Es el tipo de datos de la columna. En este caso, `INT` significa que la columna es un número entero.
*   `AUTO_INCREMENT` Es una característica que permite que el valor de la columna se genere automáticamente en incrementos de 1 para cada nueva fila que se inserte en la tabla. Esto es útil para garantizar que cada fila tenga un valor único en la columna `id`.
*   `PRIMARY KEY` Es una restricción de la tabla que especifica que la columna `id` es la clave principal de la tabla. Una clave principal es una columna o un conjunto de columnas que se utilizan para identificar de forma única cada fila en la tabla.
*   `NOT NULL` Es otra restricción que especifica que la columna `id` no puede contener valores nulos, lo que significa que cada fila debe tener un valor para la columna `id`.

```sql
user_name VARCHAR(255) DEFAULT NULL
```

*   `user_name` Es el nombre de la columna. En este caso, `user_name` se refiere al nombre de usuario de una persona.
*   `VARCHAR(255)` Es el tipo de datos de la columna. `VARCHAR` es un tipo de datos que se utiliza para almacenar cadenas de caracteres de longitud variable. En este caso, `255` especifica la longitud máxima de la cadena que se puede almacenar en la columna.
*   `DEFAULT NULL` Es un valor predeterminado que se asigna a la columna en caso de que no se especifique un valor para ella durante la inserción de datos en la tabla. En este caso, el valor predeterminado es `NULL`, lo que significa que si no se especifica un valor para la columna `user_name`, se almacenará un valor nulo.

```sql
user_surname VARCHAR(255) DEFAULT NULL
```

*   `user_surname` Es el nombre de la columna. En este caso, `user_surname` se refiere al los apellidos del usuario.

```sql
user_phone_number VARCHAR(255) DEFAULT NULL
```

*   `user_phone_number` Es el nombre de la columna. En este caso, `user_phone_number` se refiere al telefono del usuario.

```sql
user_id_business VARCHAR(255) DEFAULT NULL
```

*   `user_id_business` Es el nombre de la columna. En este caso, `user_id_business` se refiere al numero o codigo identificador del usuario en la empresa.

```sql
registration_date_user TIMESTAMP NOT NULL DEFAULT current_timestamp() ON UPDATE current_timestamp()
```

*   `registration_date_user` Es el nombre de la columna. En este caso, `registration_date_user` se refiere a la fecha y hora en que se registró un usuario.
*   `TIMESTAMP` Es el tipo de datos de la columna. El tipo de datos TIMESTAMP se utiliza para almacenar fechas y horas.
*   `DEFAULT current_timestamp()` Es un valor predeterminado que se asigna a la columna en caso de que no se especifique un valor para ella durante la inserción de datos en la tabla. En este caso, el valor predeterminado es la fecha y hora actuales, que se generan mediante la función `current_timestamp()`.
*   `ON UPDATE current_timestamp()` Es una característica que se utiliza para actualizar automáticamente la columna "registration_date_user" a la fecha y hora actuales cada vez que se actualiza una fila en la tabla.

```sql
user_email VARCHAR(255) UNIQUE DEFAULT NULL
```

*   `user_email` Es el nombre de la columna. En este caso, `user_email` se refiere al correo electronico del usuario.
*   `UNIQUE` Es una restricción de la tabla que especifica que la columna `user_email` debe contener valores únicos, lo que significa que no puede haber más de una fila en la tabla con el mismo valor en la columna `user_email`.

```sql
user_working INT DEFAULT NULL
```

*   `user_working` Es el nombre de la columna. En este caso, `user_working` se refiere al estado laboral del usuario. Mas adelante, en el manejo de jormadas, se explicara como se trata el estado de un trabajador en su horatio laboral. El trabajador puede estar en el estado `0` o `1` siendo `0` no trabajando y `1` trabajando.

```sql
user_password VARCHAR(255) DEFAULT NULL
```

*   `user_password` Es el nombre de la columna. En este caso, `user_password` se refiere ala contraseña de inicio de sesion del usuario.

```sql
user_rol VARCHAR(255) DEFAULT NULL
```

*   `user_rol` Es el nombre de la columna. En este caso, `user_rol` se refiere al rol que tiene el empleado en la aplicacion siendo. Mas adelante, en la gestion de roles y privilegios, se explicara como se define el rol de los usuarios. El trabajador puede tener dos tipos de roles, `Usuario` pudiendo solo utilizar las funciones basicas y `Administrador` pudiendo manejar al resto de usuario y administrarlos.

```sql
accept_terms VARCHAR(255) DEFAULT NULL
```

*   `accept_terms` Es el nombre de la columna. En este caso, `accept_terms` se refiere al campo legal del usuario indicando si acepto o no los terminos.

### `records`

```sql
id INT AUTO_INCREMENT PRIMARY KEY NOT NULL
```

*  `id` Es el nombre de la columna. Se pueden usar diferentes nombres para las columnas, pero `id` es comúnmente utilizado para una columna que contiene un identificador único para cada fila en la tabla.

```sql
user_id INT NOT NULL
```

*   `user_id` Es el nombre de la columna. En este caso, se refiere al identificador único de un usuario.

```sql
entry_hour DATETIME NULL DEFAULT NULL
```

*   `entry_hour` Es el nombre de la columna. En este caso, se refiere a la hora de inicio de una jornada.
*   `DATETIME` Es el tipo de datos de la columna. `DATETIME` se utiliza para almacenar fechas y horas en un formato específico.

```sql
exit_hour DATETIME NULL DEFAULT NULL
```

*   `exit_hour` Es el nombre de la columna. En este caso, se refiere a la hora de finalizacion de una jornada.


```sql
total_hours TIME DEFAULT NULL
```

*   `total_hours` Es el nombre de la columna. En este caso, se refiere al número total de horas trabajadas en un registro.
*   `TIME` Es el tipo de datos de la columna. `TIME` se utiliza para almacenar valores de tiempo en formato `horas: minutos: segundos`.

```sql
total_seconds INT(255) DEFAULT NULL
```

*   `total_seconds` Es el nombre de la columna. En este caso, se refiere al número total de segundos trabajados en un registro. Mas adelante se explicara el proceso para calcular los segundos de una jornada.

```sql
total_remuneration DECIMAL(5,2) DEFAULT NULL
```

*   `total_remuneration` Es el nombre de la columna. En este caso, se refiere a la cantidad total de remuneración recibida por un trabajador.
*   `DECIMAL` Es el tipo de datos de la columna. `DECIMAL` se utiliza para almacenar valores numéricos con decimales.
*   `(5,2)` Define la precisión y la escala de la columna. En este caso, se establece en `5` y `2`, respectivamente. La precisión se refiere al número total de dígitos que puede contener el valor numérico, mientras que la escala se refiere al número de dígitos decimales que se permiten.

```sql
FOREIGN KEY (user_id) REFERENCES users(id)
```

*   `FOREIGN KEY` Es una restricción que se utiliza para mantener la integridad referencial entre dos tablas en una base de datos. En este caso, se está creando una clave foránea en una tabla para hacer referencia a una columna en otra tabla.
*   `(user_id)` Es el nombre de la columna en la tabla actual que se utilizará como clave foránea para hacer referencia a otra tabla.
*   `REFERENCES` Es una palabra clave que indica que se está haciendo referencia a otra tabla.
*   `users` Es el nombre de la tabla a la que se está haciendo referencia.
*   `(id)` Es el nombre de la columna en la tabla "users" que se utilizará como clave primaria para establecer la relación entre las dos tablas. En otras palabras, "user_id" en la tabla actual debe coincidir con "id" en la tabla "users".

### `remuneration`

```sql
id INT AUTO_INCREMENT PRIMARY KEY NOT NULL,
```

*   `id` Es el nombre de la columna.

```sql
user_id INT NOT NULL
```

*   `user_id` Es el nombre de la columna. En este caso, se refiere al identificador único de un usuario.

```sql
hourly_pay DECIMAL(5,2) DEFAULT NULL
```

*   `hourly_pay` Es el nombre de la columna.

```sql
total_remuneration DECIMAL(5,5) DEFAULT NULL
```

*   `total_remuneration` Es el nombre de la columna.

```sql
FOREIGN KEY (user_id) REFERENCES users(id)
```

*   `FOREIGN KEY` Es una restricción que se utiliza para mantener la integridad referencial entre dos tablas en una base de datos. En este caso, se está creando una clave foránea en una tabla para hacer referencia a una columna en otra tabla.
*   `(user_id)` Es el nombre de la columna en la tabla actual que se utilizará como clave foránea para hacer referencia a otra tabla.
*   `REFERENCES` Es una palabra clave que indica que se está haciendo referencia a otra tabla.
*   `users` Es el nombre de la tabla a la que se está haciendo referencia.
*   `(id)` Es el nombre de la columna en la tabla "users" que se utilizará como clave primaria para establecer la relación entre las dos tablas. En otras palabras, "user_id" en la tabla actual debe coincidir con "id" en la tabla "users".

## Codigo

```sql
DROP DATABASE IF EXISTS time_control;

CREATE DATABASE  time_control;

USE  time_control;

CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY NOT NULL,
    user_name VARCHAR(255) DEFAULT NULL,
    user_surname VARCHAR(255) DEFAULT NULL,
    user_phone_number VARCHAR(255) DEFAULT NULL,
    user_id_business VARCHAR(255) DEFAULT NULL,
    registration_date_user TIMESTAMP NOT NULL DEFAULT current_timestamp() ON UPDATE current_timestamp(),
    user_email VARCHAR(255) UNIQUE DEFAULT NULL,
    user_working INT DEFAULT NULL,
    user_password VARCHAR(255) DEFAULT NULL,
    user_rol VARCHAR(255) DEFAULT NULL,
    accept_terms VARCHAR(255) DEFAULT NULL
);

CREATE TABLE records (
    id INT AUTO_INCREMENT PRIMARY KEY NOT NULL,
    user_id INT NOT NULL,
    entry_hour DATETIME NULL DEFAULT NULL,
    exit_hour DATETIME NULL DEFAULT NULL,
    total_hours TIME DEFAULT NULL,
    total_seconds INT(255) DEFAULT NULL,
    total_remuneration DECIMAL(5,2) DEFAULT NULL,

    FOREIGN KEY (user_id) REFERENCES users(id)
);

CREATE TABLE remuneration (
    id INT AUTO_INCREMENT PRIMARY KEY NOT NULL,
    user_id INT NOT NULL,
    hourly_pay DECIMAL(5,2) DEFAULT NULL,
    total_remuneration DECIMAL(5,5) DEFAULT NULL,

    FOREIGN KEY (user_id) REFERENCES users(id)
);
```
