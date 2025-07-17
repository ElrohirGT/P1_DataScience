---
header-includes:
  - \usepackage{amsmath}
  - \usepackage{amssymb}
  - \usepackage{fontspec}
  - \setmainfont{FiraCode Nerd Font}
  - \setmonofont{FiraCode Nerd Font Mono}
  - \usepackage{setspace}
  - \setstretch{1.5}
  - \usepackage{fvextra}
  - \DefineVerbatimEnvironment{Highlighting}{Verbatim}{breaklines,commandchars=\\\{\}}
  - \hypersetup{colorlinks=true, linkcolor=blue, urlcolor=blue}
  - \usepackage{geometry}
  - \usepackage{etoolbox}
  - \AtBeginEnvironment{longtable}{\scriptsize}
geometry: top=0.67in, bottom=0.67in, left=0.85in, right=0.85in
---

# Libro de Códigos

Este libro de codigos contiene información del dataset `data_clean.csv` que contiene:

- Total de filas: 6599
- Total de columnas: 21

Este libro también contiene descripciones, tipos de datos y valores válidos. Se generó como parte del proceso de limpieza, análisis y validación de datos sobre establecimientos educativos en Guatemala.

## Enlaces

- [Enlace a GitHub](https://github.com/ElrohirGT/P1_DataScience)
- No se trabajó google docs sino md en el repositorio en la carpeta [docs/libro_codigos](https://github.com/ElrohirGT/P1_DataScience/blob/main/docs/libro_codigos.md)

## Variables del Dataset

### 1. `codigo_departamento`

- **Descripción**: Código oficial del departamento según el sistema administrativo guatemalteco.
- **Tipo**: Texto (`object`)
- **Ejemplos**: `"01"`, `"16"`, `"00"`
- **Observaciones**: Se usa en combinación con `codigo_municipio` para formar la clave geográfica.

### 2. `departamento`

- **Descripción**: Nombre del departamento al que pertenece el establecimiento.
- **Tipo**: Texto
- **Ejemplos**: `"GUATEMALA"`, `"ZACAPA"`, `"ALTA VERAPAZ"`

### 3. `codigo_municipio`

- **Descripción**: Código oficial del municipio según el sistema administrativo guatemalteco.
- **Tipo**: Texto
- **Ejemplos**: `"01"`, `"09"`, `"13"`

### 4. `municipio`

- **Descripción**: Nombre del municipio en donde está ubicado el establecimiento.
- **Tipo**: Texto
- **Ejemplos**: `"COBAN"`, `"ZONA 1"`, `"ZACAPA"`

### 5. `codigo_establecimiento`

- **Descripción**: Identificador del establecimiento dentro del sistema (descripción asumida por parte del código original del dataset).
- **Tipo**: Texto
- **Ejemplo**: `"0138"`, `"0243"`

### 6. `codigo_interno`

- **Descripción**: Código de control interno del establecimiento (descripción asumida por parte del código original del dataset).
- **Tipo**: Texto
- **Ejemplo**: `"46"`

### 7. `codigo_distrito`

- **Descripción**: Identificador del distrito al que pertenece el establecimiento.
- **Tipo**: Texto
- **Ejemplo**: `"403"`, `"318"`

### 8. `establecimiento`

- **Descripción**: Nombre oficial del establecimiento educativo.
- **Tipo**: Texto

### 9. `tipo_establecimiento`

- **Descripción**: Clasificación general del establecimiento.
- **Tipo**: Texto
- **Valores posibles**:
  - COLEGIO
  - ESCUELA
  - INSTITUTO
  - LICEO
  - CENTRO
  - HOMESCHOOL
  - PROGRAMA
  - CEEX
  - TECNICO
  - COMPLEJO
  - FUNDACION
  - ACADEMIA
  - INED
  - CORPORACION
  - ASOCIACION
  - MODALIDADES

### 10. `direccion`

- **Descripción**: Dirección registrada del establecimiento.
- **Tipo**: Texto
- **Valores nulos tratados como**: `"SIN DIRECCION"`

### 11. `telefono`

- **Descripción**: Teléfono principal del establecimiento (8 dígitos).
- **Tipo**: Texto
- **Valores nulos tratados como**: `"SIN TELEFONO"`

### 12. `supervisor`

- **Descripción**: Nombre del supervisor asignado.
- **Tipo**: Texto

### 13. `director`

- **Descripción**: Nombre del director del establecimiento.
- **Tipo**: Texto
- **Valores nulos tratados como**: `"NO REGISTRADO"`

### 14. `nivel`

- **Descripción**: Nivel educativo que ofrece el establecimiento.
- **Tipo**: Texto
- **Valores únicos**:
  - DIVERSIFICADO (6599 casos)

### 15. `sector`

- **Descripción**: Sector al que pertenece el establecimiento.
- **Tipo**: Categórica
- **Valores únicos**:
  - PRIVADO (5417)
  - OFICIAL (874)
  - COOPERATIVA (213)
  - MUNICIPAL (95)

### 16. `area`

- **Descripción**: Localización geográfica.
- **Tipo**: Categórica
- **Valores únicos**:
  - URBANA (5249)
  - RURAL (1349)
  - SIN ESPECIFICAR (1)

### 17. `status`

- **Descripción**: Estado operativo del establecimiento.
- **Tipo**: Categórica
- **Valores únicos**:
  - ABIERTA (6599)

### 18. `modalidad`

- **Descripción**: Modalidad lingüística del establecimiento.
- **Tipo**: Texto
- **Valores únicos**:
  - MONOLINGUE (6390)
  - BILINGUE (209)

### 19. `jornada`

- **Descripción**: Jornada escolar.
- **Tipo**: Texto
- **Valores únicos**:
  - MATUTINA (1686)
  - VESPERTINA (1836)
  - NOCTURNA (106)
  - DOBLE (1957)
  - INTERMEDIA (13)
  - SIN JORNADA (1001)

### 20. `plan`

- **Descripción**: Tipo de plan de estudios.
- **Tipo**: Texto
- **Valores únicos**:
  - DIARIO(REGULAR) (4051)
  - FIN DE SEMANA (1310)
  - SEMIPRESENCIAL (490)
  - SEMIPRESENCIAL (UN DIA A LA SEMANA) (409)
  - SEMIPRESENCIAL (DOS DIAS A LA SEMANA) (62)
  - A DISTANCIA (116)
  - VIRTUAL A DISTANCIA (52)
  - SEMIPRESENCIAL (99)
  - SABATINO (5)
  - INTERCALADO (2)
  - DOMINICAL (2)
  - MIXTO (1)

### 21. `departamental`

- **Descripción**: División interna utilizada en la administración educativa.
- **Tipo**: Texto
- **Ejemplos**:
  - GUATEMALA NORTE
  - GUATEMALA SUR
  - GUATEMALA OCCIDENTE
  - GUATEMALA ORIENTE
  - QUICHE NORTE
