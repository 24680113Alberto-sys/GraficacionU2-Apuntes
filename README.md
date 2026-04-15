# Graficación por Computadora: Fundamentos de 2D, Curvas y Fractales

Este repositorio contiene la documentación detallada sobre los principios de la manipulación espacial bidimensional, el modelado de curvas paramétricas, la generación de fractales y la naturaleza de las fuentes tipográficas digitales.

---

## 2.1 y 2.2. Transformaciones Bidimensionales y su Representación Matricial

En la graficación por computadora, la manipulación espacial de objetos bidimensionales se realiza mediante **transformaciones geométricas**. Para optimizar el procesamiento algorítmico, estas se modelan como **transformaciones afines** utilizando coordenadas homogéneas.

### Coordenadas Homogéneas
Permiten representar puntos en el plano $(x, y)$ como vectores de tres componentes $(x, y, 1)$. Esto es fundamental computacionalmente, ya que permite unificar operaciones que normalmente requerirían adición (como la traslación) en operaciones exclusivas de **multiplicación de matrices**, facilitando el cálculo en el hardware gráfico.

La ecuación general de transformación se define como:
$$P' = M \cdot P$$
Donde $P'$ es el nuevo punto, $M$ es la matriz de transformación y $P$ es el punto original.

### 2.1.1. Traslación
Consiste en reposicionar un objeto a lo largo de una trayectoria recta de una coordenada a otra. Se le suma un vector de traslación $(t_x, t_y)$ a las coordenadas originales.
* **Matriz de transformación:**
$$\begin{bmatrix} x' \\ y' \\ 1 \end{bmatrix} = \begin{bmatrix} 1 & 0 & t_x \\ 0 & 1 & t_y \\ 0 & 0 & 1 \end{bmatrix} \begin{bmatrix} x \\ y \\ 1 \end{bmatrix}$$

### 2.1.2. Escalamiento
Altera el tamaño de un objeto multiplicando sus coordenadas por factores de escala $s_x$ y $s_y$.
* **Comportamiento:** Si $s > 1$, el objeto aumenta; si $0 < s < 1$, se reduce. Factores negativos producen una reflexión.
* **Matriz de transformación:**
$$\begin{bmatrix} x' \\ y' \\ 1 \end{bmatrix} = \begin{bmatrix} s_x & 0 & 0 \\ 0 & s_y & 0 \\ 0 & 0 & 1 \end{bmatrix} \begin{bmatrix} x \\ y \\ 1 \end{bmatrix}$$

### 2.1.3. Rotación
Gira un objeto un ángulo $\theta$ alrededor del origen. La convención indica que ángulos positivos producen rotaciones en sentido **antihorario**.
* **Matriz de transformación:**
$$
\begin{bmatrix} 
x' \\ 
y' \\ 
1 
\end{bmatrix} 
= 
\begin{bmatrix} 
\cos(\theta) & -\sin(\theta) & 0 \\ 
\sin(\theta) & \cos(\theta) & 0 \\ 
0 & 0 & 1 
\end{bmatrix} 
\begin{bmatrix} 
x \\ 
y \\ 
1 
\end{bmatrix}
$$

### 2.1.4. Sesgado (Shearing)
Distorsiona la forma de un objeto deslizando sus capas internas de manera proporcional a su distancia a un eje. Un sesgado en el eje $X$ dependiente de $y$ (con factor $Sh_x$) se representa como:
$$\begin{bmatrix} x' \\ y' \\ 1 \end{bmatrix} = \begin{bmatrix} 1 & Sh_x & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix} \begin{bmatrix} x \\ y \\ 1 \end{bmatrix}$$

---

## 2.3. Trazo de Líneas Curvas

El dibujo de curvas en gráficos computacionales utiliza **ecuaciones paramétricas**, donde $x$ e $y$ se definen en función de un parámetro variable $t$, generalmente normalizado en el intervalo $0 \leq t \leq 1$.

### 2.3.1. Curvas de Bézier
Son polinomios paramétricos definidos por un conjunto de puntos de control. La curva pasa exactamente por el primer y último punto (anclaje), mientras que los intermedios (manejadores) atraen la curva hacia ellos.

* **Definición Matemática (Polinomios de Bernstein):**
$$P(t) = \sum_{i=0}^{n} \binom{n}{i} (1-t)^{n-i} t^i P_i \quad \text{para} \quad 0 \leq t \leq 1$$
* **Nota:** Una desventaja es que mover un solo punto altera la forma de toda la curva (**control global**).

### 2.3.2. Curvas B-spline (Basis Spline)
Resuelven el problema del control global construyendo la curva mediante múltiples segmentos polinomiales de menor grado.
* **Control Local:** Modificar un punto solo afecta a un segmento específico.
* **Continuidad:** No tiene que interpolar todos sus puntos de control, produciendo trazos más continuos y suaves bajo la derivación.

---

## 2.4. Fractales

Estructuras geométricas con **autosimilitud** (se repiten a diferentes escalas) y dimensión fraccional. Se dibujan mediante algoritmos iterativos o recursivos.

En graficación 2D, fractales como el **Conjunto de Mandelbrot** o **Julia** se calculan iterando funciones en el plano complejo:
$$z_{n+1} = z_n^2 + c$$

El renderizado evalúa para cada píxel cuántas iteraciones toma para que la magnitud $|z|$ exceda un límite (divergencia), asignando colores basados en dicho conteo.

---

## 2.5. Uso y Creación de Fuentes de Texto

Las fuentes tipográficas (TrueType `.ttf` u OpenType `.otf`) no son mapas de bits, sino **gráficos vectoriales**.

* **Composición:** Cada carácter (glifo) es un contorno cerrado de líneas rectas y curvas paramétricas (Bézier cuadráticas o cúbicas).
* **Renderizado:** El motor interpreta los vértices y aplica triangulación o rasterización para rellenar el contorno.
* **Ventaja:** Esto permite aplicar las mismas **transformaciones afines matriciales** (escalado, rotación, sesgado) sin pérdida de resolución ni pixelación.

---

## Referencias Bibliográficas (Formato APA)


* Foley, J. D., van Dam, A., Feiner, S. K., & Hughes, J. F. (1995). *Computer graphics: Principles and practice* (2.ª ed.). Addison-Wesley Professional.
* Hearn, D., Baker, M. P., & Carithers, W. (2014). *Computer graphics with OpenGL* (4.ª ed.). Pearson Education.
* Shirley, P., & Marschner, S. (2009). *Fundamentals of computer graphics* (3.ª ed.). A K Peters / CRC Press.
