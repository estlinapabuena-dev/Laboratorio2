# Laboratorio2
**Universidad Militar Nueva Granada**  
**Asignatura:** Procesamiento Digital de Señales  
**Estudiantes:** [Lina Marcela Pabuena,Ralf Steven Castiblanco Solano ]  
**Fecha:** Febrero 2026 
**Asignatura:** Procesamiento Digital de Señales  
**Título de la práctica:** Convolución, correlación y transformada de Fourier

## Objetivos
- Comprender la convolución como una operación que permite obtener la respuesta de un sistema discreto ante una entrada determinada.
- Analizar la correlación como medida de similitud entre dos señales.
- Aplicar la Transformada de Fourier como herramienta de análisis en el dominio de la frecuencia.

# PARTE A

## Resumen

Este repositorio documenta la primera fase de un laboratorio enfocado en el procesamiento de señales discretas. El objetivo principal fue calcular la convolución de dos señales, $x[n]$ y $h[n]$, definidas a partir de datos personales (cédula y código estudiantil, respectivamente). El proceso incluyó una **convolución manual**, seguida de una **verificación computacional** utilizando Python.

### 1. Definición de Señales y Convolución Manual

Las señales de entrada, **$x[n]$** y **$h[n]$**, se definieron usando los dígitos de la cédula y el código estudiantil de cada una de las integrantes. La convolución, $y[n] = x[n] * h[n]$, se calculó paso a paso de forma manual, documentando cada operación.

