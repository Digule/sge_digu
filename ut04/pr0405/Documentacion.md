# EJERCICIO [PR0405]: [Python Programación funcional]

## Índice
1. [Filtrado de una lista de números](#filtrado-de-una-lista-de-numeros)
2. [Mapeo de temperaturas](#mapeo-de-temperaturas)
3. [Suma acumulativa](#suma-acumulativa)
4. [Palabras con cierta longitud](#palabras-con-cierta-longitud)
5. [Multiplicación de pares](#multiplicacion-de-pares)
6. [Combinar operaciones en listas anidadas](#combinar-operaciones-en-listas-anidadas)

---

## Buscar valor en un diccionario
```python
# Ejemplo de lista de entrada
numeros = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
# Resultado esperado: [2, 4, 6, 8, 10]

pares = list(filter(lambda num: num % 2 == 0,numeros))

print(" ".join(str(num_pares) for num_pares in pares))
```

## Contar elementos en un diccionario
```python
# Ejemplo de lista de entrada
celsius = [0, 20, 37, 100]
# Resultado esperado: [32.0, 68.0, 98.6, 212.0]
fahrenheit = list(map(lambda x: (x*9/5) + 32,celsius))
print(" ".join(str(fa) for fa in fahrenheit))
```

## Contador de frecuencias de palabras
```python
from functools import reduce
# Ejemplo de lista de entrada
numeros = [1, 2, 3, 4, 5]
# Resultado esperado: 15
mult = reduce(lambda acc,val:acc + val, numeros,0)
print(mult)
```

## Diccionario de listas
```python
# Ejemplo de lista de entrada
palabras = ["perro", "gato", "elefante", "oso", "jirafa"]
# Resultado esperado: ['ELEFANTE', 'JIRAFA']
palabras_mas_de_cinco = list(filter(lambda word: len(word) > 5,palabras))
palabras_convertir_mayus = list(map(lambda word: word.upper(),palabras_mas_de_cinco))
print(" ".join(str(word) for word in palabras_convertir_mayus))
```

## Diccionario invertido
```python
from functools import reduce
# Ejemplo de lista de entrada
numeros = [1, 2, 3, 4, 5, 6]
# Resultado esperado: 48 (producto de 2, 4 y 6)
pares = filter(lambda num: num % 2 == 0, numeros)
#La verdad es que el map lo veo incesario pero el ejercicio lo pedia
transformados = map(lambda num: num, pares)
producto = reduce(lambda x, y: x * y, transformados)
print("El producto de los números pares transformados es:", producto)
```

## Combinar dos diccionarios
```python
from functools import reduce
# Ejemplo de lista de entrada
numeros = [[-3, 2, 7], [10, -5, 3], [0, 8, -2]]
# Resultado esperado: 30 (suma de 2, 7, 10, 3, y 8)
lista = reduce(lambda x, y: x + y, numeros)
positivos = filter(lambda x: x > 0,lista)
suma_positivos = reduce(lambda x, y: x + y, positivos)

print(suma_positivos)
```



