# Lab 4 - 3D Model Renderer

Renderizador 3D básico en Rust que carga y dibuja modelos OBJ usando rasterización de triángulos.

## Resultado

<img width="631" height="330" alt="image" src="https://github.com/user-attachments/assets/0e03dd8f-3485-4c16-9c25-76777b05497a" />

## Características

- ✅ Carga de modelos OBJ
- ✅ Rasterización de triángulos con algoritmo de coordenadas baricéntricas
- ✅ Z-buffer para manejo de profundidad
- ✅ Iluminación básica (Lambertian shading)
- ✅ Transformaciones 3D (traslación, rotación, escala)
- ✅ Controles interactivos

## Controles

### Movimiento
- `←↑↓→` - Mover el modelo
- `A/S` - Disminuir/Aumentar escala

### Rotación
- `Q/W` - Rotar en eje X
- `E/R` - Rotar en eje Y
- `T/Y` - Rotar en eje Z

### Otros
- `ESC` - Salir

## Estructura del Proyecto

```
src/
├── main.rs          # Lógica principal y loop de renderizado
├── obj.rs           # Cargador de archivos OBJ
├── vertex.rs        # Estructura de vértices
├── framebuffer.rs   # Buffer de píxeles y Z-buffer
├── triangle.rs      # Rasterización de triángulos
├── shaders.rs       # Vertex shader y transformaciones
├── color.rs         # Sistema de colores
├── fragment.rs      # Estructura de fragmentos
└── line.rs          # Algoritmo de línea (Bresenham)
```

## Pipeline de Renderizado

1. **Vertex Shader**: Transforma vértices usando matriz de modelo
2. **Primitive Assembly**: Agrupa vértices en triángulos
3. **Rasterization**: Convierte triángulos en fragmentos usando coordenadas baricéntricas
4. **Fragment Processing**: Aplica iluminación y escribe al framebuffer con Z-testing

## Dependencias

```toml
[dependencies]
nalgebra-glm = "0.18"
minifb = "0.25"
tobj = "4.0"
```

## Compilación y Ejecución

```bash
cd src
cargo build --release
cargo run --release
```

## Detalles Técnicos

### Iluminación
- Modelo de iluminación difusa (Lambert)
- Luz direccional desde `(0, 0, -1)`
- Interpolación de normales para suavizado

### Transformaciones
- Matriz de modelo combina rotación, escala y traslación
- Soporte para rotaciones en los tres ejes (Euler angles)
- División de perspectiva en vertex shader

### Rasterización
- Bounding box para optimización
- Coordenadas baricéntricas para interpolación
- Z-buffer para corrección de visibilidad

## Modelo Utilizado

El modelo `spaceship.obj` fue creado en Blender y exportado en formato Wavefront OBJ.

---

**Autor**: Marinés García 
**Curso**: Gráficas por Computadora  
**Fecha**: Octubre 2025