- **Señal $y[n]$**: Lina
  ![conv lina](https://github.com/user-attachments/assets/153582a5-05e7-4d07-b0c3-720d2b422c82)
  
### 2. Representación Gráfica y Secuencial

Se generaron las representaciones gráficas y secuenciales de las señales originales ($x[n]$, $h[n]$) y de la señal resultante ($y[n]$). Este paso se realizó a mano para visualizar el desplazamiento y la superposición de las señales.

- **Gráfica señal $y[n]$**: Lina
  ![conv lina a mano](https://github.com/user-attachments/assets/514129b4-bbf1-4e4d-9e9f-46781c67801a)

### 3. Verificación Computacional con Python

Para validar los resultados manuales, se implementó el cálculo de la convolución en Python. Se utilizó la librería **NumPy** para manipular las señales como arreglos y verificar la precisión del cálculo.

<pre>
# Datos de Lina
x = np.array([1,0,1,1,0,8,2,1,5,0])   # cédula
h = np.array([5,6,0,0,8,2,2])         # código estudiantil

# Gráfica de h[n]
t = np.arange(len(h))
plt.figure(figsize=(8, 4))
plt.stem(t, h)
plt.xlabel('n')
plt.ylabel('h[n]')
plt.title('h[n] Lina')
plt.grid()
plt.show()

# Gráfica de x[n]
t = np.arange(len(x))
plt.figure(figsize=(8, 4))
plt.stem(t, x)
plt.xlabel('n')
plt.ylabel('x[n]')
plt.title('x[n] Lina')
plt.grid()
plt.show()

# Convolución
y = np.convolve(x, h, mode='full')
print("Señal convolución entre h[n] y x[n], Lina:")
print(y)

# Gráfica de y[n]
t = np.arange(len(y))
plt.figure(figsize=(10, 4))
plt.stem(t, y)
plt.xlabel('n')
plt.ylabel('y[n]')
plt.title('Convolución y[n] = x[n] * h[n]')
plt.grid()
plt.show()
</pre> 

## Gráfica Código Estudiantil Lina
<img width="678" height="393" alt="Grafica Codigo estudiantil Lina" src="https://github.com/user-attachments/assets/6fbecc7b-b591-4250-8839-b40a92d5a6e7" />

## Gráfica Cédula Lina
<img width="678" height="393" alt="Grafica cedula lina" src="https://github.com/user-attachments/assets/d56ceb1a-93f1-49ea-afb2-bd100345d890" />

## Gráfica Convolución Lina
<img width="850" height="394" alt="convolución Lina" src="https://github.com/user-attachments/assets/fbcbcc0f-cf23-4089-8a8a-2a91edeaf5a6" />


## PARTE B

##  Resumen
Esta sección del laboratorio se centra en la aplicación de la correlación cruzada entre dos señales discretas, **x₁[nTs]** y **x₂[nTs]**, con el fin de medir su similitud en función de un desplazamiento temporal. El objetivo es determinar la similitud entre ambas señales en función de un desplazamiento temporal. El proceso incluye el cálculo, la representación gráfica del resultado y una discusión sobre la utilidad de esta técnica en el procesamiento digital de señales.

### 1. Definición de Señales
- Señal Cosenoidal
  x1[nTs] = cos(2π * 100 * nTs) = cos(n * π/4)  
- Señal Senoidal
  x2[nTs] = sin(2π * 100 * nTs) = sin(n * π/4)

### 2. Correlación Cruzada
<img width="689" height="393" alt="image" src="https://github.com/user-attachments/assets/8250ec23-9857-4f87-b1a8-dd81d334ff54" />

## Código en Python

```python
import numpy as np
import matplotlib.pyplot as plt

# Parámetros
Ts = 1.25e-3   # periodo de muestreo
n = np.arange(9)  # muestras 0 <= n <= 8
f = 100        # frecuencia 100 Hz

# Señales discretas
x1 = np.cos(2 * np.pi * f * n * Ts)   # x1[n] = cos(2π·100·n·Ts)
x2 = np.sin(2 * np.pi * f * n * Ts)   # x2[n] = sin(2π·100·n·Ts)

# Correlación cruzada
correlacion = np.correlate(x1, x2, mode='full')
print("Correlación cruzada (vector resultado):")
print(correlacion)

# Eje de desplazamientos (lags)
t_corr = np.arange(-len(n) + 1, len(n))

# Gráfica de la correlación cruzada
plt.figure(figsize=(8, 4))
plt.stem(t_corr, correlacion)
plt.axhline(0, color="red")  # línea en y=0 para referencia
plt.xlabel("Desplazamiento")
plt.ylabel("Correlación")
plt.title("Correlación cruzada entre x1[n] y x2[n]")
plt.grid()
plt.show()

## 2. Resultados de Colab

Vector de correlación cruzada (`mode='full'`):

```
[-2.44929360e-16 -7.07106781e-01 -1.50000000e+00 -1.41421356e+00
 -2.54671001e-16  2.12132034e+00  3.50000000e+00  2.82842712e+00
 -2.28847549e-17 -2.82842712e+00 -3.50000000e+00 -2.12132034e+00
  4.55531587e-16  1.41421356e+00  1.50000000e+00  7.07106781e-01
  0.00000000e+00]

La gráfica muestra los valores de correlación cruzada en el rango de desplazamientos `m = -8 … 8`.

## 3 Análisis
El análisis de la correlación cruzada muestra que los valores de Ts y f determinan
directamente el argumento de las funciones seno y coseno, estableciendo una relación
de fase constante entre ambas señales. El eje horizontal de la gráfica representa los
desplazamientos temporales entre −8 y 8 muestras, mientras que el eje vertical indica
la magnitud de la correlación cruzada.

La gráfica presenta una simetría aproximada alrededor del origen, característica de la
correlación entre señales periódicas de igual frecuencia con un desfase constante.
Se observan picos máximos cercanos a 3.5, los cuales indican los desplazamientos donde
la similitud entre ambas señales es mayor.

El valor cercano a cero en el desplazamiento n = 0 refleja la ortogonalidad entre el seno
y el coseno, lo que implica una baja correlación cuando ambas señales están alineadas.
A medida que el desplazamiento aumenta en sentido positivo o negativo, la correlación
disminuye debido a la desalineación progresiva de las señales.

### 4 ¿En qué situaciones resulta útil aplicar la correlación cruzada en el procesamiento digital de señales?
La correlación cruzada es útil en múltiples contextos de procesamiento digital de señales, como:
**Estimación de retardo/desfase** → sincronización de señales, localización de fuentes (radar, sonar, acústica).  
**Detección de patrones o plantillas** (*matched filtering*), útil para encontrar secuencias conocidas en ruido.  
**Comunicaciones digitales** → sincronización de símbolos, detección de preámbulos o códigos de inicio.  
**Señales biomédicas** → análisis de retardo entre ECG y PPG, o entre distintos sensores.  
**Procesamiento de imágenes** → registro y alineación de imágenes desplazadas.  
**Control de calidad** → comparación de señales de vibración o fallas con patrones de referencia.

## PARTE C 

