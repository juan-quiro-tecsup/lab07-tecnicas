# Bitacora de tecnicas avanzadas

Laboratorio 07: Tecnicas Avanzadas de Prompting.
Nombre: Juan Carlos Quiro Alvaro
Herramienta de IA usada: ChatGPT

## Ejercicio 2: Zero-shot, one-shot y few-shot

| Tipo | Aciertos (de 5) | Formato de la respuesta | Todas con el mismo formato (Si/No) |
|------|-----------------|-------------------------|------------------------------------|
| Zero-shot | 5/5 | Lista numerada con explicación breve de cada comentario | No |
| One-shot | 5/5 | Lista numerada con la etiqueta Positivo, Negativo o Neutral | Si |
| Few-shot | 5/5 | "texto" -> etiqueta, una línea por comentario | Si |

**Comentario:** Zero-shot dio formato libre, con explicaciones. One-shot siguió las etiquetas del ejemplo. Few-shot mantuvo siempre texto etiqueta porque imitó los ejemplos. Los ejemplos fijan el formato, no cambian los aciertos.

## Ejercicio 3: Chain of Thought

| Pedido | Respuesta de la IA | Muestra los pasos (Si/No) | Correcta (Si/No) |
|--------|--------------------|---------------------------|------------------|
| Directo | 318,60 | No | Si |
| Paso a paso | 318,60 | Si | Si |

**Comentario:** Ver los pasos me permite revisar cada cálculo con la calculadora. Si hay un error, sé en qué paso ocurrió, en vez de solo creer un número.

## Ejercicio 4: Role prompting

| Version | Vocabulario (sencillo/tecnico) | Usa ejemplos o codigo | A quien le sirve mas |
|---------|-------------------------------|-----------------------|----------------------|
| A. Sin rol | Intermedio | Ejemplo corto de codigo | Publico general |
| B. Rol docente | Sencillo | Analogia (caja con etiqueta) | Estudiantes que nunca programaron |
| C. Rol senior | Tecnico (tipo de dato, memoria, alcance) | Codigo Java | Companeros desarrolladores |

**Comentario:** El rol cambia el enfoque y el vocabulario, no el conocimiento. El docente usa palabras simples y analogias; el senior usa terminos tecnicos y codigo.

## Ejercicio 5: Descomposicion

- Pedido de una sola vez: respuesta generica y larga, con codigo mezclado sin revisar cada parte.
- Paso 1: lista de 5 requisitos (registrar productos, controlar stock, entradas y salidas, buscar productos, reportes).
- Paso 2: diseno de clases (Producto, Inventario, etc.) con atributos y tipos de dato.
- Paso 3: codigo Java de la clase Producto con atributos, constructor, getters y setters.
- Paso 4: 3 mejoras concretas (validaciones, encapsulamiento, metodo toString, etc.).
- Comparacion: el pedido por pasos fue mas coherente y revisable; el de una sola vez fue mas general.

## Ejercicio 6: Prompt estructurado y autocritica

| Que revisar | Cumple (Si / No) |
|---|---|
| Tiene las 4 columnas pedidas? | Si |
| Incluye el bloqueo despues de 3 intentos? | Si |
| Incluye casos con campos vacios? | Si |
| Indica que casos agrego en la autocritica? | Si |
| Hay algun caso repetido o que no tenga sentido? | No |

**Comentario:** El prompt estructurado dio una tabla clara de 6 casos. La autocritica agrego casos limite (campos vacios, correo sin @, contrasena con espacios). Yo debo revisar el resultado final porque la IA puede dejar casos repetidos o incorrectos.

```text
<rol>Actua como analista de pruebas de software.</rol>
<contexto>Login web con correo y contrasena. La cuenta se bloquea
despues de 3 intentos fallidos.</contexto>
<tarea>Piensa paso a paso que puede fallar y escribe 6 casos de prueba.</tarea>
<formato>Tabla con las columnas: ID, escenario, datos de entrada,
resultado esperado.</formato>

Revisa tu tabla: faltan casos limite como campos vacios, correo sin @
o contrasena con espacios? Agrega los que falten e indica cuales agregaste.
```