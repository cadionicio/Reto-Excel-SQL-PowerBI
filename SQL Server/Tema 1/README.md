# Manejo de tipos de datos

| **Función**       | **Descripción**                                                                                   | **Sintaxis**                                      | **Ejemplo**                                                   |
|-------------------|---------------------------------------------------------------------------------------------------|--------------------------------------------------|---------------------------------------------------------------|
| `CAST()`          | Convierte un valor de un tipo de dato a otro.                                                      | `CAST(valor AS tipo_dato)`                       | `CAST('100' AS INT)`                                           |
| `CONVERT()`       | Similar a `CAST()`, convierte un valor a otro tipo de dato y ofrece más control sobre el formato.   | `CONVERT(tipo_dato, valor [, formato])`          | `CONVERT(VARCHAR, fecha, 103)`                                 |
| `COALESCE()`      | Devuelve el primer valor no nulo de la lista de valores.                                           | `COALESCE(valor1, valor2, ...)`                  | `COALESCE(NULL, 'texto', 'default')`                           |
| `ISNULL()`        | Reemplaza valores nulos por un valor predeterminado.                                               | `ISNULL(valor, valor_predeterminado)`            | `ISNULL(NULL, 0)`                                              |
| `NULLIF()`        | Devuelve `NULL` si los dos valores dados son iguales, de lo contrario devuelve el primer valor.    | `NULLIF(valor1, valor2)`                         | `NULLIF(5, 5)`                                                 |
| `LENGTH()`        | Devuelve la longitud de una cadena de caracteres.                                                  | `LENGTH(cadena)`                                 | `LENGTH('Hola Mundo')`                                         |
| `SUBSTRING()`     | Extrae una parte de una cadena de texto, especificando la posición inicial y la longitud.          | `SUBSTRING(cadena, inicio, longitud)`            | `SUBSTRING('abcdef', 2, 3)` (Resultado: `bcd`)                 |
| `REPLACE()`       | Reemplaza parte de una cadena de texto por otra.                                                   | `REPLACE(cadena, parte_antigua, parte_nueva)`    | `REPLACE('Hola Mundo', 'Mundo', 'SQL')`                        |
| `UPPER()`         | Convierte una cadena de texto a mayúsculas.                                                        | `UPPER(cadena)`                                  | `UPPER('hola')` (Resultado: `HOLA`)                            |
| `LOWER()`         | Convierte una cadena de texto a minúsculas.                                                        | `LOWER(cadena)`                                  | `LOWER('HOLA')` (Resultado: `hola`)                            |
| `CONCAT()`        | Concatenación de dos o más valores, combinando múltiples cadenas de texto en una sola.             | `CONCAT(valor1, valor2, ...)`                    | `CONCAT('Hola', ' ', 'Mundo')`                                 |
| `YEAR()`          | Extrae el año de una fecha.                                                                        | `YEAR(fecha)`                                    | `YEAR('2023-09-21')` (Resultado: `2023`)                       |
| `MONTH()`         | Extrae el mes de una fecha.                                                                        | `MONTH(fecha)`                                   | `MONTH('2023-09-21')` (Resultado: `9`)                         |
| `DAY()`           | Extrae el día de una fecha.                                                                        | `DAY(fecha)`                                     | `DAY('2023-09-21')` (Resultado: `21`)                          |
| `DATEDIFF()`      | Calcula la diferencia entre dos fechas en días.                                                    | `DATEDIFF(fecha1, fecha2)`                       | `DATEDIFF('2023-09-21', '2023-09-01')` (Resultado: `20`)       |
| `AVG()`           | Calcula el promedio de un conjunto de valores numéricos.                                           | `AVG(campo)`                                     | `AVG(salario)`                                                 |
| `SUM()`           | Suma todos los valores de un conjunto numérico.                                                    | `SUM(campo)`                                     | `SUM(salario)`                                                 |
| `COUNT()`         | Devuelve el número de filas que cumplen con una condición.                                         | `COUNT(campo)`                                   | `COUNT(*)`                                                     |
| `MIN()`           | Devuelve el valor mínimo de un conjunto de datos.                                                  | `MIN(campo)`                                     | `MIN(salario)`                                                 |
| `MAX()`           | Devuelve el valor máximo de un conjunto de datos.                                                  | `MAX(campo)`                                     | `MAX(salario)`                                                 |


