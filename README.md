# Caminata aleatoria con un dado de cuatro caras

Tarea de **Probabilidad y Estadística**. Se simula en Python una caminata aleatoria en dos dimensiones controlada por un dado de cuatro caras ligado a la rosa de los vientos, y se analiza la distribución de la distancia final al origen mediante un histograma de frecuencias.

## Planteamiento

Cada cara del dado indica una dirección. En cada tiro se avanza **siempre una unidad** en esa dirección:

| Cara del dado | Dirección | Movimiento |
|:---:|:---:|:---:|
| 1 | Norte | (0, +1) |
| 2 | Oeste | (−1, 0) |
| 3 | Sur | (0, −1) |
| 4 | Este | (+1, 0) |

1. Se parte del origen (0, 0) y se tira el dado **10,000 veces** (una caminata).
2. Al terminar, se mide la distancia euclidiana del origen al punto final: d = √(x² + y²).
3. El experimento se repite **1,000 veces** y cada distancia se guarda.
4. Con todas las distancias se construye un histograma de frecuencias.

## Contenido del repositorio

| Archivo | Descripción |
|---|---|
| `caminatas.ipynb` | Cuaderno de Google Colab con la simulación y el histograma |
| `README.md` | Este documento |

## Cómo ejecutarlo

**En Google Colab:** abre `caminatas.ipynb` desde GitHub con el botón *Open in Colab* y ve a *Entorno de ejecución → Ejecutar todo*. No requiere instalar nada.

## Estructura del cuaderno

| Celda | Qué hace |
|---|---|
| 1. Librerías | Importa NumPy y Matplotlib |
| 2. Parámetros | Define `PASOS` (tiros por caminata) y `CAMINATAS` (repeticiones) |
| 3. Simulación | Tira el dado, calcula la posición final y guarda la distancia de cada caminata |
| 4. Histograma | Grafica la frecuencia de las distancias y marca el promedio con una línea roja punteada |

Para experimentar, cambia los valores de la celda 2 y vuelve a ejecutar las celdas 2, 3 y 4.

### Cálculo de la posición

En lugar de mover el punto paso a paso, se cuentan las caras de los 10,000 tiros:

```python
x = (número de 4) − (número de 2)   # Este − Oeste
y = (número de 1) − (número de 3)   # Norte − Sur
```

## Resultados

Con 1,000 caminatas de 10,000 pasos se obtuvo:

| Estadístico | Simulación | Teoría |
|---|:---:|:---:|
| Distancia promedio | 86.21 | ≈ 88.6 |
| Desviación estándar | 45.98 | ≈ 46.3 |

*Los valores de la simulación cambian ligeramente en cada ejecución por ser aleatorios.*

### Interpretación del histograma

- Ninguna distancia es negativa y muy pocas caminatas terminan cerca del origen.
- La mayoría de las caminatas termina entre 50 y 85 unidades del origen.
- La distribución tiene una **cola larga hacia la derecha**: unas pocas caminatas se alejan más de 200 unidades.
- La línea roja punteada (el promedio) queda un poco a la derecha del pico, porque la cola jala el promedio hacia arriba.

Los resultados de la simulación coinciden con estos valores teóricos, lo que valida el modelo.

## Tecnologías

- Python 3
- NumPy
- Matplotlib
- Google Colab
