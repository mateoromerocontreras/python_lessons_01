# Práctica: Trabajando con listas

Estos ejercicios acompañan a la lección [Trabajar con listas en Python](../lessons/02_working_with_lists.md).

## Cómo trabajar

1. Completa los ejercicios en orden, ya que cada uno introduce o combina un concepto clave.
2. Guarda tus soluciones en un archivo llamado `working_lists_practice.py`.
3. Ejecuta tu código frecuentemente con Python 3 (`python working_lists_practice.py`) y comprueba que la salida coincida con lo esperado.
4. Recuerda aplicar las normas de estilo PEP 8: 4 espacios de indentación por nivel y nombres descriptivos para tus variables.

---

## Ejercicio 1: Predecir el flujo y la indentación

Antes de ejecutar cada bloque en tu computadora, escribe en una hoja o comenta en tu archivo qué líneas se imprimirán y en qué orden. Luego, ejecuta el código y compara el resultado con tu predicción.

### Código A

```python
animals = ["perro", "gato", "loro"]

for animal in animals:
    print(animal)
    print("Un " + animal + " es una excelente mascota.")

print("¡Amo a todos los animales!")
```

### Código B

```python
animals = ["perro", "gato", "loro"]

for animal in animals:
    print(animal)
print("Un " + animal + " es una excelente mascota.")
print("¡Amo a todos los animales!")
```

**Preguntas de reflexión**:
- ¿Por qué en el Código B la frase `"Un ... es una excelente mascota."` solo se imprime una vez?
- ¿Qué valor conserva la variable `animal` al finalizar el bucle?
- ¿Qué ocurriría si eliminas la sangría de la primera línea dentro del `for`?

---

## Ejercicio 2: Generar y analizar secuencias numéricas

Crea un script que realice las siguientes tareas de cálculo y generación numérica:

1. Genera una lista con los múltiplos de 3 comprendidos entre 3 y 30 inclusive utilizando `range()` y `list()`. Almacénala en `multiples_of_three`.
2. Muestra la lista completa.
3. Utiliza las funciones `min()`, `max()` y `sum()` para calcular e imprimir:
   - El múltiplo menor.
   - El múltiplo mayor.
   - La suma total de todos los múltiplos de la lista.
4. Emplea una **lista por comprensión** (*list comprehension*) para generar los primeros 10 números elevados al cubo ($1^3, 2^3, \dots, 10^3$) y guárdala en una lista llamada `cubes`. Muestra la lista resultante.

### Salida esperada

```text
Múltiplos de 3: [3, 6, 9, 12, 15, 18, 21, 24, 27, 30]
Menor múltiplo: 3
Mayor múltiplo: 30
Suma total: 165
Primeros 10 cubos: [1, 8, 27, 64, 125, 216, 343, 512, 729, 1000]
```

**Enfoque**: `range()` con salto (*step*), `list()`, `min()`, `max()`, `sum()` y listas por comprensión.

---

## Ejercicio 3: Rebanadas y recorridos parciales (*Slicing*)

Comienza con la siguiente lista de ciudades:

```python
cities = ["Madrid", "Bogotá", "Tokio", "El Cairo", "Sídney", "Toronto"]
```

Realiza las siguientes operaciones:

1. Extrae y muestra las **primeras tres** ciudades utilizando un *slice* con inicio omitido (`[:3]`).
2. Extrae y muestra las **dos ciudades del medio** (`Tokio` y `El Cairo`) utilizando un *slice* con índices explícitos.
3. Extrae y muestra las **últimas dos** ciudades utilizando índices negativos (`[-2:]`).
4. Utiliza un bucle `for` para recorrer únicamente las primeras tres ciudades y mostrar un mensaje con el formato: `Próximo destino: <nombre_de_la_ciudad>`.

### Salida esperada

```text
Primeras tres ciudades: ['Madrid', 'Bogotá', 'Tokio']
Ciudades del medio: ['Tokio', 'El Cairo']
Últimas dos ciudades: ['Sídney', 'Toronto']

Itinerario inicial:
Próximo destino: Madrid
Próximo destino: Bogotá
Próximo destino: Tokio
```

**Enfoque**: sintaxis de *slicing* `[inicio:fin]`, índices negativos e iteración sobre porciones de listas.

---

## Ejercicio 4: Copia segura frente a referencia compartida

Escribe un programa que demuestre la diferencia crucial entre copiar una lista y simplemente asignarla a una nueva variable:

1. Comienza con una lista de sabores de pizza:
   ```python
   my_pizzas = ["margarita", "cuatro quesos", "pepperoni"]
   ```
2. Crea una copia independiente llamada `friend_pizzas` usando una rebanada completa (`my_pizzas[:]`).
3. Crea una variable adicional llamada `shared_pizzas` asignándole directamente `my_pizzas` (`shared_pizzas = my_pizzas`).
4. Agrega un sabor diferente a cada una:
   - A `my_pizzas`, agrega `"vegetariana"`.
   - A `friend_pizzas`, agrega `"champiñones"`.
   - A `shared_pizzas`, agrega `"barbacoa"`.
