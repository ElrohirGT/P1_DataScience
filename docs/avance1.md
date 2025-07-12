# Avance del Proyecto: Limpieza de Datos de Establecimientos Educativos de Nivel Diversificado en Guatemala

## Entregable: Análisis del Estado Inicial del Conjunto de Datos

Este avance tiene como objetivo entregar una descripción detallada del conjunto de datos crudos descargado, identificar variables que requerirán mayor atención durante la limpieza, y definir una estrategia de limpieza sin implementarla aún.

## Componentes del Avance

### ✅ Descarga y Unificación de los Datos

- Se desarrolló un script en Python utilizando Selenium para automatizar la descarga de datos desde el sitio del Ministerio de Educación.
- Se implementó un sistema de cacheo basado en el archivo `links_cache.txt` para evitar descargas repetidas.
- Los datos fueron almacenados en archivos `.txt` en formato Python.
- Se unificaron todos los datos en un único archivo `.csv` (`data_unified.csv`).

### ✅ Estructura del Conjunto de Datos Crudo

En esta sección se presenta un análisis exploratorio del conjunto de datos unificado que contiene información de establecimientos educativos a nivel diversificado en Guatemala. El objetivo es comprender su composición inicial, identificar posibles irregularidades estructurales y sentar las bases para las futuras operaciones de limpieza.

#### Dimensiones Generales del Dataset

- **Total de filas (registros)**: 6599
- **Total de variables (columnas)**: 17
- **Filas completamente duplicadas**: 0
- **Valores nulos**: No se detectan valores nulos en ninguna de las columnas. Todos los registros tienen datos presentes en las variables disponibles.
- **Tipo de datos**: Todas las columnas son de tipo `object` (texto).

#### Variables del Conjunto de Datos

A continuación se listan las variables que componen el dataset, junto con una breve descripción del tipo de información que contienen:

| Variable        | Descripción                                                                                      |
|----------------|--------------------------------------------------------------------------------------------------|
| `codigo`       | Identificador único del establecimiento educativo. Formato compuesto por códigos departamentales, municipales y de nivel. |
| `distrito`     | Código que representa el distrito educativo al que pertenece el establecimiento.                 |
| `departamento` | Nombre del departamento geográfico (ej. ALTA VERAPAZ).                                           |
| `municipio`    | Nombre del municipio donde se encuentra ubicado el centro educativo.                             |
| `establecimiento` | Nombre oficial del establecimiento, que puede incluir variaciones en ortografía, uso de mayúsculas o símbolos. |
| `direccion`    | Ubicación física del establecimiento, usualmente con calles, zonas o kilómetros.                |
| `telefono`     | Número telefónico de contacto. Presenta formato numérico pero se encuentra almacenado como texto.|
| `supervisor`   | Nombre del supervisor a cargo del área o distrito educativo del establecimiento.                 |
| `director`     | Nombre del director o responsable directo del establecimiento.                                   |
| `nivel`        | Nivel educativo ofrecido por el establecimiento (en todos los casos: DIVERSIFICADO).             |
| `sector`       | Define si el establecimiento es de carácter PRIVADO u OFICIAL.                                   |
| `area`         | Zona en la que opera el establecimiento: URBANA o RURAL.                                         |
| `status`       | Estado de funcionamiento del centro educativo (ej. ABIERTA).                                     |
| `modalidad`    | Modalidad lingüística o pedagógica (ej. MONOLINGÜE, BILINGÜE).                                   |
| `jornada`      | Jornada o turno en que se imparten las clases (ej. MATUTINA, VESPERTINA).                        |
| `plan`         | Tipo de plan de estudios ofrecido (ej. DIARIO(REGULAR)).                                         |
| `departamental`| Nombre del departamento, redundante con la columna `departamento` pero útil para verificar integridad. |

### [ ] Análisis Exploratorio Inicial

> pendiente...

### [ ] Variables que Requieren Mayor Atención en la Limpieza

> pendiente...

### [ ] Estrategia Propuesta para la Limpieza

> pendiente...

## Resumen de Estado

| Etapa                                                         | Estado   |
|---------------------------------------------------------------|----------|
| Descarga de los datos                                         | ✅      |
| Unificación y exportación a CSV                               | ✅      |
| Conteo de filas y columnas del set unificado                  | ✅      |
| Conteo de filas y columnas del set unificado                  | ✅ |
| Conteo de duplicados y valores nulos por columna              | ✅ |
| Identificación del tipo de datos por variable                 | ✅ |
| Descripción general de cada variable                          | ✅ |
| Identificación de variables críticas para limpieza            | [ ]      |
| Definición preliminar de estrategia de limpieza               | [ ]      |
| Implementación de operaciones de limpieza                     | [ ]      |
| Revisión de duplicados e inconsistencias en campos clave      | [ ]      |
| Generación del conjunto limpio                                | [ ]      |
| Documentación de variables y metadatos                        | [ ]      |
