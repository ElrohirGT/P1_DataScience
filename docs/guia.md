# Proyecto: Limpieza de Datos de Establecimientos Educativos de Nivel Diversificado en Guatemala

## Descarga de Datos

- Fuente oficial: Ministerio de Educación de Guatemala.
- Enlace de descarga: [http://www.mineduc.gob.gt/BUSCAESTABLECIMIENTO_GE/](http://www.mineduc.gob.gt/BUSCAESTABLECIMIENTO_GE/)
- Alcance: Establecimientos educativos hasta el nivel escolar “Diversificado”.

## Almacenamiento de Datos Crudos

- Formato: Archivos .csv
- Organización: Un archivo por departamento o conjunto completo según disponibilidad.
- Conservación de datos originales sin modificaciones.

## Estado de los Datos y Diagnóstico Inicial

- Revisión de la estructura de los archivos.
- Identificación de:
  - Inconsistencias tipográficas
  - Valores nulos
  - Formatos inconsistentes en campos clave (nombre, dirección, teléfono)
  - Posibles registros duplicados

## Operaciones de Limpieza

- Estándar de limpieza aplicado a todas las variables.
- Transformación de texto (mayúsculas/minúsculas, eliminación de espacios en blanco).
- Normalización de campos clave:
  - **Nombre del establecimiento**: corrección de errores tipográficos, uniformidad.
  - **Dirección**: estandarización de calles, zonas, y números.
  - **Teléfono**: formato uniforme, eliminación de caracteres no numéricos.
- Consolidación de registros con nombres similares que representan un mismo establecimiento.
- Registro detallado de cada operación realizada con su justificación.

## Conjunto de Datos Limpios

- Integración de todos los departamentos en un solo archivo limpio.
- Validación de unicidad en campos clave.
- Inclusión solo de variables relevantes y completas.
- Preparado para análisis, sin decisiones analíticas previas.

## Libro de Códigos

- Descripción general del conjunto de datos:
  - Fuente
  - Fecha de descarga
  - Nivel educativo incluido
- Descripción de cada variable:
  - Nombre
  - Tipo de dato
  - Valores posibles
  - Observaciones relevantes
- Registro de variables creadas durante la limpieza, si corresponde.

## Rúbrica de Evaluación

| Criterio                                             | Puntos | Descripción                                                                 |
|------------------------------------------------------|--------|-----------------------------------------------------------------------------|
| Carga de los conjuntos de datos                      | 5      | Evidencia clara de descarga y carga de archivos .csv                       |
| Análisis del estado de los datos crudos              | 15     | Diagnóstico detallado previo a la limpieza                                 |
| Operaciones de limpieza y justificación              | 45     | Limpieza completa, documentada y justificada, atención a campos clave     |
| Libro de códigos                                     | 25     | Bien estructurado, claro, con metadatos y descripción de variables         |
| Generación del conjunto de datos limpios             | 10     | Archivo final limpio, consolidado, sin duplicaciones ni errores visibles  |
| **Total**                                            | **100**|                                                                             |
