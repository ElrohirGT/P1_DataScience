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
- **Valores nulos por columna**:

  - `direccion`: 2 valores nulos
  - `telefono`: 46 valores nulos
  - `director`: 26 valores nulos
  - Resto de columnas: 0 valores nulos
- **Tipo de datos por columna**: Todas las columnas son de tipo `object` (texto), incluso aquellas que podrían representar datos categóricos o numéricos.

#### Variables del Conjunto de Datos

A continuación se listan las variables que componen el dataset, junto con una breve descripción del tipo de información que contienen:

| Variable          | Descripción                                                                                                               |
|-------------------|---------------------------------------------------------------------------------------------------------------------------|
| `codigo`          | Identificador único del establecimiento educativo. Formato compuesto por códigos departamentales, municipales y de nivel. |
| `distrito`        | Código que representa el distrito educativo al que pertenece el establecimiento.                                          |
| `departamento`    | Nombre del departamento geográfico (ej. ALTA VERAPAZ).                                                                    |
| `municipio`       | Nombre del mu nicipio donde se encuentra ubicado el centro educativo.                                                     |
| `establecimiento` | Nombre oficial del establecimiento, que puede incluir variaciones en ortografía, uso de mayúsculas o símbolos.            |
| `direccion`       | Ubicación física del establecimiento, usualmente con calles, zonas o kilómetros.                                          |
| `telefono`        | Número telefónico de contacto. Presenta formato numérico pero se encuentra almacenado como texto.                         |
| `supervisor`      | Nombre del supervisor a cargo del área o distrito educativo del establecimiento.                                          |
| `director`        | Nombre del director o responsable directo del establecimiento.                                                            |
| `nivel`           | Nivel educativo ofrecido por el establecimiento (en todos los casos: DIVERSIFICADO).                                      |
| `sector`          | Define si el establecimiento es de carácter PRIVADO u OFICIAL.                                                            |
| `area`            | Zona en la que opera el establecimiento: URBANA o RURAL.                                                                  |
| `status`          | Estado de funcionamiento del centro educativo (ej. ABIERTA).                                                              |
| `modalidad`       | Modalidad lingüística o pedagógica (ej. MONOLINGÜE, BILINGÜE).                                                            |
| `jornada`         | Jornada o turno en que se imparten las clases (ej. MATUTINA, VESPERTINA).                                                 |
| `plan`            | Tipo de plan de estudios ofrecido (ej. DIARIO(REGULAR)).                                                                  |
| `departamental`   | Nombre del departamento, redundante con la columna `departamento` pero útil para verificar integridad.                    |

### [ ] Análisis Exploratorio Inicial

> pendiente...

### [ ] Estrategia Propuesta para la Limpieza

Antes de aplicar las transformaciones específicas por variable, **se realizó un análisis exploratorio general de valores nulos**, identificando columnas con valores vacíos reales o simulados (como cadenas vacías `" "` o espacios `"  "`).
Como primer paso de limpieza, **se reemplazaron todos estos casos por valores nulos reales (`np.nan`)**, con el objetivo de facilitar su posterior tratamiento, análisis de calidad y filtrado.

A continuación, se detalla la estrategia específica aplicada por variable:

| Variable(s)                                                | Problema Detectado                                                                                           | Operación de Limpieza Propuesta                                                                                                                                                                 | Justificación                                                                                                 |
| ---------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| `establecimiento`                                          | Inconsistencias tipográficas: uso mixto de mayúsculas/minúsculas, dobles espacios, comillas, y abreviaciones | - Normalizar a MAYÚSCULAS.<br>- Eliminar dobles espacios.<br>- Estandarizar comillas.<br>- Crear nueva columna `tipo_establecimiento` a partir de patrones comunes (ej. "Colegio", "Instituto") | Mejora consistencia textual y permite clasificar o agrupar fácilmente por tipo de centro educativo.           |
| `direccion`                                                | Texto no estructurado con errores ortográficos y abreviaciones irregulares (ej. "km", "zona")                | - Corregir espacios.<br>- Estandarizar abreviaciones comunes para guatemala (`km` → `Km`, `zona` → `Zona`, etc.).<br>- Normalizar formato general                                                              | Facilita georreferenciación futura, análisis espacial y cruce con mapas.                                      |
| `telefono`                                                 | Verificación de formato inconsistente, con caracteres no numéricos y longitudes incorrectas                                  | - Validar longitud de 8 dígitos.<br>- Normalizar como texto limpio                                                                                        | Permite validar teléfonos, contactar a centros o analizar cobertura de comunicación.                          |
| `departamento`, `departamental`                            | Campos redundantes. Posibles diferencias tipográficas                                                        | - Verificar coincidencia exacta entre ambos.<br>- Si son equivalentes, eliminar `departamental`                                                                                                 | Elimina duplicidad innecesaria y refuerza integridad de la variable geográfica.                               |
| `codigo`                                                   | Campo compuesto que incluye subcódigos concatenados                                                          | - Separar en columnas nuevas: `codigo_departamento`, `codigo_municipio`, `codigo_establecimiento`, `codigo_interno` (si aplica).<br>- Eliminar campo original `codigo`                          | Facilita segmentación, análisis por región y comprensión jerárquica del código.                               |
| `supervisor`, `director`                                   | Nombres con inconsistencias en tildes, uso de mayúsculas o espacios extra                                    | - Normalizar: quitar espacios innecesarios, capitalizar correctamente, corregir tildes comunes                                                                                                  | Mejora identificación de responsables y su cruce con otros registros institucionales.                         |
| `modalidad`, `jornada`, `plan`, `status`, `sector`, `area` | Variaciones tipográficas en valores iguales (ej. "MATUTINA", "matutina", " MATUTINA ")                       | - Estandarizar todos los valores en MAYÚSCULAS.<br>- Eliminar espacios innecesarios                                                                                                             | Asegura agrupamientos correctos al analizar por categoría o filtro.                                           |
| General (todas las columnas)                               | Presencia de `" "` o cadenas vacías que aparentan ser datos válidos                                          | - Reemplazar por valores `NaN` o nulos reales (`np.nan`)                                                                                                                                        | Mejora la detección de valores faltantes y permite análisis precisos de calidad de datos.                     |
| Todo el dataset                                            | Todos los campos son tipo `object` (texto), incluso numéricos o categóricos                                  | - Mantener `telefono` como texto limpio.<br>- Evaluar tipado adecuado para análisis posterior: convertir valores categóricos (`status`, `sector`, etc.) y códigos numéricos donde aplique       | Permite eficiencia en análisis estadístico, creación de visualizaciones, y compatibilidad con otros sistemas. |

## Resumen de Estado

| Etapa                                                         | Estado   |
|---------------------------------------------------------------|----------|
| Descarga de los datos                                         | ✅       |
| Unificación y exportación a CSV                               | ✅       |
| Conteo de filas y columnas del set unificado                  | ✅       |
| Conteo de filas y columnas del set unificado                  | ✅       |
| Conteo de duplicados y valores nulos por columna              | ✅       |
| Identificación del tipo de datos por variable                 | ✅       |
| Descripción general de cada variable                          | ✅       |
| Definición de estrategia de limpieza                          | ✅       |
| Implementación de operaciones de limpieza                     | [ ]      |
| Revisión de duplicados e inconsistencias en campos clave      | [ ]      |
| Generación del conjunto limpio                                | [ ]      |
| Documentación de variables y metadatos                        | [ ]      |
