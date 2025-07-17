# Limpieza de Datos - Proyecto 1 de Ciencia de Datos 🧹

Este repositorio contiene el desarrollo del proceso de **limpieza y unificación de datos** para el Proyecto 1 de Ciencia de Datos. Se parte de archivos dispersos y desorganizados para producir un único dataset consolidado y limpio, listo para análisis.

## 🧰 Instrucciones Rápidas

### 1. Clonar el repositorio

```bash
git clone https://github.com/ElrohirGT/P1_DataScience
cd P1_DataScience
```

### 2. Ejecutar con Nix (recomendado)

```bash
nix develop
jupyter-lab
```

> Esto abrirá Jupyter Lab. Desde ahí, ejecutar el notebook `Proyecto1.ipynb` para correr el flujo completo del proyecto.

### 3. Alternativa: VS Code

Si no usas Nix, puedes abrir el proyecto en VS Code, seleccionar un kernel de Python y ejecutar:

```bash
pip install -r requirements.txt
```

## 📂 Estructura del Proyecto

```bash
.
├── Proyecto1.ipynb           # Notebook principal con toda la lógica de limpieza
├── data/                     # Archivos de entrada (CSV, TXT, datasets previos)
├── docs/                     # Documentación auxiliar del proyecto
├── reportes/                 # Se genera tras ejecutar el notebook
├── cache/                    # Se genera tras ejecutar el notebook
├── zips/                     # Archivos TXT originales del Ministerio
├── requirements.txt
└── flake.nix / flake.lock    # Archivos para entorno reproducible con Nix
```

## ⚙️ Notas Importantes

* Al ejecutar el notebook por primera vez, se crean automáticamente las carpetas `cache/` y `reportes/`.
* En el archivo `cache/links_cache.txt` se guarda el resultado del proceso de web scraping.
  Si **no deseas ejecutar el scraping**, puedes crear manualmente la carpeta `cache/` y colocar dentro un archivo vacío llamado `links_cache.txt`. Esto forzará al programa a omitir esa parte y pasar directamente a procesar los archivos en `zips/`.
* Existen **banderas booleanas** dentro del notebook para controlar qué se ejecuta y qué se omite. Puedes ajustarlas según tu necesidad.

## 📊 Salidas del Proyecto

Al finalizar la ejecución del notebook, se generará:

* `data/data_clean_vX.csv`: versiones intermedias del dataset limpio.
* `data/data_unified.csv`: dataset final unificado.
* `reportes/`: reportes de validación, errores, agrupaciones, y tipos de establecimientos.
* `data_clean.csv`: data limpiada a utilizar.
