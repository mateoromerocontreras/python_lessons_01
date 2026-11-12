# Trabajar con listas en Python

## Objetivos de aprendizaje

Al final de esta lección, podrás:

- Recorrer listas completas usando el bucle `for` y realizar acciones repetidas con cada elemento.
- Identificar y corregir errores comunes de indentación y sintaxis.
- Generar listas numéricas mediante `range()`, calcular estadísticas básicas (`min()`, `max()`, `sum()`) y escribir listas por comprensión sencillas.
- Extraer porciones de una lista (*slices*), recorrerlas y copiar listas sin modificar la original.
- Reconocer qué es una tupla, cuándo usarla y en qué se diferencia de una lista mutable.
- Aplicar normas básicas de estilo según PEP 8 para mantener tu código legible.

## Requisitos previos y preparación

Debes haber completado la lección [01: Introducción a las listas de Python](01_introduction_to_lists.md) (creación de listas, índices positivos y negativos, `append()`, `insert()`, `remove()`, `pop()` y `len()`).

Crea un archivo llamado `working_lists_intro.py` y ejecútalo con Python 3:

```text
python working_lists_intro.py
```

Tiempo estimado: 60-90 minutos.

Resultado de la clase: un programa que recorre y transforma listas de elementos y números, analiza estadísticas, extrae fragmentos de datos mediante *slicing* y utiliza tuplas para proteger valores inmutables.

---

## Recorrer una lista completa con un bucle `for`

En la lección anterior aprendiste a acceder a elementos individuales usando su índice. Sin embargo, cuando tienes listas con decenas o cientos de elementos, escribir una instrucción para cada elemento resulta ineficiente.

Un **bucle** permite repetir un bloque de instrucciones para cada elemento de una lista, sin importar cuántos elementos contenga.

```python
magicians = ["alice", "david", "carolina"]

for magician in magicians:
    print(magician)
```

Salida:

```text
alice
david
carolina
```

### ¿Cómo funciona este código?

1. La línea `for magician in magicians:` le indica a Python que tome el primer valor de la lista `magicians` y lo guarde en una variable temporal llamada `magician`.
2. Python ejecuta la línea indentada: `print(magician)`.
3. Al terminar la línea, Python regresa al inicio del bucle, toma el siguiente valor (`"david"`) y lo asigna a `magician`.
4. El proceso se repite hasta que no quedan más elementos en la lista.

### Nombres significativos para variables temporales

Es una buena práctica elegir nombres en plural para la lista y en singular para la variable temporal:

```python
for cat in cats:
    print(cat)

for dog in dogs:
    print(dog)

for item in list_of_items:
    print(item)
```

Esto ayuda a entender inmediatamente si una línea de código opera con un único elemento o con toda la colección.

---

## Realizar múltiples acciones dentro y fuera de un bucle

Puedes escribir tantas líneas como necesites dentro de un bucle. Todas las líneas con sangría (indentadas) después de la instrucción `for` forman parte del cuerpo del bucle y se ejecutarán una vez por cada elemento.

```python
magicians = ["alice", "david", "carolina"]

for magician in magicians:
    print(magician.title() + ", ¡fue un gran truco!")
    print("No puedo esperar a ver tu próximo truco, " + magician.title() + ".\n")

print("¡Gracias a todos! El espectáculo ha terminado.")
```

Salida:

```text
Alice, ¡fue un gran truco!
No puedo esperar a ver tu próximo truco, Alice.

David, ¡fue un gran truco!
No puedo esperar a ver tu próximo truco, David.

Carolina, ¡fue un gran truco!
No puedo esperar a ver tu próximo truco, Carolina.

¡Gracias a todos! El espectáculo ha terminado.
```

Observa la última línea (`print("¡Gracias a todos!...")`). Al **no** estar indentada, se ejecuta **una sola vez** al finalizar el bucle.

---

## Evitar errores comunes de indentación

