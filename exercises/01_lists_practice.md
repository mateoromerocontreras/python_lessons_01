# Práctica con listas

Estos ejercicios acompañan a [Introducción a las listas de Python](../lessons/01_introduction_to_lists.md).

## Cómo trabajar

Completa los ejercicios en orden. Ejecuta tu programa después de cada cambio. Guarda tus propias soluciones en un archivo separado, como `lists_practice.py`.

## Ejercicio 1: Predecir los elementos

Antes de ejecutar el código, escribe el resultado de cada instrucción `print()`. Después ejecútalo y explica cualquier diferencia.

```python
snacks = ["apple", "pretzel", "yogurt"]
print(snacks[0])
print(snacks[-1])
print(len(snacks))
```

Enfoque: índices, índices negativos y longitud.

## Ejercicio 2: Actualizar una lista de equipaje

Comienza con:

```python
packing_list = ["shirt", "water bottle", "notebook"]
```

Realiza estos cambios:

1. Reemplaza `notebook` por `camera`.
2. Agrega `sunscreen` al final.
3. Inserta `map` en el índice `1`.
4. Muestra la lista final y su longitud.

Resultado esperado:

```text
['shirt', 'map', 'water bottle', 'camera', 'sunscreen']
5
```

Enfoque: asignación mediante índices, `append()`, `insert()` y `len()`.

## Ejercicio 3: Eliminar de forma segura

Escribe un programa que comience con:

```python
chores = ["dishes", "laundry", "shopping"]
```

Pide al usuario una tarea para eliminar. Si la tarea está en la lista, elimínala y muestra la lista actualizada. De lo contrario, muestra `Esa tarea no está en la lista.`

Sample interactions:

```text
Tarea para eliminar: laundry
['dishes', 'shopping']
```

```text
Tarea para eliminar: vacuuming
Esa tarea no está en la lista.
```

Enfoque: `input()`, el operador `in` y `remove()`.

Caso límite: prueba con un valor que no esté presente.

## Ejercicio 4: Mostrar el orden sin cambiar la lista

Comienza con:

```python
scores = [72, 95, 84]
```

Después:

1. Muestra la lista original.
2. Muestra la lista en orden ascendente usando `sorted()`.
3. Muestra la lista otra vez para demostrar que el orden original no cambió.
4. Ordena la lista original permanentemente en orden descendente con `sort(reverse=True)` y muéstrala.

Enfoque: ordenamiento temporal frente a ordenamiento permanente.

## Ejercicio 5: Buscar una posición de forma segura

Escribe un programa con esta lista:

```python
planets = ["Mercury", "Venus", "Earth", "Mars"]
```

Pide al usuario una posición entera. Si la posición es válida, muestra el planeta que está en esa posición. De lo contrario, muestra `Esa posición no existe.`

Una posición válida debe ser como mínimo `0` y menor que `len(planets)`.

Sample interactions:

```text
Posición: 2
Earth
```

```text
Posición: 8
Esa posición no existe.
```

Enfoque: `int()`, `len()`, operadores de comparación y cómo evitar `IndexError`.

Casos límite: prueba `0`, el último índice válido, `-1` y un número mayor que el último índice. Decide si tu programa debe permitir índices negativos y haz explícita esa decisión.

## Ejercicio 6: Mini proyecto: planificador de viajes

Crea un pequeño planificador de viajes que gestione una lista de destinos.

Requisitos:

- Comienza con al menos tres destinos.
- Muestra la cantidad de destinos.
- Agrega un destino proporcionado por el usuario.
- Permite que el usuario elimine un destino, pero llama a `remove()` solo si existe.
- Muestra el orden original.
- Muestra una versión alfabética sin cambiar el orden original.
- Muestra el primer destino solo cuando la lista no está vacía.

Restricciones:

- Usa una lista.
- Usa `append()`, `remove()`, `len()` y `sorted()`.
- Usa una instrucción `if` para proteger la eliminación y el acceso al primer elemento.
- No uses paquetes externos.

Punto de control: ejecuta el programa una vez con un destino que exista y otra vez con un destino que no exista.

## Autoevaluación

- ¿Puedes explicar por qué el índice `3` no es válido para una lista con tres elementos?
- ¿Puedes mostrar un ordenamiento permanente y uno temporal?
- ¿Puedes eliminar un valor sin producir un error cuando no existe?
- ¿Puedes proteger el acceso al primer elemento de una lista vacía?

## Extensión opcional

Agrega un menú que permita al usuario elegir entre agregar, eliminar, mostrar los destinos ordenados o salir. Mantén el menú sencillo y asegúrate de que cada operación se proteja contra una lista vacía o un valor inexistente.