## Pregunta 1:
**¿Cómo elegirías entre los tipos de datos `VARCHAR` e `INT` al diseñar una tabla en una base de datos?**

### Respuesta:
"Al diseñar una tabla, elijo `VARCHAR` para almacenar texto de longitud variable, asignando un tamaño máximo para evitar el desperdicio de espacio. Si el dato es numérico, uso `INT` para números enteros y `DECIMAL` o `FLOAT` para números con decimales. `DECIMAL` es más adecuado cuando se necesita precisión exacta, como para precios, mientras que `FLOAT` es más eficiente en el uso de memoria, aunque menos preciso. Para fechas, utilizo `DATE`, que almacena los datos en el formato `YYYY-MM-DD`, adecuado cuando no es necesario almacenar la hora."

## Pregunta 2:
**¿Qué es la conversión de tipos de datos y cuándo es necesario realizarla en una base de datos?**

### Respuesta :
"La conversión de tipos de datos es el proceso de transformar un valor de un tipo de dato a otro, como convertir una cadena de texto (`VARCHAR`) a un número (`INT`) o una fecha a texto. Existen dos tipos de conversiones: implícitas, que el sistema realiza automáticamente cuando los tipos de datos son compatibles, y explícitas, que deben ser forzadas con funciones como `CAST()` o `CONVERT()`. La conversión es necesaria, por ejemplo, cuando necesitas realizar cálculos con datos que originalmente están en formato de texto o cuando formateas datos numéricos para mostrarlos en un reporte."

## Pregunta 3:
**¿Cuándo deberías usar `DECIMAL` en lugar de `FLOAT` y por qué?**

### Respuesta :
"Usaría `DECIMAL` cuando necesito una precisión exacta, como en valores financieros o precios, ya que garantiza que los números no tengan errores de redondeo. Por otro lado, usaría `FLOAT` cuando manejo grandes cantidades de datos numéricos que no requieren tanta precisión, como cálculos científicos, donde el espacio en memoria es más importante que la precisión exacta."

## Pregunta 4:
**¿Qué problemas podrían surgir al no elegir el tipo de dato adecuado para una columna en una base de datos?**

### Respuesta :
"No elegir el tipo de dato adecuado en una columna puede generar varios problemas. Por ejemplo, si usamos un tipo `VARCHAR` para almacenar datos numéricos, puede ser difícil realizar cálculos o comparaciones eficientes. Si usamos un tipo de dato más grande de lo necesario, como `DECIMAL` en lugar de `INT` cuando no es necesario manejar decimales, estaríamos desperdiciando almacenamiento y disminuyendo la eficiencia de las consultas. También puede haber problemas de precisión, como al usar `FLOAT` para manejar precios, lo que podría generar errores de redondeo no deseados."

## Pregunta 5:
**¿Cómo manejarías la conversión de tipos de datos al trabajar con fechas en una base de datos?**

### Respuesta :
"Al manejar fechas en una base de datos, la conversión depende del análisis que quiero realizar. Si necesito trabajar con el año, uso la función `YEAR(fecha)` para extraer el año, `MONTH(fecha)` para el mes, y `DAY(fecha)` para el día. Si las fechas están almacenadas como cadenas, primero convierto el dato a un formato de fecha adecuado con `CAST()` o `CONVERT()`. Esto es útil cuando las fechas no están en el formato correcto y necesito hacer cálculos como la diferencia entre dos fechas o comparaciones de tiempo."

### Pregunta 6:
**¿Cómo manejarías valores nulos (`NULL`) en una columna con tipos de datos numéricos, como `INT` o `DECIMAL`?**

### Respuesta :
"En una base de datos, `NULL` representa la ausencia de valor, lo que significa que no se ha asignado ningún valor a esa columna, mientras que `0` es un valor numérico válido. Al manejar columnas numéricas con valores `NULL`, utilizo funciones como `COALESCE()` o `ISNULL()` para reemplazar `NULL` por un valor predeterminado, como `0`, especialmente si necesito realizar cálculos como sumas o promedios. Esto evita que los cálculos se vean afectados por la presencia de valores nulos."