Python utiliza la sangría (indentación) para definir qué instrucciones pertenecen a un bloque. Comprender estos errores te ahorrará mucho tiempo de depuración:

### 1. Olvidar indentar el bloque del bucle

```python
magicians = ["alice", "david", "carolina"]
for magician in magicians:
print(magician)  # IndentationError: expected an indented block
```

Si olvidas indentar la línea inmediatamente posterior al `for`, Python detiene la ejecución con un `IndentationError`.

### 2. Olvidar indentar líneas adicionales

```python
magicians = ["alice", "david", "carolina"]

for magician in magicians:
    print(magician.title() + ", ¡gran truco!")
print("Espero tu próximo acto, " + magician.title() + ".")
```

Esto es un **error lógico**: la sintaxis es válida, por lo que Python no emitirá un mensaje de error, pero el segundo mensaje solo se mostrará una vez, para el último mago (`carolina`), en lugar de repetirse para cada uno.

### 3. Indentar código después del bucle por accidente

```python
magicians = ["alice", "david", "carolina"]

for magician in magicians:
    print(magician.title())
    print("¡El espectáculo ha terminado!")  # Se repite 3 veces en lugar de 1
```

Si indentas una instrucción de cierre o resumen, se repetirá innecesariamente en cada ciclo.

### 4. Olvidar los dos puntos `:`

```python
for magician in magicians  # SyntaxError: expected ':'
    print(magician)
```

Los dos puntos `:` al final de la línea `for` le indican a Python que a continuación comienza un nuevo bloque de código.

---

## Creación y uso de listas numéricas

Las listas numéricas son esenciales para almacenar puntuaciones, mediciones, coordenadas o estadísticas.

### La función `range()`

La función `range()` genera una serie de números consecutivos:

```python
for value in range(1, 5):
    print(value)
```

Salida:

```text
1
2
3
4
```

> **Comportamiento "off-by-one"**: `range(1, 5)` comienza en `1` y se detiene al alcanzar `5`, sin incluirlo. Si deseas contar del 1 al 5 inclusive, usa `range(1, 6)`.

### Convertir `range()` en una lista con `list()`

Para almacenar los números directamente en una lista en memoria, envuelve `range()` en `list()`:

```python
numbers = list(range(1, 6))
print(numbers)  # [1, 2, 3, 4, 5]
```

### Usar un paso (*step*) en `range()`

El tercer argumento define el salto o incremento entre números:

```python
even_numbers = list(range(2, 11, 2))
print(even_numbers)  # [2, 4, 6, 8, 10]
```

### Construir listas dinámicamente

Puedes crear una lista vacía y llenarla dentro de un bucle calculando nuevos valores:

```python
squares = []

for value in range(1, 11):
    square = value ** 2
    squares.append(square)

print(squares)
# [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```

### Estadísticas sencillas con listas de números

Python incluye funciones integradas para obtener valores estadísticos elementales sin necesidad de bucles:

```python
digits = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0]

print(min(digits))  # 0
print(max(digits))  # 9
print(sum(digits))  # 45
```

### Listas por comprensión (*List Comprehensions*)

Una **lista por comprensión** te permite generar una lista completa en una sola línea de código concisa:

```python
squares = [value ** 2 for value in range(1, 11)]
print(squares)
# [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```

Estructura de la sintaxis:
- Un par de corchetes `[...]`.
- La expresión que genera cada elemento (`value ** 2`).
- El bucle `for` que proporciona los valores (`for value in range(1, 11)`).
- Observa que en una comprensión no se escriben dos puntos `:` al final del bucle.

---

## Trabajar con partes de una lista (Rebanado o *Slicing*)

Un *slice* te permite trabajar con un subconjunto específico de una lista en lugar de todos sus elementos.

### Sintaxis básica de rebanado

Se especifica el índice del primer elemento y el índice donde detenerse (sin incluir este último):

```python
players = ["charles", "martina", "michael", "florence", "eli"]

print(players[0:3])  # ['charles', 'martina', 'michael']
print(players[1:4])  # ['martina', 'michael', 'florence']
```

