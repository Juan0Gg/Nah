# 📚 Guía de Conceptos Python

## Tabla de Contenidos

- [Tipos de Datos](#tipos-de-datos)
- [Métodos Importantes](#métodos-importantes)
- [Funciones Lambda](#funciones-lambda)
- [Métodos HTTP y API](#métodos-http-y-api)
- [Manejo de Errores](#manejo-de-errores)
- [Librerías Importantes](#librerías-importantes)
- [Manejo de Archivos](#manejo-de-archivos)
- [Entornos Virtuales](#entornos-virtuales)
- [List Comprehensions](#list-comprehensions)

---

## Tipos de Datos

### Listas

Son colecciones ordenadas y mutables que permiten elementos duplicados.

```python
lista = [1, 2, 3, 4, 5, 6]
lista.append(7)  # Agregar elemento
```

### Tuplas

Son colecciones ordenadas e **INMUTABLES** que permiten elementos duplicados.

```python
tupla = (1, 2, 3, 4, 5, 6)
# No se pueden modificar
```

### Diccionarios

Son colecciones desordenadas, mutables e indexadas por claves únicas.

```python
diccionario = {"nombre": "Juan", "edad": 30, "ciudad": "Madrid"}
diccionario["edad"] = 31  # Modificar valor
```

### Conjuntos

Son colecciones desordenadas, mutables e indexadas por claves únicas, sin elementos duplicados.

```python
conjunto = {1, 2, 3, 4, 5, 6}
conjunto.add(7)  # Agregar elemento
```

---

## Métodos Importantes

### Funciones Integradas

- **`enumerate(lista)`** – Devuelve pares (índice, valor) de la lista

  ```python
  for i, valor in enumerate([10, 20, 30]):
      print(i, valor)  # 0 10, 1 20, 2 30
  ```

- **`range(start, stop, step)`** – Genera secuencia de números

  ```python
  for i in range(0, 10, 2):
      print(i)  # 0, 2, 4, 6, 8
  ```

- **`sorted(lista)`** – Devuelve nueva lista ordenada (no modifica la original)

  ```python
  original = [3, 1, 2]
  ordenada = sorted(original)  # [1, 2, 3]
  ```

- **`list.sort()`** – Ordena la lista en el mismo lugar (modifica original)

  ```python
  lista = [3, 1, 2]
  lista.sort()  # Ahora lista = [1, 2, 3]
  ```

- **`len(lista)`** – Devuelve la cantidad de elementos

  ```python
  print(len([1, 2, 3]))  # 3
  ```

- **`sum(lista)`** – Devuelve la suma de elementos
  ```python
  print(sum([1, 2, 3]))  # 6
  ```

### Métodos de Listas

- **`lista.append(valor)`** – Agregar elemento al final
- **`lista.insert(índice, valor)`** – Insertar en posición específica
- **`lista[0]`** – Acceder/modificar por índice
- **`lista.remove(valor)`** – Elimina primera ocurrencia del valor
- **`lista.pop(índice)`** – Elimina y devuelve elemento en índice
- **`lista.index(valor)`** – Retorna índice de primera ocurrencia
- **`lista.clear()`** – Elimina todos los elementos
- **`lista.copy()`** – Crea copia de la lista
- **`lista.count(valor)`** – Cuenta cuántas veces aparece el valor
- **`lista.map(funcion, lista)`** – Aplica función a cada elemento (con `map()`)
- **`lista.filter(funcion, lista)`** – Filtra elementos según función (con `filter()`)

### Métodos de Diccionarios

- **`dict.keys()`** – Ver todas las claves
- **`dict.values()`** – Ver todos los valores
- **`dict.items()`** – Ver pares (clave, valor)
- **`dict.get(clave, default)`** – Obtener valor con valor por defecto
- **`dict.pop(clave)`** – Elimina y devuelve valor
- **`dict.update(otro_dict)`** – Actualiza con otro diccionario

### Métodos JSON

- **`json.dump(obj, file)`** – Guarda objeto Python en archivo JSON
- **`json.dumps(obj)`** – Convierte objeto Python a cadena JSON
- **`json.load(file)`** – Carga archivo JSON como objeto Python
- **`json.loads(cadena)`** – Convierte cadena JSON a objeto Python

```python
import json

# Guardando
data = {"nombre": "Juan", "edad": 30}
json.dump(data, open('datos.json', 'w'))

# Cargando
data = json.load(open('datos.json', 'r'))
```

---

## Entornos Virtuales

### Crear entorno virtual

```bash
python -m venv .venv
```

### Activar entorno virtual

**En Windows (CMD):**

```bash
.venv\Scripts\activate.bat
```

**En Windows (PowerShell):**

```bash
.venv\Scripts\Activate.ps1
```

**En macOS/Linux:**

```bash
source .venv/bin/activate
```

---

## Funciones Lambda

Son funciones anónimas pequeñas definidas en una sola línea, útiles para operaciones simples.

```python
# Sintaxis básica
lambda argumentos: expresion

# Ejemplos
square = lambda x: x ** 2
print(square(5))  # 25

# Con map()
numeros = [1, 2, 3, 4, 5]
doblados = list(map(lambda x: x * 2, numeros))
print(doblados)  # [2, 4, 6, 8, 10]

# Con filter()
pares = list(filter(lambda x: x % 2 == 0, numeros))
print(pares)  # [2, 4]
```

---

## Métodos HTTP y API

**API**: Conjunto de reglas y protocolos que permiten la comunicación entre aplicaciones o sistemas.

### Métodos HTTP

- **GET** – Solicitar datos de un servidor
- **POST** – Enviar datos al servidor
- **PUT** – Actualizar datos existentes
- **DELETE** – Eliminar datos
- **PATCH** – Actualizar parcialmente datos

### Formato JSON

Formato ligero y legible para intercambio de datos entre cliente y servidor.

```json
{
  "nombre": "Juan",
  "edad": 30,
  "ciudad": "Madrid",
  "es_genial": true,
  "habilidades": ["Python", "JavaScript", "SQL"],
  "estudiante": null
}
```

---

## Manejo de Errores

### Excepciones

Son eventos que ocurren durante la ejecución y que interrumpen el flujo normal. Causadas por errores de sintaxis, lógica o situaciones imprevistas.

```python
try:
    # Código que puede generar una excepción
    resultado = 10 / 0
except ZeroDivisionError:
    print("No se puede dividir entre cero")
except ValueError:
    print("Valor inválido")
else:
    # Se ejecuta si NO hay excepción
    print("Operación exitosa")
finally:
    # Siempre se ejecuta
    print("Limpieza de recursos")
```

### Excepciones Comunes

| Excepción           | Causa                              |
| ------------------- | ---------------------------------- |
| `ValueError`        | Valor incorrecto para la operación |
| `TypeError`         | Tipo de dato incorrecto            |
| `FileNotFoundError` | Archivo no existe                  |
| `ZeroDivisionError` | División entre cero                |
| `KeyError`          | Clave no existe en diccionario     |
| `IndexError`        | Índice fuera de rango              |
| `NameError`         | Variable no definida               |

---

## Librerías Importantes

### Requests

Facilita el envío de solicitudes HTTP e interacción con APIs web.

```python
import requests
response = requests.get('https://api.ejemplo.com/datos')
data = response.json()
```

### Openpyxl

Permite leer y escribir archivos de Excel.

- **Workbook** – Representa un archivo de Excel
- **Worksheet** – Representa una hoja dentro del archivo
- **Cell** – Representa una celda individual

```python
from openpyxl import load_workbook
# wb = openpyxl.Workbook()
wb = load_workbook('archivo.xlsx')
ws = wb.active
ws['A1'].value = "Hola"
```

### Pandas

Proporciona estructuras de datos y herramientas para manipular y analizar datos eficientemente.

```python
import pandas as pd
df = pd.read_csv('datos.csv')
print(df.head())
```

### Matplotlib

Para crear gráficas y visualizaciones de datos.

```python
import matplotlib.pyplot as plt
plt.plot(tiempo, evolucion)
plt.title() # Da un titulo
plt.legend() # Explica los colores
plt.show() # Muestras la grafica

plt.bar(categorias, valores) # Crea una grafica de barras
plt.pie(partes, labels=categorias) # Crea una grafica de pasteles
plt.hist(datos, bins=10) # Crea un historigrama
plt.scatter(variable_x, variable_y) # Crea una grafica de dispersion
```

---

## Manejo de Archivos

### Función open()

Abre un archivo y devuelve un objeto que permite leer, escribir o manipular el archivo.

### Modos de Apertura

| Modo   | Descripción                                           |
| ------ | ----------------------------------------------------- |
| `'r'`  | Lectura (predeterminado). Archivo debe existir        |
| `'w'`  | Escritura. Sobrescribe si existe, crea si no existe   |
| `'a'`  | Adición. Agrega al final si existe, crea si no existe |
| `'x'`  | Creación. Crea archivo nuevo, error si existe         |
| `'rb'` | Lectura binaria                                       |
| `'wb'` | Escritura binaria                                     |

### Forma Correcta (Con Context Manager)

```python
# Lectura
with open('archivo.txt', 'r', encoding='utf-8') as archivo:
    contenido = archivo.read()
    print(contenido)

# Escritura
with open('archivo.txt', 'w', encoding='utf-8') as archivo:
    archivo.write('Hola, mundo!')

# Lectura línea por línea
with open('archivo.txt', 'r') as archivo:
    for linea in archivo:
        print(linea.strip())
```

> ⚠️ **Importante**: Usa `with` para garantizar que el archivo se cierra automáticamente, incluso si hay errores.

---

## List Comprehensions

Nos permiten crear listas de elementos en una sola línea de código

```python
# Sintaxis
lista = [expresión for item in iterable if condición]

# Dictionary Comprehensions
diccionario = {clave: valor for item in iterable if condición}

```

---

## Expresiones Regulares

| Símbolo   | Definición                                                                            |
| --------- | ------------------------------------------------------------------------------------- |
| `\`       | Carácter de escape para indicar formas especiales o anular significados reservados.   |
| `.`       | Coincide con cualquier carácter excepto el salto de línea.                            |
| `^`       | Indica el inicio de una línea en el texto.                                            |
| `$`       | Busca el final absoluto del texto, con cortesía ante saltos de línea finales.         |
| `*`       | Cuantificador que permite de cero a infinitas repeticiones del elemento anterior.     |
| `+`       | Cuantificador que exige una o más repeticiones del elemento anterior.                 |
| `?`       | Indica opcionalidad (cero o una ocurrencia del elemento anterior).                    |
| `{m}`     | Indica que el elemento anterior debe repetirse exactamente "m" veces.                 |
| `{m,n}`   | Indica un rango de repeticiones, desde un mínimo de "m" hasta un máximo de "n".       |
| `[]`      | Define un conjunto o set de caracteres para buscar coincidencias.                     |
| `\|`      | Operador de alternancia que permite elegir entre dos valores.                         |
| `(...)`   | Agrupa caracteres y guarda el resultado de la agrupación.                             |
| `(?:...)` | Agrupa caracteres pero no guarda el resultado (no captura).                           |
| `\A`      | Coincide exclusivamente con la posición inicial (índice 0) de la cadena.              |
| `\b`      | Define el límite o frontera donde comienza o termina una palabra.                     |
| `\B`      | Coincide con posiciones donde NO hay un límite de palabra.                            |
| `\d`      | Representa cualquier dígito decimal.                                                  |
| `\D`      | Representa cualquier carácter que no sea un dígito decimal.                           |
| `\s`      | Indica un carácter de espacio en blanco.                                              |
| `\S`      | Coincide con cualquier carácter que no sea un espacio en blanco.                      |
| `\w`      | Identifica caracteres de palabra (letras, números, guiones bajos, letras acentuadas). |
| `\W`      | Coincide con cualquier carácter que no sea un carácter de palabra.                    |
| `\z`      | Coincide con el final absoluto de la cadena de caracteres.                            |
