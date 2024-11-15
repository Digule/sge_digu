# EJERCICIO [PR0404]: [Python Ejercicios Diccionarios]

## Índice
1. [Buscar valor en un diccionario](#buscar-valor-en-un-diccionario)
2. [Contar elementos en un diccionario](#contar-elementos-en-un-diccionario)
3. [Contador de frecuencias de palabras](#contador-de-frecuencias-de-palabras)
4. [Diccionario de listas](#diccionario-de-listas)
5. [Diccionario invertido](#diccionario-invertido)
6. [Combinar dos diccionarios](#combinar-dos-diccionarios)
---

## Buscar valor en un diccionario
```python
fruta = input("Introduce una fruta para comprobar su precio: ")
frutas_precio = {"manzana":12,"platano":15,"naraja":8,"melon":10,"piña":5}
print(frutas_precio[fruta]) if fruta.lower() in frutas_precio else print(f"Lo siento pero {fruta} no esta disponible")
```

## Contar elementos en un diccionario
```python
productos = {
    "Electrónica": ["Smartphone", "Laptop", "Tablet", "Auriculares", "Smartwatch"],
    "Hogar": ["Aspiradora", "Microondas", "Lámpara", "Sofá", "Cafetera"],
    "Ropa": ["Camisa", "Pantalones", "Chaqueta", "Zapatos", "Bufanda"],
    "Deportes": ["Pelota de fútbol", "Raqueta de tenis", "Bicicleta", "Pesas", "Cuerda de saltar"],
    "Juguetes": ["Muñeca", "Bloques de construcción", "Peluche", "Rompecabezas", "Coche de juguete"],
}

print(f"Hay {len(productos)} categorías. \n---------------------")

total_productos = 0
for categoria, items in productos.items():
    total_productos += len(items)
    print(f"{categoria} --> {len(items)} productos")

print(f"--------------------- \nEn total hay {total_productos} productos.")
```

## Contador de frecuencias de palabras
```python
frase = input("Introduce una frase: ")
dict = {}
for palabra in frase.split():
    dict[palabra] = dict.get(palabra, 0) + 1  
print(dict)
```

## Diccionario de listas
```python
asignaturas = {
    "Matemáticas": ["Ana", "Carlos", "Luis", "María", "Jorge"],
    "Física": ["Elena", "Luis", "Juan", "Sofía"],
    "Programación": ["Ana", "Carlos", "Sofía", "Jorge", "Pedro"],
    "Historia": ["María", "Juan", "Elena", "Ana"],
    "Inglés": ["Carlos", "Sofía", "Jorge", "María"],
}

opcion = input("Opcion 1 = Listar estudiantes matriculados en una asignatura \nOpcion 2 = Matricular un estudiante en una asignatura \nOpcion 3 = Dar de baja un estudiante de una asignatura\nOpción:" )
match int(opcion):
    case 1 : 
        asignatura = input("Introduce una asignatura: ")
        estudiantes = asignaturas[asignatura] if asignatura in asignaturas else []
        print(f"Estudiantes matriculados en {asignatura}s : {" ".join(estudiantes)}")
    case 2:
        asignatura = input("Introduce una asignatura: ")
        alumno_nombre = input("Nombre del Alumno: ")
        if asignatura in asignaturas:
            asignaturas[asignatura].append(alumno_nombre)
            print("Matriculao")
        else:
            print("La asignatuta no existe")
    case 3:
        asignatura = input("Introduce una asignatura: ")
        alumno_nombre = input("Nombre del Alumno: ")
        if asignatura in asignaturas:
            if alumno_nombre in asignaturas[asignatura]:
                asignaturas[asignatura].remove(alumno_nombre)
                print("Matriculao")
            else:
                print("No existe alumno")
        else:
            print("La asignatuta no existe")
```

## Diccionario invertido
```python
diccionario = {"Jose":1,"Paco":2,"Ramon":3}
def invertir_diccionario(diccionario):
    return {valor: clave for clave, valor in diccionario.items()}
a = invertir_diccionario(diccionario)
print(a)
```

## Combinar dos diccionarios
```python
diccionario_principal = {"Jamon":120,"Laptop":80,"Gallina":6,"Toallas":10}
diccionario_secundario = {"Laptop":120,"Rotuladores":3,"Platanos":2,"Toallas":7}
diccionario_combinado = diccionario_principal.copy()  

for producto, precio in diccionario_secundario.items():
    if producto in diccionario_combinado:
        diccionario_combinado[producto] += precio 
    else:
        diccionario_combinado[producto] = precio  
print(diccionario_combinado)
```



