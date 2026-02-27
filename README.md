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

Para validar los resultados manuales, se implementó el cálculo de la convolución en Python. Se utilizó la librería **NumPy** para manipular las señales como arreglos y verificar la precisión del cálculo.ñ

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

