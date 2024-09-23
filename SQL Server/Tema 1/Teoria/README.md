
# Resumen de Consultas - 22-09-2024

Este documento resume las principales consultas realizadas sobre SQL Server y cómo abordar errores comunes en la manipulación de datos.

## Índice
1. [Conversión de Tipos de Datos en SQL](#conversion-de-tipos-de-datos-en-sql)
2. [Inserción de Datos Incorrectos](#insercion-de-datos-incorrectos)
3. [Errores de Truncamiento](#errores-de-truncamiento)
4. [Validación de Fechas](#validacion-de-fechas)
5. [Uso de DECIMAL y AS](#uso-de-decimal-y-as)
6. [Consulta de Tipos de Datos en Columnas](#consulta-de-tipos-de-datos-en-columnas)
7. [Conversión de Edad a INT](#conversion-de-edad-a-int)
8. [Suma de Valores en Columnas de Texto](#suma-de-valores-en-columnas-de-texto)

## 1. Conversión de Tipos de Datos en SQL
Se explican ejemplos para convertir valores entre tipos de datos utilizando las funciones `CAST()` y `CONVERT()`.

**Ejemplo SQL Server:**
```sql
SELECT CAST(Salario AS DECIMAL(10, 2)) AS SalarioDecimal
FROM PersonasErrores;
```

## 2. Inserción de Datos Incorrectos
Cómo crear tablas con datos erróneos para practicar conversiones de tipos de datos.

**Ejemplo de Creación de Tabla:**
```sql
CREATE TABLE PersonasErrores (
    PersonaID INT PRIMARY KEY IDENTITY(1,1),
    Nombre VARCHAR(50),
    Edad VARCHAR(10),
    FechaNacimiento VARCHAR(20),
    Salario VARCHAR(20)
);
```

## 3. Errores de Truncamiento
Solución al error "Msg 2628 Los datos binarios o de la cadena se truncan" mediante la modificación de la longitud de columnas.

**Solución:**
```sql
ALTER TABLE PersonasErrores ALTER COLUMN Edad VARCHAR(10);
```

## 4. Validación de Fechas
Cómo verificar si las fechas en una columna son válidas usando `ISDATE` en SQL Server.

**Consulta SQL Server:**
```sql
SELECT * FROM PersonasErrores WHERE ISDATE(FechaNacimiento) = 0;
```

## 5. Uso de DECIMAL y AS
Explicación del uso de `DECIMAL(10, 2)` y la función `AS` para renombrar columnas.

**Ejemplo:**
```sql
SELECT SUM(CAST(Salario AS DECIMAL(10, 2))) AS SumaSalarios
FROM PersonasErrores;
```

## 6. Consulta de Tipos de Datos en Columnas
Consulta para obtener los tipos de datos de las columnas en una tabla.

**Ejemplo:**
```sql
SELECT COLUMN_NAME, DATA_TYPE, CHARACTER_MAXIMUM_LENGTH
FROM INFORMATION_SCHEMA.COLUMNS
WHERE TABLE_NAME = 'PersonasErrores';
```

## 7. Conversión de Edad a INT
Métodos para convertir la columna `Edad` de `VARCHAR` a `INT` sin perder los datos originales.

**Ejemplo:**
```sql
UPDATE PersonasErrores SET Edad = NULL WHERE ISNUMERIC(Edad) = 0;

ALTER TABLE PersonasErrores ALTER COLUMN Edad INT;
```

## 8. Suma de Valores en Columnas de Texto
Suma de valores almacenados como texto utilizando `CAST()` para convertir los datos.

**Ejemplo SQL Server:**
```sql
SELECT SUM(CAST(Salario AS DECIMAL(10, 2))) AS SumaSalarios
FROM PersonasErrores
WHERE ISNUMERIC(Salario) = 1;
```
