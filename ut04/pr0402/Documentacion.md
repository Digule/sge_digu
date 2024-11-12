# EJERCICIO [PR0402]: [Python Ejercicios Cadenas]

## Índice
1. [Contar vocales y consonantes](#lontar-vocales-y-consonantes)
2. [Invertir una cadena](#invertir-una-cadena)
3. [Verificar palíndromo](#verificar-palíndromo)
4. [Contar palabras](#contar-palabras)
5. [Eliminar caracteres repetidos](#eliminar-caracteres-repetidos)
6. [Mayúsculas y minúsculas](#mayúsculas-y-minúsculas)
7. [Invertir palabras de una cadena](#invertir-palabras-de-una-cadena)
8. [Anagrama](#anagrama)
9. [Frecuencia de caracteres](#frecuencia-de-caracteres)
10. [Quitar caracteres alfanuméricos](#quitar-caracteres-alfanuméricos)
11. [Transformar a camelCase](#transformar-a-camelCase)
12. [Codificación RLE (Run-Length Encoding)](#codificación-rle)
13. [Decodificar RLE](#decodificar-rle)
14. [Comparar cadenas por valor ASCII](#comparar-cadenas-por-valor-ascii)
15. [Contar la longitud de palabra más larga](#contar-la-longitud-de-palabra-más-larga)
16. [Formatear número con separador de miles](#formatear-número-con-separador-de-miles)
17. [Rotar caracteres de una cadena](#rotar-caracteres-de-una-cadena)
---

## Contar vocales y consonantes
```python
inp = input("Escribe la cadena para analizar: ")

def word_counter(word1):
    vocales =['a','e','i','o','u']
    consonantes = ['b', 'c', 'd', 'f', 'g', 'h', 'j', 'k', 'l', 'm', 'n', 'p', 'q', 'r', 's', 't', 'v', 'w', 'x', 'y', 'z']
    countV = 0
    countC = 0
    for item in vocales:
        countV += word1.count(item) 
    for i in consonantes:
        countC += word1.count(i)
    print(f"Hay {countV} vocales en esta cadena.")
    print(f"Hay {countC} consonantes en esta cadea")


word_counter(inp)
```
## Invertir una cadena
```python
inp = input("Introduce una cadena: ")

def invertir_cadena(word1):
    return word1[::-1]

b= invertir_cadena(inp)
print(f"|{inp} al reves es {b}")
```
## Verificar palíndromo
```python
inp = input("Introduce la cadena para analizar: ")

def is_palindormo(word1):
    return "Es un palindromo" if inp == word1[::-1] else "No es palindromo"
b = is_palindormo(inp)
print(b)
```
## Contar palabras
```python
def contar_palabras(word1):
    return len(word1.split(" "))
inp = input("Inserte la cadena para analizar: ")
b = contar_palabras(inp)
print(f"Hay {b} palabras en esta frase")
```
## Eliminar caracteres repetidos
```python
def eliminar_caracteres_duplicados(param1):
    resultado = ""
    for cter in param1:
        if cter not in resultado:
            resultado += cter
    return resultado
#Esta bien concatenar string con +=
inp = input("Introduce una cadena ")
b= eliminar_caracteres_duplicados(inp)
print(b)
```
## Mayúsculas y minúsculas
```python
def combersion_upper_lower(word1):
    return word1.swapcase()

inp = input("Introduce la cadena par cambiar: ")
b = combersion_upper_lower(inp)
print(b)
```
## Invertir palabras de una cadena
```python
def invertir_cadena(param1):
    return " ".join(param1.split(" ")[::-1])
    
inp = input("Introduce la cadena: ")
b = invertir_cadena(inp)
print(b)
```
## Anagrama
```python
def anagrama(param1,param2):
    param1 = list(param1).sort()
    param2 = list(param2).sort()
    return "Es un anagrama" if param1 == param2 else "No es un anagrama"

inp1 = input("Introduce la primera palabra para comprobar: ")
inp2 = input("Introduce la segunda palabra para comprobar: ")
b = anagrama(inp1,inp2)
print(b)
```
## Frecuencia de caracteres
```python
#No
```
## Quitar caracteres alfanuméricos
```python
def remove_not_alfnum(param1):
    c = [i for i in param1 if i.isalnum()]
    return "".join(c)
b = remove_not_alfnum(input("Inserte cadena para analizar: "))
print(b)
    
```
## Transformar a camelCase
```python
def to_Camel_Case(param1):
    param1 = param1.split()
    c = [word.capitalize() for word in param1]
    a,*b = c 
    c,*d = a
    return c.lower()+ "".join(d) + "".join(b)
b = to_Camel_Case(input("Inserte la cadena: "))
print(b)
```
## Codificación RLE
```python
def rle(param1):
    cadena = []
    count = 1
    
    for i in range(1, len(param1)):
        if param1[i] == param1[i - 1]:
            count += 1
        else:
            cadena.append(f"{param1[i - 1]}{count}")
            count = 1
            
    cadena.append(f"{param1[-1]}{count}")
    return ''.join(cadena)

a = rle(input("A:"))
print(a)
```
## Decodificar RLE
```python
def rle_decode(param1):
    cadena=[]
    count = 1    
    for item in range(0,len(param1)):        
        if item.isdigit():
            count = count * 10 + int(item)  
        else:
            cadena.append(param1[item] * count)  
            count = 1  
    return "".join(cadena)
a = rle_decode(input("Introduce la cadena a decodificar: "))
print(a)
```
## Comparar cadenas por valor ASCII
```python
def get_formated_chain(param1):
    lista = param1.split(" ")
    dic = { "nombre": "Diego", "ciclo": "Dam",}
    for char in lista:
        if char[0] == "{" and char[-1] == "}":
            for key in dic:
                param1 = param1.replace(key, dic[key])
    return param1
a = get_formated_chain(input("Introduce la cadena a dar formato: "))
print(a)
```
## Contar la longitud de palabra más larga
```python
#No
```
## Formatear número con separador de miles
```python
#No
```
## Rotar caracteres de una cadena
```python
#No
```