# Tarea: Mi prompt avanzado

## Tarea elegida

Disenar las clases de un sistema de prestamo de libros para una biblioteca municipal de Arequipa.

## Version 1: prompt basico

```text
Disena las clases de un sistema de biblioteca.
```

- **Tecnica agregada:** ninguna (zero-shot).
- **Por que:** es el punto de partida para comparar.
- **Que mejoro:** nada todavia. La respuesta fue generica: lista de clases sin tipos de dato ni reglas de la biblioteca.

## Version 2

```text
Actua como arquitecto de software Java que disena sistemas para bibliotecas municipales.
Disena las clases de un sistema de prestamo de libros para una biblioteca de Arequipa.
Responde en una tabla con columnas: clase, atributos, tipo de dato.
```

- **Tecnica agregada:** role prompting y formato definido.
- **Por que:** queria un enfoque tecnico y una tabla facil de revisar.
- **Que mejoro:** salio en tabla con tipos de dato (String, int, LocalDate). Faltaron reglas como el limite de libros y la multa.

## Version 3: prompt final

```text
<rol>Actua como arquitecto de software Java que disena sistemas para bibliotecas municipales.</rol>
<contexto>Biblioteca de Arequipa. Cada socio puede llevar maximo 3 libros por 7 dias. Si devuelve tarde, paga multa por dia de retraso.</contexto>
<tarea>Piensa paso a paso que clases hacen falta y como se relacionan. Luego revisa tu diseno, agrega lo que falte e indica que agregaste.</tarea>
<formato>Tabla con columnas: clase, atributos con tipo de dato, relaciones con otras clases.</formato>
```

- **Tecnicas agregadas:** prompt estructurado, chain of thought y autocritica.
- **Por que:** las etiquetas separan las reglas, "paso a paso" ordena el diseno y la autocritica detecta lo que falta.
- **Que mejoro:** incluyo la clase Prestamo con fecha limite y multa, las relaciones entre clases e indico que agrego (por ejemplo, la clase Multa).

## Tecnicas usadas en el prompt final

| Parte del prompt | Tecnica |
|---|---|
| `<rol>` arquitecto de software Java | Role prompting |
| Etiquetas `<rol>`, `<contexto>`, `<tarea>`, `<formato>` | Prompt estructurado |
| "Piensa paso a paso que clases hacen falta" | Chain of thought |
| "Revisa tu diseno, agrega lo que falte" | Autocritica |

## Evaluacion del resultado

| Criterio | Cumple (Si/No) |
|---|---|
| Tiene las 3 columnas pedidas | Si |
| Incluye la regla de 3 libros por 7 dias | Si |
| Incluye la multa por retraso | Si |
| Indica que agrego en la autocritica | Si |
| No hay clases repetidas o sin sentido | Si |

## Por que elegi estas tecnicas

Elegi role prompting porque queria el enfoque de un arquitecto Java y no una respuesta general. Use un prompt estructurado para que el contexto con las reglas, la tarea y el formato no se mezclaran. Agregue chain of thought para que la IA razonara que clases hacen falta antes de listarlas, y autocritica para que completara lo que olvido. No use few-shot porque la tabla ya estaba definida en el prompt. Tampoco use descomposicion porque el diseno era lo bastante pequeno para resolverlo en un solo pedido.