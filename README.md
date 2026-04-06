# Estructuras de Datos — Universidad de Antioquia
### Ingeniería de Sistemas | Curso: Estructuras de Datos y Laboratorio

Este repositorio contiene los trabajos y problemas propuestos desarrollados para la asignatura de 
Estructuras de Datos y su laboratorio. Las soluciones fueron desarrolladas de forma autónoma, 
haciendo uso de diversas herramientas de apoyo como asistentes de inteligencia artificial, 
demostrando no solo la capacidad de resolver los problemas sino también la de utilizar 
eficientemente las herramientas disponibles en el entorno tecnológico actual.

---

## Contenido del repositorio

### 📓 Ejercicio_arbol_de_merkel.ipynb
Implementación del **Árbol de Merkle**, estructura utilizada en blockchain y verificación de 
integridad de datos. El cuaderno contiene dos versiones:
- **Versión a fuerza bruta:** implementación directa con concatenaciones y hashes manuales paso a paso.
- **Versión refinada:** implementación mediante una clase `node` y una función `tree()` genérica 
que construye el árbol automáticamente para cualquier cantidad de elementos, subiendo nivel por 
nivel hasta obtener el hash raíz.

Ambas versiones utilizan el algoritmo **SHA-256** de la librería `hashlib` para la generación 
de hashes.

---

### 📓 Ejercicio_arbols_ABB_y_B+.ipynb
Implementación y comparación de tres estructuras de datos fundamentales cargadas con 10,000 
registros de estudiantes generados aleatoriamente:

- **Lista Doblemente Ligada:** cada nodo almacena un diccionario con `id`, `nombre` y `promedio`, 
con punteros al nodo anterior y siguiente.
- **Árbol Binario de Búsqueda (ABB):** árbol donde cada nodo cumple que su hijo izquierdo tiene 
ID menor y el derecho ID mayor. Se incluye la variante con datos ordenados, que produce el 
caso degenerado (árbol lineal).
- **Árbol B+:** árbol balanceado de orden 100 donde todos los datos residen únicamente en las 
hojas, enlazadas entre sí para facilitar el recorrido secuencial.

Cada estructura tiene dos variantes: una con los datos en el orden original del archivo 
y otra con los datos preordenados por ID. El cuaderno incluye un **menú interactivo** con las 
siguientes operaciones medidas y comparadas entre las 6 estructuras:

| Operación | Descripción |
|-----------|-------------|
| Buscar | Búsqueda por ID en las 6 estructuras |
| Insertar | Inserción de un nuevo estudiante generado aleatoriamente |
| Listar | Recorrido completo ordenado por ID |
| Prueba de rendimiento | Ejecución de 100, 1000, 2000 o 4000 búsquedas aleatorias para obtener el tiempo promedio por estructura |

---

### 📓 Matriz_100k.ipynb
Generación y lectura de una matriz binaria de 100,000 × 100,000 celdas almacenada en un 
archivo `.bin`. El cuaderno contiene:

- **Generador:** crea el archivo `matriz_100k_byte.bin` escribiendo la matriz por bloques de 
100 filas para no saturar la memoria RAM, con un patrón de bytes alternando 0 y 1.
- **Verificador:** lee y muestra los primeros bytes del archivo en formato hexadecimal, 
confirmando que la escritura fue correcta. Incluye manejo de errores para archivo no encontrado 
u otros problemas de lectura.

> ⚠️ El archivo generado pesa aproximadamente **10 GB** (100,000 × 100,000 bytes). 
> No está incluido en el repositorio.

---

### 🖼️ Entidad_relación_-_Estructuras.png
Diagrama entidad-relación desarrollado como ejercicio en clase, que modela un sistema 
hospitalario con las siguientes entidades:

- **Sala** (`#nombre`, `*número de camas`)
- **Paciente** (`#número de registro`, `*nombre`)
- **Personal** (`#número de empleado`, `*nombre`, `*dirección`, `*teléfono`)

Las relaciones modeladas son: una sala **trata** pacientes y una sala **emplea** personal.
El símbolo `#` indica llave primaria y `*` indica atributo obligatorio.

---

### 📓 Laboratorio_1_Hashes_y_Merkel.ipynb
Este cuaderno contiene dos problemas relacionados con el uso de funciones hash y la estructura de árbol de Merkle, aplicada al análisis de cadenas de texto y la búsqueda de un hash objetivo.

- **Problema 1:** Generación de un hash SHA-256 para una lista aleatoria de números del 0 al 9. El problema incluye una función para "desencriptar" el hash, intentando encontrar el orden original de los números que genera un hash específico a través de intentos aleatorios.
  
- **Problema 2:** Construcción de un **Árbol de Merkle** con un conjunto de cadenas de texto. Este problema incluye la implementación de una clase `node` para representar los nodos del árbol, junto con funciones para concatenar hashes, generar el árbol y buscar el hash raíz. El cuaderno también incluye una función de "desencriptación" para encontrar el orden de las cadenas que genera un hash raíz objetivo.

Ambos problemas utilizan el algoritmo **SHA-256** de la librería `hashlib` para la generación de los hashes.

---

## Tecnologías utilizadas
- **Python 3** con Google Colab como entorno de desarrollo
- Librerías: `random`, `faker`, `hashlib`, `pandas`, `re`, `time`, `os`

---

*Universidad de Antioquia — Ingeniería de Sistemas*
