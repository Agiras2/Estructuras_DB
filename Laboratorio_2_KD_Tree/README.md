# 📍 KD-Tree vs. Fuerza Bruta: Análisis de Búsqueda Espacial Geográfica

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg?style=flat-square&logo=python)
![Math](https://img.shields.io/badge/Calculus-Haversine-red.svg?style=flat-square)
![Location](https://img.shields.io/badge/Region-Valle_de_Aburrá-orange?style=flat-square)

## 🧠 Descripción del Proyecto
Este proyecto implementa y compara dos enfoques algorítmicos para resolver problemas críticos de búsqueda espacial en 2D, utilizando coordenadas geográficas reales (latitud y longitud). El objetivo es medir la eficiencia del **KD-Tree** frente a una **Fuerza Bruta Optimizada** en entornos de alta precisión.

### Problemas Resueltos:
* 🔵 **Búsqueda por Radio:** Localizar todos los puntos dentro de un umbral de distancia.
* 🔴 **Vecino más Cercano (Nearest Neighbor):** Identificar el punto más próximo a una consulta específica.

---

## 📂 Estructura del Software
El sistema se divide en dos módulos principales:

1.  **`KD_Tree.py`**: Motor de datos.
    * Generación de datasets aleatorios.
    * Implementación de estructuras: `LinkedList` y `Node_KD_2D`.
    * Lógica de construcción recursiva del árbol.
2.  **`Lab2_2_KD_Tree.py`**: Capa de aplicación y análisis.
    * Algoritmos de búsqueda y poda espacial.
    * Visualización avanzada con `matplotlib`.
    * Benchmarking y dashboard interactivo con `ipywidgets`.

---

## 🌳 Arquitectura del KD-Tree
El árbol se construye mediante una partición binaria del espacio, alternando los ejes según el nivel de profundidad.

### Notas sobre Coordenadas
Para mantener la coherencia matemática con el plano cartesiano:
* **Latitud ($\phi$):** Corresponde al **Eje Y** (Cortes en niveles pares).
* **Longitud ($\lambda$):** Corresponde al **Eje X** (Cortes en niveles impares).

> [!TIP]
> **Construcción Eficiente:** Se utiliza la **mediana** de los puntos en cada nivel para asegurar un árbol balanceado, garantizando una profundidad de $O(\log n)$.

---

## 🔍 Algoritmos y Estrategias de Poda

### 1. Búsqueda por Radio
* **Fuerza Bruta:** Filtra candidatos mediante una "caja delimitadora" antes de aplicar la costosa fórmula de Haversine.
* **KD-Tree:** Explora la rama más prometedora y solo accede a la rama opuesta si el radio de búsqueda interseca el plano de división del nodo actual.

### 2. Vecino más Cercano
* **KD-Tree:** Mantiene un registro del "mejor candidato hasta ahora". Utiliza una estrategia de **poda por distancia**, descartando subárboles donde es matemáticamente imposible encontrar un punto más cercano.

### ⚙️ Optimización de Unidades
Para acelerar la poda, convertimos distancias angulares a métricas locales:
* $1^\circ \text{ lat} \approx 111,320 \text{ m}$
* $1^\circ \text{ lon} \approx 111,320 \times \cos(\text{lat}) \text{ m}$

---

## 📊 Benchmarking y Rendimiento
Se realizaron pruebas de estrés con **1,000 iteraciones** y re-randomización constante en el área del Valle de Aburrá.

### 🔵 Búsqueda por Radio
| Métrica | Lista Ligada (FB) | KD-Tree |
| :--- | :---: | :---: |
| **Tiempo Medio** | $1.8994 \text{ ms}$ | $0.0420 \text{ ms}$ |
| **Tiempo Máximo** | $8.2068 \text{ ms}$ | $0.1294 \text{ ms}$ |
| **Speedup** | --- | **45.17x** |

**Análisis:** El KD-Tree es drásticamente más rápido. Aunque visita más nodos (debido a la estructura del árbol), evita el cálculo de Haversine en el 95% de los datos.

### 🔴 Vecino más Cercano
| Métrica | Lista Ligada (FB) | KD-Tree |
| :--- | :---: | :---: |
| **Tiempo Medio** | $0.3934 \text{ ms}$ | $0.0166 \text{ ms}$ |
| **Speedup** | --- | **23.75x** |

---

## 🧪 Visualización e Interfaz
El proyecto incluye una herramienta interactiva que permite:
* **Visualizar Particiones:** Ver cómo el KD-Tree segmenta el mapa de Medellín y sus alrededores.
* **Zoom Dinámico:** Inspeccionar el comportamiento del árbol en áreas densas.
* **Métricas en Vivo:** Comparativas inmediatas de tiempo y operaciones.

---

## ⚖️ Complejidad Computacional
| Algoritmo | Caso Promedio | Peor Caso |
| :--- | :---: | :---: |
| **Fuerza Bruta** | $O(n)$ | $O(n)$ |
| **KD-Tree** | $O(\log n)$ | $O(n)$ |

> [!WARNING]
> En distribuciones **no homogéneas** (clústeres muy densos en un solo punto), el KD-Tree puede perder eficiencia y aproximarse a un comportamiento lineal.

---

## 🔥 Conclusión Experimental
Los resultados demuestran que el **KD-Tree supera significativamente** a la fuerza bruta en aplicaciones geográficas. Su capacidad para podar regiones enteras del espacio lo convierte en la estructura ideal para sistemas de mapas, logística y servicios basados en localización (LBS).

---
**👨‍💻 Autor:** *Andrés Giraldo Arismendy - Con asistencia de Claude AI, desarrollado por Antrophic.*
