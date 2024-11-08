# EJERCICIO [PR0401]: [Python Ejercicios Basicos]

## Índice
1. [Lectura de un número válido](#lectura-de-un-número-válido)
2. [Tabla de multiplicar](#tabla-de-multiplicar) 
3. [Triángulo de asteriscos](#triángulo-de-asteriscos)
4. [Pirámide de asteriscos](#pirámide-de-asteriscos)
5. [Número mayor y menor](#número-mayor-y-menor)
6. [Conversión de unidades](#conversión-de-unidades)
7. [Acierta el número](#acierta-el-número)
8. [Piedra, papel o tijeras](#piedra-papel-o-tijeras)
9. [Secuencia de Fibonacci](#secuencia-de-fibonacci)
---

## Lectura de un número válido

```python
inp = input("Introuduce un numero: ")
while not inp.isdigit():
    print("Error valor no valido")
    inp = input("Introuduce un numero: ")
print(inp)

```

## Tabla de multiplicar

```python
inp = input ("Dame un numero: ")
vlor = input("Dame un valor: ")
n = int(inp)
k = int(vlor)
for i in range(1, k+1):
    print(f"{n} x {i} = {n * i}")
```
## Triángulo de asteriscos

```python
a = "*"
inp = input("Dame un numeor de lineas: ")
k = int(inp)
for i in range(0,k+1):
        print(a * (i))
```

## Pirámide de asteriscos

```python
a = "*"
inp = input("Dame un numeor de lineas: ")
k = int(inp)
for i in range(1, k + 1):
    print(" " * (k - i) + a * (2 * i - 1))

```

## Número mayor y menor

```python
mayor = 0
menor = 999999999
numbers = []
for i in range(5):
    inp = input("Introduce un numero: ")
    numbers.append(inp)
for i in numbers:
    n = int(i)
    if(n > mayor): 
        mayor = n
for a in numbers:
    b = int(a)
    if(b<menor):
        menor = b
print(f"El mayor nuemero es {mayor}")
print(f"El menor nuemero es {menor}")
```
## Conversión de unidades

```python
unidades = ["Milimetros","Centimetros","Metros","Kilometros"]
inpLong = input("Introuduce la longitud: ")
n = int(inpLong).lowe
inpUnidadOrg = input(f"Introduce elige entre las unidades | {" ".join(unidades)}: ").lower()
inpUnidad = input(f"Introduce elige entre las unidades | {" ".join(unidades)}: ").lower()
conversion = 0
match inpUnidadOrg:
    case "Milimetros":
        #conversion  = n /(10 if inputUnidad == "cm" else 1000 if inputUnidad == "m" else 1)
        match inpUnidad:
            case "Kilometros":
                conversion = n / 1000000
            case "Metros":
                conversion = n / 1000
            case "Centimetros":
                conversion = n * 10
            case _:
                conversion = n
        print(f"{n} {inpUnidadOrg} es {conversion} {inpUnidad}.")
    case "Centimetros":
        match inpUnidad:
            case "Kilometros":
                conversion = n / 100000
            case "Metros":
                conversion = n / 100
            case "Milimetros":
                conversion = n * 10
            case _:
                conversion = n
        print(f"{n} {inpUnidadOrg} es {conversion} {inpUnidad}.")
    case "Metros":
        match inpUnidad:
            case "Kilometros":
                conversion = n / 1000
            case "Milimetros":
                conversion = n * 1000
            case "Centimetros":
                conversion = n * 100
            case _:
                conversion = n
        print(f"{n} {inpUnidadOrg} es {conversion} {inpUnidad}.")
    case "Kilometros":
        match inpUnidad:
            case "Milimetros":
                conversion = n * 1000000
            case "Centimetros":
                conversion = n * 100000
            case "Metros":
                conversion = n * 1000
            case _:
                conversion = n
        print(f"{n} {inpUnidadOrg} es {conversion} {inpUnidad}.")
```

## Acierta el número

```python
from random import *

rdm = randint(0,100)
inp = input("Introduce un número entre 0 y 100: ")
n = int(inp)
while (n != rdm):
    inp = input("Introduce un número entre 0 y 100: ")
    n = int(inp)
    if(rdm > n):
        print("Es superior")
    else:
        print("Es inferiro")
    
print("✅HAS ACERTADO✅")
```

## Piedra, papel o tijeras

```python
import random

opciones = ["piedra", "papel", "tijeras", "lagarto", "spock"]
reglas = {
    "piedra": ["lagarto", "tijeras"],
    "papel": ["piedra", "spock"],
    "tijeras": ["lagarto", "papel"],
    "lagarto": ["spock", "papel"],
    "spock": ["tijeras", "piedra"]
}
puntuacion_jugador = 0
puntuacion_pc = 0

while puntuacion_jugador < 5 and puntuacion_pc < 5:
    eleccion_jugador = input("Elige piedra, papel, tijeras, lagarto o spock: ").lower()
    
    if eleccion_jugador not in opciones:
        print("Opción no válida. Intenta de nuevo.")
    else:
        indice_pc = random.randint(0, len(opciones) - 1)
        eleccion_pc = opciones[indice_pc]
        
        print(f"La pc eligió: {eleccion_pc}")
        
        if eleccion_jugador == eleccion_pc:
            print("¡Es un empate!")
        elif eleccion_pc in reglas[eleccion_jugador]:
            print("¡Ganaste esta ronda!")
            puntuacion_jugador += 1
        else:
            print("La máquina ganó esta ronda.")
            puntuacion_pc += 1
        
        print(f"Puntuaciones - Jugador: {puntuacion_jugador}, pc: {puntuacion_pc}")

if puntuacion_jugador == 5:
    print("¡Felicidades! Has ganado el juego.")
else:
    print("La pc ha ganado el juego. Mejor suerte la próxima vez.")
```
## Secuencia de Fibonacci

```python
inp = int(input("Introduce la logitud de la cadena: "))
anterior = 0
actual = 1
print(f"1. ---> {anterior}")
print(f"2. ---> {actual}")
for i in range(2,inp):
    siguiente = anterior + actual
    print(f"{i+1}. ---> {siguiente}")
    anterior = actual 
    actual = siguiente
```
