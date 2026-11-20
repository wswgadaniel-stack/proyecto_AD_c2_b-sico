# Modelo de datos del proyecto

## 1. Descripción general

El dataset contiene información relacionada con reportes de producción, tiempos, desperdicios y operaciones realizadas en las diferentes áreas de la empresa.

La fuente de información es el sistema corporativo ERP Epicor.

El diccionario de datos entregado contiene 35 campos que permiten identificar trabajos, productos, operaciones, máquinas, empleados, cantidades producidas y tiempos reportados.

## 2. Estructura del dataset

| Característica | Descripción |
|---|---|
| Nombre de la hoja del diccionario | Data_set |
| Cantidad de campos | 35 |
| Fuente | ERP Epicor |
| Tipo de información | Reportes de producción y operaciones |
| Estructura | Dataset tabular |

**Nota:** el archivo de Excel utilizado como referencia contiene el diccionario de datos, no los registros completos de producción.

## 3. Diccionario de campos

Los tipos de datos se basan en la información registrada en el diccionario original. Cuando el tipo o la descripción no están especificados, se indica como pendiente de confirmar.

| N.º | Campo | Tipo de dato | Descripción y significado |
|---:|---|---|---|
| 1 | JobNum | Alfanumérico | Número de trabajo o lote. Identifica también a qué unidad de negocio pertenece. Ejemplo: FE769236. FE significa FirmeEmpaques y corresponde a un trabajo confirmado con órdenes de producción. |
| 2 | TrabajoReport | Alfanumérico | Trabajo en el que se reporta el registro. Identifica qué trabajo está reportando desperdicio a otro trabajo o a sí mismo. |
| 3 | PartNum | Alfanumérico | Número de parte o identificador único del producto. Funciona como una identificación individual, similar a una cédula. |
| 4 | PartDescription | Texto | Nombre o descripción del producto. |
| 5 | OprSeq | Numérico | Secuencia de la operación en la que se realizó el registro. Puede ir desde 0 hasta 200. Permite identificar en qué operación se realiza el reporte de tiempos. |
| 6 | Op_Report | Numérico | Número de operación en la que se reporta el registro. Identifica qué operación está reportando desperdicio a otra operación o a sí misma. |
| 7 | ResourceID | Alfanumérico | Máquina en la que se realizó el reporte. Es el número o identificador de la máquina de producción. |
| 8 | Recurso_Report | Alfanumérico | Máquina o recurso que reporta desperdicio a otro recurso o a sí mismo. |
| 9 | EmployeeNum | Numérico | Código único del empleado. |
| 10 | Empleado_Report | Numérico | Empleado que reportó alguna novedad. Identifica qué empleado está reportando desperdicio a otro empleado o a sí mismo. |
| 11 | Departamento | Texto | Departamento o área de trabajo. Puede corresponder a extrusión, impresión, laminación, corte y refilado, sellado o insertadoras. |
| 12 | Desperdicio01 | Numérico | Cantidad de desperdicio o muda reportada. |
| 13 | JobOper_OpCode | Texto | Código de la operación. Las operaciones tienen un código dependiendo del área de la empresa donde se ejecutan. |
| 14 | Metros | Numérico | Cantidad de producción reportada en metros. |
| 15 | Kilogramos | Numérico | Cantidad de producción reportada en kilogramos. |
| 16 | LaborType | Texto | Tipo de labor. Los valores son S (Setup), I (Indirectos) y P (Producción). Especifica a qué tipo corresponden los tiempos reportados. |
| 17 | Cod_Motivo | Numérico | Código de cada reporte en Epicor. Según el diccionario, cada reporte tiene un código único. |
| 18 | Motivo | Texto | Descripción textual del motivo asociado al código del reporte. |
| 19 | Fecha_Ingreso | Fecha | Fecha del reporte. |
| 20 | LaborNote | Texto | Nota del operario. Puede contener números. |
| 21 | Calculated_F_Material | Texto | Estructura del material. |
| 22 | LaborHed_Shift | Pendiente | Campo sin descripción ni tipo de dato especificados en el diccionario. |
| 23 | LaborDtlTop_DiscrepQty | Pendiente | Campo sin descripción ni tipo de dato especificados en el diccionario. |
| 24 | Calculated_F_ProdEsta | Pendiente | Campo sin descripción ni tipo de dato especificados en el diccionario. |
| 25 | Calculated_F_HorasEsti | Pendiente | Campo relacionado con horas estimadas. Falta confirmar el tipo de dato y su definición exacta. |
| 26 | Calculated_F_HorasReales | Pendiente | Campo relacionado con horas reales. Falta confirmar el tipo de dato y su definición exacta. |
| 27 | DspClockInTime | Pendiente | Campo sin descripción ni tipo de dato especificados en el diccionario. |
| 28 | DspClockOutTime | Pendiente | Campo sin descripción ni tipo de dato especificados en el diccionario. |
| 29 | ResourceGroup | Pendiente | Campo sin descripción ni tipo de dato especificados en el diccionario. |
| 30 | FechaInicio | Fecha | Fecha de inicio. |
| 31 | FechaFinal | Fecha | Fecha de finalización. |
| 32 | Año | Fecha (según diccionario) | Campo relacionado con el año del registro. Se debe confirmar el tipo de dato real. |
| 33 | Nombre del mes | Fecha (según diccionario) | Campo relacionado con el nombre del mes. Se debe confirmar el tipo de dato real. |
| 34 | Semana del año | Fecha (según diccionario) | Campo relacionado con la semana del año. Se debe confirmar el tipo de dato real. |
| 35 | Operario | Pendiente | Campo sin descripción ni tipo de dato especificados en el diccionario. |

