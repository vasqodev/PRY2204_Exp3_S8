# 🚗 Proyecto Base de Datos: Taller Mecánico Mikes Ltda.
**Asignatura:** Modelamiento de Bases de Datos (PRY2204)  
**Semana:** 8 - Actividad Sumativa  
**Autor:** Rodrigo Vasquez  

## 📋 Descripción del Proyecto
Este repositorio contiene el script SQL final correspondiente al encargo **"Construyendo una base de datos a partir de un modelo relacional normalizado con sentencias SQL"**. 

El objetivo principal de este proyecto es implementar la base de datos para el **Taller Mecánico Mikes Ltda.** a partir de un Modelo Relacional normalizado previo. El desarrollo incluye la definición de la estructura de datos (DDL), la implementación de reglas de negocio específicas, el poblamiento inicial de las tablas (DML) y la construcción de informes estadísticos y financieros (DQL).

## 🛠️ Estructura del Script (`Exp3_S8_Rodrigo_Vasquez.sql`)

El script ha sido diseñado para ejecutarse de forma **secuencial y sin errores** en Oracle SQL Developer. Se ha estructurado en las siguientes fases lógicas:

1. **Limpieza de Entorno (Drop):** Se incluyó un bloque inicial con `DROP TABLE ... CASCADE CONSTRAINTS` y `DROP SEQUENCE`. Esta buena práctica permite al evaluador ejecutar el script múltiples veces sin conflictos de tablas o secuencias preexistentes.
2. **Creación de Tablas (DDL):** Se crearon las tablas respetando la jerarquía de dependencias (desde entidades fuertes a débiles). Se implementaron claves primarias (PK) y foráneas (FK) estructurales, asignando tipos de datos y atributos `IDENTITY` con sus respectivos incrementos (`PAIS` y `MECANICO`).
3. **Reglas de Negocio (ALTER TABLE):** Tal como exige el caso práctico, la estructura inicial fue modificada utilizando sentencias `ALTER TABLE` para aplicar reglas de negocio críticas:
   - Eliminación de la columna derivada `costo_total` en `MANTENCION`.
   - Reestructuración de la Clave Primaria de `MANTENCION` a una PK compuesta (`num_mantencion`, `cod_sucursal`) y la consecuente actualización de la Clave Foránea en `DETALLE_SERVICIO`.
   - Creación de restricciones `UNIQUE` (email de clientes) y validaciones `CHECK` (dígito verificador, sueldo mínimo de mecánicos y estados de mantención).
4. **Secuencias:** Creación de objetos `SEQUENCE` para la auto-generación de IDs en las tablas `SERVICIO` y `CIUDAD`.
5. **Poblamiento de Datos (DML):** Uso de sentencias `INSERT INTO` para poblar el modelo con datos de prueba, respetando la integridad referencial y las restricciones establecidas. Finaliza con un `COMMIT`.
6. **Generación de Informes (SELECT):**
   - **Informe 1:** Simulación de sueldo con rebaja de impuestos del 20% para mecánicos sin jefatura y con impuestos menores a $40.000.
   - **Informe 2:** Cálculo de un ajuste salarial del 5% para mecánicos con sueldos entre $600.000 y $900.000, o que no posean un supervisor asignado.

## 🚀 Instrucciones de Ejecución

Para evaluar este proyecto en **Oracle SQL Developer**:

1. Asegúrese de estar conectado con el usuario designado para la evaluación (`PRY2204_S8`).
2. Abra el archivo `Exp3_S8_Rodrigo_Vasquez.sql` en una nueva Hoja de Trabajo SQL.
3. Ejecute el script completo (presionando `F5` o el botón "Ejecutar Script").
4. Puede verificar los resultados de los informes en la ventana de "Salida de Script".

## 💡 Criterios de Evaluación Cumplidos (Pauta Semana 8)
- [x] **Construcción DDL:** Tablas creadas en el orden correcto, con atributos y nombres de restricciones representativos.
- [x] **Reglas de negocio (ALTER TABLE):** Todas las modificaciones, incluyendo la reestructuración de PK/FK compuestas y restricciones `CHECK`/`UNIQUE`, fueron aplicadas exitosamente.
- [x] **Poblamiento DML:** Datos insertados correctamente con uso de `IDENTITY` y `SEQUENCE`.
- [x] **Recuperación DQL:** Informes generados con cláusulas `WHERE` complejas (operadores lógicos, `IS NULL`, `BETWEEN`), alias de columnas, operaciones matemáticas y ordenamiento dinámico con `ORDER BY`.

---
*Desarrollado para la entrega final de la semana 8 - Duoc UC Online.*
