# Introducción a las listas de Python

## Objetivos de aprendizaje

Al final de esta lección, podrás:

- Crear una lista y trabajar con sus elementos individuales usando índices.
- Agregar, cambiar y eliminar elementos de una lista.
- Encontrar la longitud de una lista y evitar errores comunes de índice.
- Ordenar una lista de forma permanente o mostrar una versión ordenada temporalmente.

## Requisitos previos y preparación

Debes saber crear variables, trabajar con cadenas de texto y números, y usar `print()`.

Crea un archivo llamado `lists_intro.py` y ejecútalo con Python 3:

```text
python lists_intro.py
```

Tiempo estimado: 60-90 minutos.

Resultado de la clase: crear y mantener una lista pequeña de destinos y después mostrar los destinos en distintos órdenes.

## ¿Qué es una lista?

Una lista almacena varios valores en una sola variable. Las listas están ordenadas, lo que significa que cada elemento tiene una posición. Una lista puede contener cadenas de texto, números u otros valores.

```python
cities = ["Lisbon", "Tokyo", "Nairobi"]
print(cities)
```

Los corchetes crean la lista y las comas separan sus elementos. Una lista puede estar vacía:

```python
shopping_cart = []
```

## Trabajar con elementos individuales

Python comienza a contar las posiciones de una lista desde `0`, no desde `1`.

```python
cities = ["Lisbon", "Tokyo", "Nairobi"]

print(cities[0])  # Lisbon
print(cities[1])  # Tokyo
print(cities[2])  # Nairobi
```

El número dentro de los corchetes se llama **índice**. Los índices negativos cuentan desde el final:

```python
print(cities[-1])  # Nairobi
print(cities[-2])  # Tokyo
```

Puedes reemplazar un elemento asignando un nuevo valor a su índice:

```python
cities[1] = "Seoul"
print(cities)  # ['Lisbon', 'Seoul', 'Nairobi']
```

## Agregar elementos

Usa `append()` para agregar un elemento al final de una lista:

```python
cities = ["Lisbon", "Tokyo"]
cities.append("Nairobi")
print(cities)  # ['Lisbon', 'Tokyo', 'Nairobi']
```

Usa `insert()` cuando el nuevo elemento debe ocupar una posición específica:

```python
cities.insert(1, "Seoul")
print(cities)  # ['Lisbon', 'Seoul', 'Tokyo', 'Nairobi']
```

El primer argumento es el índice donde debe colocarse el elemento. Los elementos existentes se desplazan hacia la derecha.

## Eliminar elementos

Usa `remove()` cuando conoces el valor que quieres eliminar:

```python
cities = ["Lisbon", "Tokyo", "Nairobi"]
cities.remove("Tokyo")
print(cities)  # ['Lisbon', 'Nairobi']
```

`remove()` produce un `ValueError` si el valor no está en la lista. Compruébalo antes cuando el valor podría no existir:

```python
city_to_remove = "Paris"

if city_to_remove in cities:
    cities.remove(city_to_remove)
```

Usa `pop()` cuando quieras eliminar un elemento por su índice y conservar el valor eliminado:

```python
cities = ["Lisbon", "Tokyo", "Nairobi"]
removed_city = cities.pop(1)
print(removed_city)  # Tokyo
print(cities)        # ['Lisbon', 'Nairobi']
```

Sin un índice, `pop()` elimina y devuelve el último elemento:

```python
last_city = cities.pop()
```

## Encontrar la longitud

Usa `len()` para saber cuántos elementos hay en una lista:

```python
cities = ["Lisbon", "Tokyo", "Nairobi"]
print(len(cities))  # 3
```

El índice positivo válido más grande siempre es `len(list_name) - 1`. Para una lista con tres elementos, los índices válidos son `0`, `1` y `2`.

## Evitar errores de índice

Un `IndexError` ocurre cuando solicitas una posición que no existe:

```python
cities = ["Lisbon", "Tokyo", "Nairobi"]
# print(cities[3])  # IndexError: list index out of range
```

Usa un índice válido o comprueba primero la longitud:

