# Graficación por Computadora: Fundamentos de 2D, Curvas y Fractales

Este repositorio contiene la documentación detallada sobre los principios de la manipulación espacial bidimensional, el modelado de curvas paramétricas, la generación de fractales y la naturaleza de las fuentes tipográficas digitales.

---

## 2.1 y 2.2. Transformaciones Bidimensionales y su Representación Matricial

En la graficación por computadora, la manipulación espacial de objetos bidimensionales se realiza mediante **transformaciones geométricas**. Para optimizar el procesamiento algorítmico, estas se modelan como **transformaciones afines** utilizando coordenadas homogéneas.

### Coordenadas Homogéneas

Permiten representar puntos en el plano `(x, y)` como vectores de tres componentes `(x, y, 1)`.

La ecuación general de transformación se define como:


P' = M · P


Donde:
- `P'` = punto transformado  
- `M` = matriz de transformación  
- `P` = punto original  

---

### 2.1.1. Traslación

Consiste en mover un objeto mediante un vector `(tx, ty)`.


| x' | | 1 0 tx | | x |
| y' | = | 0 1 ty | · | y |
| 1 | | 0 0 1 | | 1 |


---

### 2.1.2. Escalamiento

Modifica el tamaño del objeto con factores `sx` y `sy`.


| x' | | sx 0 0 | | x |
| y' | = | 0 sy 0 | · | y |
| 1 | | 0 0 1 | | 1 |


- Si `s > 1` → agranda  
- Si `0 < s < 1` → reduce  
- Si `s < 0` → refleja  

---

### 2.1.3. Rotación

Rota un objeto un ángulo `θ` (antihorario).


| x' | | cosθ -sinθ 0 | | x |
| y' | = | sinθ cosθ 0 | · | y |
| 1 | | 0 0 1 | | 1 |


---

### 2.1.4. Sesgado (Shearing)

Deforma el objeto desplazando sus puntos proporcionalmente.


| x' | | 1 Shx 0 | | x |
| y' | = | 0 1 0 | · | y |
| 1 | | 0 0 1 | | 1 |


---

## 2.3. Trazo de Líneas Curvas

Las curvas se representan mediante ecuaciones paramétricas:


x = f(t)
y = g(t)
0 ≤ t ≤ 1


---

### 2.3.1. Curvas de Bézier


P(t) = Σ (n sobre i) (1 - t)^(n-i) t^i Pi


Características:
- Pasa por el primer y último punto
- Control global
- Usa polinomios de Bernstein

---

### 2.3.2. Curvas B-Spline

Características:
- Control local
- Mayor suavidad
- No necesariamente pasa por todos los puntos

---

## 2.4. Fractales

Se generan mediante iteraciones matemáticas:


z(n+1) = z(n)^2 + c


Ejemplos:
- Conjunto de Mandelbrot
- Conjunto de Julia

---

## 2.5. Uso y Creación de Fuentes de Texto

Las fuentes (`.ttf`, `.otf`) son gráficos vectoriales.

Características:
- Basadas en curvas Bézier
- Escalables sin perder calidad
- Aplican transformaciones matriciales

---

## Referencias Bibliográficas (Formato APA)

 
- Foley, J. D., et al. (1995). *Computer graphics: Principles and practice*. Addison-Wesley  
- Hearn, D., et al. (2014). *Computer graphics with OpenGL*. Pearson  
- Shirley, P., & Marschner, S. (2009). *Fundamentals of computer graphics*. CRC Press 
