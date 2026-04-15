#  Proyecto: Graficación 2D en Blender

##  Descripción

Este repositorio contiene la implementación de conceptos fundamentales de **Graficación 2D** utilizando **Blender y Python (bpy)**. Está diseñado como material académico para la Unidad 2.

---

##  Estructura del Proyecto

```
Graficacion2D-Blender/
│
├── README.md
├── requirements.txt
├── src/
│   ├── transformaciones/
│   │   ├── traslacion.py
│   │   ├── escalamiento.py
│   │   ├── rotacion.py
│   │   └── sesgado.py
│   │
│   ├── matrices/
│   │   └── transformaciones_matriciales.py
│   │
│   ├── curvas/
│   │   ├── bezier.py
│   │   └── bspline.py
│   │
│   ├── fractales/
│   │   └── fractal.py
│   │
│   ├── fuentes/
│   │   └── texto.py
│   │
│   └── control/
│       └── control_teclas.py
│

```

---

#  Instalación

1. Descargar e instalar Blender
2. Clonar el repositorio:

```bash
git clone https://github.com/tu_usuario/graficacion2d-blender.git
cd graficacion2d-blender
```

3. Ejecutar scripts en Blender:

* Ir a "Scripting"
* Abrir archivo .py
* Ejecutar

---

#  Contenido

## 2.1 Transformaciones Bidimensionales

###  Traslación

```python
import bpy

obj = bpy.context.active_object
obj.location.x += 2
obj.location.y += 1
```

###  Escalamiento

```python
obj.scale.x *= 2
obj.scale.y *= 2
```

###  Rotación

```python
import math
obj.rotation_euler[2] += math.radians(45)
```

###  Sesgado (Shear)

```python
import bmesh
import mathutils

obj = bpy.context.active_object
mesh = obj.data
bm = bmesh.new()
bm.from_mesh(mesh)

for v in bm.verts:
    v.co.x += v.co.y * 0.5

bm.to_mesh(mesh)
bm.free()
```

---

## 2.2 Representación Matricial

```python
import mathutils

traslacion = mathutils.Matrix.Translation((2, 1, 0))
rotacion = mathutils.Matrix.Rotation(1.57, 4, 'Z')
escala = mathutils.Matrix.Scale(2, 4)

transformacion = traslacion @ rotacion @ escala

obj.matrix_world = transformacion
```

---

##  Control con teclas

```python
import bpy

class MoverObjeto(bpy.types.Operator):
    bl_idname = "wm.mover_objeto"
    bl_label = "Mover Objeto"

    def modal(self, context, event):
        obj = context.object

        if event.type == 'LEFT_ARROW':
            obj.location.x -= 0.1
        elif event.type == 'RIGHT_ARROW':
            obj.location.x += 0.1

        return {'RUNNING_MODAL'}

    def invoke(self, context, event):
        context.window_manager.modal_handler_add(self)
        return {'RUNNING_MODAL'}

bpy.utils.register_class(MoverObjeto)
```

---

## 2.3 Curvas

###  Bézier

```python
import bpy

bpy.ops.curve.primitive_bezier_curve_add()
```

###  B-Spline

```python
bpy.ops.curve.primitive_nurbs_curve_add()
```

---

## 2.4 Fractales

```python
import bpy

def fractal(x, y, size, depth):
    if depth == 0:
        return

    bpy.ops.mesh.primitive_plane_add(size=size, location=(x,y,0))

    fractal(x+size, y, size/2, depth-1)
    fractal(x-size, y, size/2, depth-1)

fractal(0,0,2,3)
```

---

## 2.5 Texto y Fuentes

```python
import bpy

bpy.ops.object.text_add()
obj = bpy.context.object
obj.data.body = "Hola Mundo"
```