5. Imprime las tres listas con etiquetas descriptivas.
6. Explica en un comentario en tu código por qué `"barbacoa"` aparece tanto en `my_pizzas` como en `shared_pizzas`, mientras que `friend_pizzas` se mantuvo aislada.

### Salida esperada

```text
Mis pizzas: ['margarita', 'cuatro quesos', 'pepperoni', 'vegetariana', 'barbacoa']
Pizzas de mi amigo: ['margarita', 'cuatro quesos', 'pepperoni', 'champiñones']
Pizzas compartidas (alias): ['margarita', 'cuatro quesos', 'pepperoni', 'vegetariana', 'barbacoa']
```

**Enfoque**: manejo de referencias en memoria, inmutabilidad de la estructura vs. mutación de objetos y clonación segura con `[:]`.

---

## Ejercicio 5: Configuración de resolución con tuplas

Un estudio de diseño necesita registrar resoluciones de pantalla estándar que no deben alterarse accidentalmente durante el renderizado.

1. Define una tupla llamada `screen_resolution` con los valores `1920` (ancho) y `1080` (alto).
2. Muestra los valores individuales accediendo por sus índices (`0` y `1`).
3. Intenta cambiar el ancho a `1280` escribiendo `screen_resolution[0] = 1280`. Comenta esa línea y escribe al lado qué excepción produce Python (`TypeError`).
4. Reasigna una nueva tupla a la variable `screen_resolution` con los valores `(1280, 720)`.
5. Recorre la tupla reasignada con un bucle `for` e imprime cada dimensión precedida por el texto `Dimensión:`.

### Salida esperada

```text
Ancho actual: 1920 px
Alto actual: 1080 px
Nueva resolución asignada: (1280, 720)
Dimensión: 1280
Dimensión: 720
```

**Enfoque**: sintaxis de tuplas `()`, acceso mediante índices, inmutabilidad y reasignación de variables.

---

## Ejercicio 6: Mini proyecto: Analizador de calificaciones académicas

Desarrolla un programa modular para analizar el rendimiento de un grupo de estudiantes en una evaluación oficial.

### Requisitos

1. Define una tupla de configuración inmutable con los límites reglamentarios de nota permitidos:
   ```python
   grade_limits = (0, 100)
   ```
2. Inicia con una lista de calificaciones registradas:
   ```python
   grades = [85, 92, 78, 90, 88, 76, 95]
   ```
3. Utiliza un bucle `for` con `enumerate(grades, start=1)` para mostrar cada nota en pantalla:
   ```text
   Estudiante 1: 85 puntos
   Estudiante 2: 92 puntos
   ...
   ```
4. Calcula y muestra las estadísticas generales:
   - Total de estudiantes evaluados (usando `len()`).
   - Nota mínima (usando `min()`).
   - Nota máxima (usando `max()`).
   - Promedio general con dos cifras decimales (usando `sum()` y `len()`).
5. Extrae el **Cuadro de Honor (Top 3)**:
   - Ordena temporalmente las notas de mayor a menor sin modificar la lista original `grades`.
   - Utiliza una rebanada (*slice*) para obtener las 3 notas más altas y muéstralas.
6. **Curva de bonificación**:
   - Crea una lista independiente `curved_grades` usando una lista por comprensión que otorgue +5 puntos a cada estudiante, pero asegurando con `min(nota + 5, grade_limits[1])` que nadie supere el límite máximo de 100 definido en la tupla.
   - Imprime ambas listas (`grades` y `curved_grades`) para certificar que la lista original permanece intacta.

### Restricciones

- Usa únicamente funciones y estructuras de la biblioteca estándar de Python.
- Aplica las convenciones de estilo PEP 8 (sangría de 4 espacios y nombres legibles en español o inglés consistente).
- Comprueba que la lista original de calificaciones no sufra mutaciones inesperadas.

### Salida esperada

```text
--- Registro de calificaciones ---
Estudiante 1: 85 puntos
Estudiante 2: 92 puntos
Estudiante 3: 78 puntos
Estudiante 4: 90 puntos
Estudiante 5: 88 puntos
Estudiante 6: 76 puntos
Estudiante 7: 95 puntos

--- Resumen estadístico ---
Total de evaluaciones: 7
Nota más baja: 76
Nota más alta: 95
Promedio general: 86.29

Cuadro de honor (Top 3): [95, 92, 90]
Calificaciones originales: [85, 92, 78, 90, 88, 76, 95]
Calificaciones con bonificación (+5): [90, 97, 83, 95, 93, 81, 100]
```

---

## Autoevaluación

- ¿Puedes explicar qué sucede cuando se ejecuta `for elemento in lista:` paso a paso?
- ¿Por qué `range(2, 8)` produce solo hasta el número 7?
- ¿Cuál es la diferencia de comportamiento entre `lista_b = lista_a` y `lista_b = lista_a[:]`?
- ¿En qué circunstancias debes preferir una tupla en lugar de una lista?
- ¿Por qué es fundamental no mezclar espacios y tabuladores según PEP 8?

---

## Extensión opcional

Amplía el programa del Ejercicio 6 para que reciba nuevas calificaciones por consola mediante la función `input()`. Valida que cada número ingresado esté dentro de los límites de la tupla `grade_limits` antes de incorporarlo a la lista de calificaciones con `append()`.