```python
index = 2

if 0 <= index < len(cities):
    print(cities[index])
else:
    print("Esa posición no existe.")
```

Para una lista vacía, no accedas al primer elemento hasta comprobar que la lista contiene algún elemento:

```python
cities = []

if cities:
    print(cities[0])
else:
    print("Todavía no hay ciudades.")
```

Cuando necesites procesar cada elemento, un bucle `for` evita que tengas que gestionar los índices manualmente:

```python
for city in cities:
    print(city)
```

Si necesitas tanto el índice como el elemento, usa `enumerate()`:

```python
for index, city in enumerate(cities):
    print(index, city)
```

## Ordenar listas

Hay dos formas comunes de ordenar una lista.

### Ordenamiento permanente con `sort()`

`sort()` cambia la lista original:

```python
cities = ["Tokyo", "Lisbon", "Nairobi"]
cities.sort()
print(cities)  # ['Lisbon', 'Nairobi', 'Tokyo']
```

Para ordenar en orden alfabético inverso, usa `reverse=True`:

```python
cities.sort(reverse=True)
print(cities)  # ['Tokyo', 'Nairobi', 'Lisbon']
```

Usa `sort()` cuando la lista deba conservar el nuevo orden.

### Ordenamiento temporal con `sorted()`

`sorted()` devuelve una nueva lista ordenada y deja la original sin cambios:

```python
cities = ["Tokyo", "Lisbon", "Nairobi"]
print(sorted(cities))  # ['Lisbon', 'Nairobi', 'Tokyo']
print(cities)          # ['Tokyo', 'Lisbon', 'Nairobi']
```

Usa `sorted()` cuando quieras mostrar o comparar una versión ordenada, pero conservar el orden original.

## Ejemplo guiado

El siguiente programa mantiene una lista de actividades del fin de semana. Observa cómo cambia la lista, comprueba que el acceso sea seguro y muestra tanto la versión original como una versión ordenada temporalmente.

```python
activities = ["read", "walk", "cook"]

activities.append("draw")
activities[0] = "write"

activity_to_remove = "walk"
if activity_to_remove in activities:
    activities.remove(activity_to_remove)

print("Orden original:", activities)
print("Vista alfabética:", sorted(activities))

if activities:
    print("Primera actividad:", activities[0])

print("Cantidad de actividades:", len(activities))
```

Resultado esperado:

```text
Orden original: ['write', 'cook', 'draw']
Vista alfabética: ['cook', 'draw', 'write']
Primera actividad: write
Cantidad de actividades: 3
```

## Errores comunes

- Recuerda que el primer índice es `0`.
- `sort()` cambia la lista; `sorted()` crea una copia ordenada para usarla o mostrarla.
- `remove()` usa un valor; `pop()` usa un índice y devuelve el elemento eliminado.
- Comprueba que un valor exista antes de usar `remove()` cuando podría no estar presente.
- Comprueba que una lista no esté vacía antes de acceder a un elemento.
- No uses `len(cities)` como índice del último elemento. Usa `len(cities) - 1`, o usa `cities[-1]` después de comprobar que la lista no está vacía.

## Repaso

Una lista es una colección ordenada. Usa índices para trabajar con elementos individuales, `append()` e `insert()` para agregar elementos, `remove()` y `pop()` para eliminarlos, y `len()` para contarlos. Usa `sort()` para un cambio permanente y `sorted()` para una vista ordenada temporal. Comprueba el contenido o la longitud de la lista antes de acceder a elementos o eliminarlos.

## Autoevaluación

1. ¿Cuál es el índice del primer elemento de una lista?
2. ¿Cuál es la diferencia entre `sort()` y `sorted()`?
3. ¿Cuándo usarías `pop()` en lugar de `remove()`?
4. ¿Por qué `cities[len(cities)]` puede producir un error?

## Extensión opcional

Crea una lista con tres libros favoritos. Agrega un cuarto libro, reemplaza un título, elimina un título solo si existe, muestra la cantidad de libros y muestra los libros en orden alfabético sin cambiar su orden original.