### Atajos útiles

- **Omitir el primer índice**: Python comienza desde el principio (`0`):
  ```python
  print(players[:3])   # ['charles', 'martina', 'michael']
  ```
- **Omitir el segundo índice**: Python continúa hasta el final de la lista:
  ```python
  print(players[2:])   # ['michael', 'florence', 'eli']
  ```
- **Índices negativos**: Permiten extraer elementos desde el final:
  ```python
  print(players[-3:])  # ['michael', 'florence', 'eli']
  ```

### Recorrer una rebanada con un bucle

Puedes usar un *slice* directamente como fuente de un bucle `for`:

```python
print("Los primeros tres jugadores del equipo:")
for player in players[:3]:
    print(player.title())
```

### Copiar una lista de forma segura frente a compartir referencia

Para duplicar una lista y poder modificarla sin alterar la original, debes crear una copia explícita usando una rebanada completa `[:]`:

```python
my_foods = ["pizza", "falafel", "tarta de zanahoria"]
friend_foods = my_foods[:]

my_foods.append("canoli")
friend_foods.append("helado")

print("Mis comidas favoritas:", my_foods)
print("Comidas de mi amigo:", friend_foods)
```

Salida:

```text
Mis comidas favoritas: ['pizza', 'falafel', 'tarta de zanahoria', 'canoli']
Comidas de mi amigo: ['pizza', 'falafel', 'tarta de zanahoria', 'helado']
```

> **¡Cuidado con la asignación directa!** Si escribes `friend_foods = my_foods`, ambas variables harán referencia a la **misma lista en memoria**. Si agregas un elemento a una, aparecerá automáticamente en la otra.

---

## Tuplas: Colecciones inmutables

A veces necesitas crear una lista de valores que no deben cambiar a lo largo de la ejecución de tu programa. Python llama a estos valores inmutables **tuplas** (*tuples*).

### Definición y acceso

Una tupla se parece a una lista, pero utiliza paréntesis `()` en lugar de corchetes `[]`:

```python
dimensions = (200, 50)

print(dimensions[0])  # 200
print(dimensions[1])  # 50
```

### Inmutabilidad

Si intentas modificar un elemento de una tupla, Python genera un error de tipo:

```python
dimensions = (200, 50)
# dimensions[0] = 250  # TypeError: 'tuple' object does not support item assignment
```

### Recorrer una tupla con un bucle

Puedes recorrer una tupla exactamente igual que una lista:

```python
dimensions = (200, 50)

for dimension in dimensions:
    print(dimension)
```

### Sobrescribir una tupla

Aunque no puedes cambiar los elementos individuales de una tupla, sí puedes reasignar una nueva tupla completa a la misma variable:

```python
dimensions = (200, 50)
print("Dimensiones originales:", dimensions)

dimensions = (400, 100)
print("Dimensiones modificadas:", dimensions)
```

---

## Buenas prácticas de estilo (PEP 8)

PEP 8 (*Python Enhancement Proposal 8*) es la guía de estilo oficial de Python. Facilita que tu código sea claro, consistente y fácil de mantener:

1. **Indentación**: Usa exactamente **4 espacios** por cada nivel de sangría. Configura tu editor de texto para que la tecla Tab inserte 4 espacios. Nunca mezcles tabuladores y espacios.
2. **Longitud de línea**: Procura que cada línea tenga un máximo de **79 caracteres** (o 72 caracteres para comentarios). Esto asegura que el código sea legible en cualquier pantalla o editor dividido.
3. **Líneas en blanco**: Usa líneas en blanco para separar bloques lógicos de código y facilitar la lectura visual, sin abusar colocando líneas vacías consecutivas.

---

## Ejemplo guiado

El siguiente programa procesa una lista de tiempos de vuelta (en segundos) de un piloto de carreras. Observa el cálculo de estadísticas, la extracción de las mejores marcas mediante *slicing* y el uso de una tupla para definir los límites reglamentarios:

```python
# Límites reglamentarios inmutables (tiempo mínimo y máximo permitido)
reglamento = (50.0, 90.0)

# Lista de tiempos registrados en los entrenamientos
lap_times = [62.4, 58.9, 61.2, 57.5, 64.0, 59.8]

print("Registro completo de vueltas:")
for lap_number, time in enumerate(lap_times, start=1):
    print(f"Vuelta {lap_number}: {time} s")

# Estadísticas del entrenamiento
total_laps = len(lap_times)
best_time = min(lap_times)
worst_time = max(lap_times)
average_time = sum(lap_times) / total_laps

print("\n--- Resumen de rendimiento ---")
print(f"Vueltas completadas: {total_laps}")
print(f"Mejor vuelta: {best_time} s")
print(f"Vuelta más lenta: {worst_time} s")
print(f"Promedio por vuelta: {average_time:.2f} s")

# Copia independiente para ordenar y extraer el top 3
sorted_times = sorted(lap_times)
top_three = sorted_times[:3]

print(f"\nLas 3 mejores vueltas: {top_three}")

# Comprobación contra la tupla de límites
print(f"Límites reglamentarios válidos: {reglamento[0]} s a {reglamento[1]} s")
if best_time >= reglamento[0] and worst_time <= reglamento[1]:
    print("Todas las vueltas cumplen con la normativa de la carrera.")
```

Salida esperada:

```text
Registro completo de vueltas:
Vuelta 1: 62.4 s
Vuelta 2: 58.9 s
Vuelta 3: 61.2 s
Vuelta 4: 57.5 s
Vuelta 5: 64.0 s
Vuelta 6: 59.8 s

--- Resumen de rendimiento ---
Vueltas completadas: 6
Mejor vuelta: 57.5 s
Vuelta más lenta: 64.0 s
Promedio por vuelta: 60.63 s

Las 3 mejores vueltas: [57.5, 58.9, 59.8]
Límites reglamentarios válidos: 50.0 s a 90.0 s
Todas las vueltas cumplen con la normativa de la carrera.
```

---

## Errores comunes

- **Desfase en `range()`**: Recuerda que `range(inicio, fin)` se detiene en `fin - 1`.
- **Confundir copia con asignación**: Escribir `b = a` solo crea un alias hacia la misma lista. Para copiar de forma independiente usa `b = a[:]`.
- **Modificar una tupla**: Asignar valores a un índice de una tupla (`mi_tupla[0] = valor`) genera un `TypeError`. Las tuplas deben redefinirse por completo.
- **Olvidar los dos puntos `:`**: La línea de encabezado del bucle `for` siempre debe terminar con `:`.
- **Mezclar sangrías**: Usar 3 espacios en una línea y 4 en otra produce un error de sangría. Mantén siempre 4 espacios por nivel.

---

## Repaso

El bucle `for` permite automatizar tareas sobre cada elemento de una lista de forma limpia y predecible. La función `range()` y las funciones estadísticas (`min()`, `max()`, `sum()`) agilizan la generación y el análisis numérico. Mediante el rebanado (*slicing*) puedes consultar fragmentos de una lista o clonarla de forma segura con `[:]`. Cuando necesites una lista inmutable de valores protegidos contra cambios accidentales, utiliza una tupla `()`.

---

## Autoevaluación

1. ¿Qué números genera la llamada `range(3, 8)`?
2. ¿Cuál es la diferencia en memoria entre escribir `copia = lista[:]` y escribir `copia = lista`?
3. ¿Qué ocurre si intentas ejecutar `mi_tupla[0] = 10`?
4. ¿Cómo obtendrías los últimos tres elementos de cualquier lista con más de tres elementos usando *slicing*?

---

## Extensión opcional

Crea una lista de 10 números aleatorios o generados con `range()`. Emplea una lista por comprensión para calcular una nueva lista que contenga únicamente los números pares multiplicados por 10, y muestra su valor mínimo, máximo y la suma de sus elementos.

