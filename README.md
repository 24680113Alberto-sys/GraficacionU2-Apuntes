# Unidad 2: Graficación 2D
# 2.1 Transformaciones Bidimensionales
2.2 Representación Matricial

En la graficación por computadora, la manipulación espacial de objetos bidimensionales se realiza mediante transformaciones geométricas. Para optimizar el procesamiento, estas se modelan como transformaciones afines utilizando coordenadas homogéneas.

Las coordenadas homogéneas permiten representar un punto 2D (x, y) como un vector:

(𝑥,𝑦,1)(x,y,1)

Esto permite unificar operaciones (como la traslación) en multiplicaciones de matrices, facilitando su implementación en hardware gráfico.

 Ecuación general de transformación

𝑃′=M⋅P

Donde:

P' → punto transformado
M → matriz de transformación
P → punto original

# 2.1.1 Traslación

La traslación consiste en mover un objeto a una nueva posición mediante un vector (t_x, t_y).

[𝑥′𝑦′1]=[1
	0
	𝑡𝑥
	0
	1
	𝑡𝑦
	0	0
	1][𝑥𝑦1]
	​

x
′
y
′
1
	​

	​

=
	​

1
0
0
	​

0
1
0
	​

t
x
	​

t
y
	​

1
	​

	​

	​

x
y
1
	​

	​


# 2.1.2 Escalamiento

Modifica el tamaño de un objeto mediante factores de escala $s_x$ y $s_y$.

$s > 1$ → agranda
$0 < s < 1$ → reduce
$s < 0$ → refleja

[
𝑥
′


𝑦
′


1
]
=
[
𝑠
𝑥
	
0
	
0


0
	
𝑠
𝑦
	
0


0
	
0
	
1
]
[
𝑥


𝑦


1
]
	​

x
′
y
′
1
	​

	​

=
	​

s
x
	​

0
0
	​

0
s
y
	​

0
	​

0
0
1
	​

	​

	​

x
y
1
	​

	​


# 2.1.3 Rotación

Permite girar un objeto un ángulo $\theta$ respecto al origen.

Sentido positivo → antihorario

[
𝑥
′


𝑦
′


1
]
=
[
cos
⁡
(
𝜃
)
	
−
sin
⁡
(
𝜃
)
	
0


sin
⁡
(
𝜃
)
	
cos
⁡
(
𝜃
)
	
0


0
	
0
	
1
]
[
𝑥


𝑦


1
]
	​

x
′
y
′
1
	​

	​

=
	​

cos(θ)
sin(θ)
0
	​

−sin(θ)
cos(θ)
0
	​

0
0
1
	​

	​

	​

x
y
1
	​

	​


# 2.1.4 Sesgado (Shearing)

Distorsiona un objeto desplazando sus puntos proporcionalmente.

Ejemplo: sesgado en el eje $X$

[
𝑥
′


𝑦
′


1
]
=
[
1
	
𝑆
ℎ
𝑥
	
0


0
	
1
	
0


0
	
0
	
1
]
[
𝑥


𝑦


1
]
	​

x
′
y
′
1
	​

	​

=
	​

1
0
0
	​

Sh
x
	​

1
0
	​

0
0
1
	​

	​

	​

x
y
1
	​

	​


#  2.3 Trazo de Líneas Curvas

Las curvas en gráficos computacionales se representan mediante ecuaciones paramétricas:

$x = f(t)$
$y = f(t)$
$0 \leq t \leq 1$
2.3.1 Curvas de Bézier

Son curvas paramétricas definidas por puntos de control.

Características:

Pasan por el primer y último punto
Los puntos intermedios controlan la forma
Presentan control global
 Ecuación general

𝑃
(
𝑡
)
=
∑
𝑖
=
0
𝑛
(
𝑛
𝑖
)
(
1
−
𝑡
)
𝑛
−
𝑖
𝑡
𝑖
𝑃
𝑖
P(t)=∑
i=0
n
	​

(
i
n
	​

)(1−t)
n−i
t
i
P
i
	​


# 2.3.2 Curvas B-Spline

Mejoran a Bézier mediante:

Control local (modificar un punto no afecta toda la curva)
Mayor suavidad
No necesariamente pasan por los puntos de control
 # 2.4 Fractales

Los fractales son estructuras con:

Autosimilitud
Dimensión fraccional

Se generan mediante algoritmos iterativos.

 Fórmula base (Mandelbrot / Julia)

𝑧
𝑛
+
1
=
𝑧
𝑛
2
+
𝑐
z
n+1
	​

=z
n
2
	​

+c

Proceso:

Cada píxel representa un valor de $c$
Se itera la ecuación
Se evalúa si $|z|$ diverge
Se asigna color según iteraciones
# 2.5 Uso y Creación de Fuentes de Texto

Las fuentes digitales (TTF, OTF) son gráficos vectoriales, no mapas de bits.

Características:

Formadas por curvas (Bézier)
Escalables sin pérdida de calidad
Se transforman con matrices (rotación, escalado, etc.)
 Proceso de renderizado
Interpretación de vértices
Construcción de contornos
Triangulación
Rasterización
#  Referencias (Formato APA)
Blender Foundation. (2024). Blender 4.0 Python API Documentation.
https://docs.blender.org/api/current/
Foley, J. D., van Dam, A., Feiner, S. K., & Hughes, J. F. (1995).
Computer graphics: Principles and practice (2.ª ed.). Addison-Wesley.
Hearn, D., Baker, M. P., & Carithers, W. (2014).
Computer graphics with OpenGL (4.ª ed.). Pearson.
Shirley, P., & Marschner, S. (2009).
Fundamentals of computer graphics (3.ª ed.). CRC Press.


