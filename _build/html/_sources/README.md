# Bitcoin ARIMA — Jupyter Book

Análisis completo de series de tiempo para BTC-USD usando modelos ARIMA.

## Estructura del proyecto

```
btc_jbook/
├── _config.yml              ← Configuración del Jupyter Book
├── _toc.yml                 ← Tabla de contenidos
├── requirements.txt         ← Dependencias
├── bitcoin_arima_analysis.ipynb  ← Notebook principal (todo el código)
└── content/
    ├── intro.md
    ├── 01_datos.ipynb
    ├── 02_estacionariedad.ipynb
    ├── 03_seleccion_aic.ipynb
    ├── 04_seleccion_bic_hqic.ipynb
    ├── 05_rolling_forecast.ipynb
    ├── 06_direct_forecast.ipynb
    ├── 07_diagnostico_residuales.ipynb
    ├── 08_metricas_error.ipynb
    ├── 09_comparacion_global.ipynb
    └── 10_conclusiones.ipynb
```

## Pasos para construir el libro

### 1. Instalar dependencias
```powershell
pip install -r requirements.txt
pip install jupyter-book
```

### 2. Ejecutar el notebook principal primero
```powershell
jupyter nbconvert --to notebook --execute bitcoin_arima_analysis.ipynb --output bitcoin_arima_analysis_ejecutado.ipynb
```

### 3. Construir el libro HTML
```powershell
jb build .
```

El libro se genera en la carpeta `_build/html/`.

### 4. Abrir en navegador
```powershell
start _build/html/index.html
```

### 5. (Opcional) Publicar en GitHub Pages
```powershell
pip install ghp-import
ghp-import -n -p -f _build/html
```

## Compartir sin construir

Si solo quieres compartir el notebook directamente:
- Sube `bitcoin_arima_analysis.ipynb` a **Google Colab** o **nbviewer.org**
- En nbviewer: ve a https://nbviewer.org y pega la URL del archivo

## Notas importantes

- `execute_notebooks: off` en `_config.yml` — el libro usa los outputs ya guardados en los notebooks. 
  Asegúrate de ejecutar los notebooks antes de construir el libro.
- Las figuras se guardan automáticamente en el directorio de trabajo al ejecutar el notebook.