## 4. Identificación de relaciones entre campos

El diccionario permite identificar posibles relaciones entre los campos del dataset.

### 4.1. Relación con los trabajos

- JobNum: identifica el trabajo de producción.
- TrabajoReport: identifica el trabajo que reporta desperdicio a otro trabajo o a sí mismo.

### 4.2. Relación con las operaciones

- OprSeq: identifica la secuencia de la operación.
- Op_Report: identifica la operación que realiza el reporte.
- JobOper_OpCode: identifica el código de la operación.

### 4.3. Relación con los recursos

- ResourceID: identifica la máquina donde se realizó el reporte.
- Recurso_Report: identifica el recurso que reporta desperdicio.
- ResourceGroup: campo pendiente de definición.

### 4.4. Relación con los empleados

- EmployeeNum: identifica al empleado.
- Empleado_Report: identifica al empleado que reporta desperdicio.
- Operario: campo pendiente de definición.

### 4.5. Relación con los productos

- PartNum: identifica el producto.
- PartDescription: contiene su descripción.
- Calculated_F_Material: contiene información sobre la estructura del material.

Estas relaciones son asociaciones identificadas a partir de las descripciones. No representan todavía relaciones verificadas mediante llaves primarias o foráneas.

## 5. Nivel de detalle del dataset

El nivel de detalle exacto de cada registro está pendiente de confirmación con el dataset original.

Se debe verificar si cada fila representa un reporte individual de producción, tiempos, desperdicio o una novedad operativa.

También se debe validar si un mismo trabajo puede tener diferentes operaciones, recursos y empleados asociados.

## 6. Controles de calidad de los datos

Se proponen los siguientes controles:

- Revisar registros sin número de trabajo.
- Validar la correspondencia entre trabajos y trabajos reportados.
- Verificar que los códigos de producto tengan una descripción asociada.
- Revisar la consistencia de las secuencias y operaciones reportadas.
- Validar que los recursos y empleados estén correctamente identificados.
- Identificar valores nulos o inconsistentes en las cantidades producidas.
- Revisar cantidades negativas o valores atípicos en metros, kilogramos y desperdicios.
- Comprobar que los códigos de motivo tengan una descripción asociada.
- Validar las fechas de ingreso, inicio y finalización.
- Revisar la coherencia de los tiempos estimados y reales.

## 7. Pendientes de validación

Para completar el modelo de datos se requiere:

1. Confirmar los tipos de datos de los campos que no tienen definición.
2. Aclarar el significado de LaborHed_Shift, LaborDtlTop_DiscrepQty, Calculated_F_ProdEsta, DspClockInTime, DspClockOutTime y ResourceGroup.
3. Confirmar el significado de Operario.
4. Verificar si Cod_Motivo es realmente único por registro.
5. Identificar la llave o combinación de campos que identifica cada registro.
6. Confirmar las relaciones entre trabajos, operaciones, recursos y empleados.
7. Validar el nivel de detalle de cada fila.
8. Confirmar los tipos reales de Año, Nombre del mes y Semana del año.

## 8. Conclusión

El dataset contiene información útil para analizar la producción y el desempeño operativo de la empresa.

Sus campos permiten identificar trabajos, productos, operaciones, máquinas, empleados, cantidades producidas, desperdicios y tiempos.

Esta información puede servir como base para analizar indicadores como OEE, tiempos de ciclo y calidad, una vez se validen la estructura, los registros y las reglas de cálculo correspondientes.