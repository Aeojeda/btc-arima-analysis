# Análisis de Series de Tiempo: Futuros de Bitcoin (BTC-USD)

## Modelado ARIMA con criterios AIC, BIC y HQIC

---

Este libro presenta el análisis completo de la serie de tiempo asociada al precio de cierre diario de **Bitcoin (BTC-USD)**, desde su primera cotización disponible hasta la fecha actual, obtenida mediante la API de Yahoo Finance.

### Objetivo

Ajustar modelos **ARIMA** para predecir el precio de Bitcoin con horizontes de predicción de **7, 14, 21 y 28 días**, comparando:

- Predicciones con ventana **rolling** de 1 día
- Predicciones **directas** mediante `forecast()`
- Criterios de selección **AIC**, **BIC** y **HQIC**

### Estructura del análisis

El análisis sigue el flujo canónico **Box-Jenkins**:

```{mermaid}
flowchart LR
    A[Datos BTC-USD\nYahoo Finance] --> B[Estacionariedad\nADF + KPSS]
    B --> C[Selección ARIMA\nAIC / BIC / HQIC]
    C --> D[Diagnóstico\nResiduales]
    D --> E[Predicción\nRolling + Directa]
    E --> F[Evaluación\nMAPE MAE RMSE R²]
    F --> G[Conclusiones]
```

### Horizontes de predicción

```{figure} ../imgs/horizonte_esquema.png
:name: horizonte
:width: 80%
Esquema de partición Train/Test para cada horizonte.
```

| Horizonte | N_train | N_test |
|-----------|---------|--------|
| 7 días    | N − 7   | 7      |
| 14 días   | N − 14  | 14     |
| 21 días   | N − 21  | 21     |
| 28 días   | N − 28  | 28     |

### Métricas de evaluación

$$\text{MAPE} = \frac{1}{h}\sum_{t=1}^{h}\left|\frac{y_t - \hat{y}_t}{y_t}\right| \times 100$$

$$\text{RMSE} = \sqrt{\frac{1}{h}\sum_{t=1}^{h}(y_t - \hat{y}_t)^2}$$

$$R^2 = 1 - \frac{\sum(y_t - \hat{y}_t)^2}{\sum(y_t - \bar{y})^2}$$

---

:::{note}
Todos los resultados fueron obtenidos con datos reales descargados desde Yahoo Finance. El notebook es completamente reproducible ejecutando las celdas en orden.
:::
