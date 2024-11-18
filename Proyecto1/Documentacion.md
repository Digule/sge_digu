# PROYECTO 1ª Evaluación

## Índice
1. [Código del Main](#main)
2. [Código de Menú](#menú)
3. [Código de DataTask](#datatask)
4. [Código de Add](#add) 
5. [Código de Listar](#listar)  
6. [Código de FileManager](#filemanager)

---

## Main
```python
import menu
#Iniciar el programa
print("██████  ██  ██████  ██    ██ ██      ███████     ██████  ██████   ██████  ██     ██ ███████  ██████ ████████ ")
print("██   ██ ██ ██       ██    ██ ██      ██          ██   ██ ██   ██ ██    ██  ██  ██  ██      ██         ██    ")
print("██   ██ ██ ██   ███ ██    ██ ██      █████       ██████  ██████  ██    ██   ████   █████   ██         ██    ")
print("██   ██ ██ ██    ██ ██    ██ ██      ██          ██      ██   ██ ██    ██    ██    ██      ██         ██    ")
print("██████  ██  ██████   ██████  ███████ ███████     ██      ██   ██  ██████     ██    ███████  ██████    ██    ")
print("                                                                                                            ")
menu.execute_menu()
```

## Menú
```python
import add
import listar
import fileManeger
import os

#Mostrar las opciones del menu
def print_menu():
    print("<|--------------| MENÚ |--------------|>")
    print(" | 0. Salir                           |")
    print(" | 1. Añadir tarea                    |")
    print(" | 2. Listar tareas                   |")
    print(" | 3. Marcar tarea como completada    |")
    print(" | 4. Eliminar tarea                  |")
    print(" | 5. Guardar y cargar desde fichero  |")
    print(" | 6. Ver tareas vencidas             |")
    print("<|------------------------------------|>")
#Manejar la opciones
def menu_seleccion(option):
    RED = "\033[31m" 
    RESET = "\033[0m"
    try:
        option_good = int(option)
        match option_good:
            case 1: 
                #Opcion añadir
                name = input("Nombre: ")
                priority = input("Prioridad: ")
                date = input("Fecha Limite (dd/mm/yyyy): ")
                complete = input("Completada?: ")
                add.add_task(name, priority, date, complete)
            case 2:
                #Opcion listar tareas
                listar.list_all_tasks_notcomplete()
            case 3:
                #Opcion marcar como completada
                name = input("Nombre: ")
                add.set_complete(name)
            case 4:
                #Opcion eliminar tareas
                name = input("Nombre: ")
                add.delete_task(name)
            case 5:
                #Opción guardar y cargar desde fichero
                print("1. Guardar tareas en fichero")
                print("2. Cargar tareas desde fichero")
                sub_option = input("Selecciona una opción: ")
                if sub_option == "1":
                    fileManeger.save_tasks_to_csv("tasks.csv")
                    print("Tareas guardadas correctamente.")
                elif sub_option == "2":
                    fileManeger.load_tasks_from_csv("tasks.csv")
                    print("Tareas cargadas correctamente.")
                else:
                    print("No válida.")
            case 6:
                #Opcion tareas vencidas
                listar.expired_tasks()
            case 0: 
                #Opcion acabar programa
                fileManeger.save_tasks_exit()
                print("Saliendo") 
                return True
            case _:  
                print("OPTION - NO es VALIDA")
    except ValueError:
        print(RED + "ERROR - NO es un NUMERO" + RESET)

#Ejecutar el menu
def execute_menu():
    while True:
        print_menu()
        option = input("Selecciona una opción: ")
        if menu_seleccion(option):  
            break
```

## DataTask
```python
import datetime

fecha = datetime.time()
#Tareas almacenadas
#HE DEJADO 3 EJEMPLOS DISTINTOS PARA QUE SE PUEDA PROBAR CLARAMENTE
tasks = [
    {"nombre": "Cocinar", "prioridad": 0, "fecha_limite": "12/12/2025", "completa": False},
    {"nombre": "Comer", "prioridad": 2, "fecha_limite": "10/10/2025", "completa": True},
    {"nombre": "Estudiar", "prioridad": 1, "fecha_limite": "02/03/2024", "completa": False}
]

#Devuelve la lista de tareas
def get_task_list():
    return tasks

#Imprime toas las tareass
def print_task_list():
    result = "\n".join([f"Nombre: {task['nombre']}, Prioridad: {task['prioridad']}, Fecha Limite: {task['fecha_limite']}, Completa: {task['completa']}" for task in tasks])

    return print(result)

#Filtra por nombre
def filtrar_by_name(name):
    for task in tasks:
        if task['nombre'].lower() == name.lower():
            return task
    return None 

#Filtra las tares que no estan completadas
def filtrar_task_notcomplete():
    print(expired_date())
    result = "\n".join([f"Nombre: {task['nombre']}, Prioridad: {task['prioridad']}, Fecha Limite: {task['fecha_limite']}, Completa: {task['completa']}" for task in tasks if not task['completa']])
    if result:  
        return result
    else:
        return "No hay tareas incompletas."
    
#Muestra las tares vecidas de tiempo
def expired_date():
    today = datetime.datetime.now()
    expired_tasks = [task for task in tasks if datetime.datetime.strptime(task['fecha_limite'], "%d/%m/%Y") < today and not task['completa']]
    if expired_tasks:
        messages = [f"La tarea '{task['nombre']}' está vencida. Fecha límite: {task['fecha_limite']}" for task in expired_tasks]
        return "\n".join(messages)
    return "No hay tareas vencidas."

```

## Add
```python
import datetime
import dataTask

#Añado una tarea
def add_task(name, priority, date, isComplete):
    tasks = []
    if not priority.isdigit():
        print("Error: La prioridad debe ser un número.")
        return
        
    else:    
        priority = int(priority)
        # Verificar que la prioridad esté en el rango válido (1-3)
        if priority < 1 or priority > 3:
            print("Error: La prioridad debe estar entre 0 y 2.")
            return
        
        if isComplete.lower() in ["si", "sí", "yes"]:
            isComplete = True
        elif isComplete.lower() in ["no","negativo","nein"]:
            isComplete = False
        else:
            print("Error: La entrada para completada debe ser 'si' o 'no'.")
            return
        
        try:
            valid_date = datetime.datetime.strptime(date, "%d/%m/%Y") 
            if valid_date < datetime.datetime.now():
                print("ERROR - la FECHA no es valida, ya que es ANTIGUA")
                return
 
        except ValueError:
            print("Error: La fecha debe estar en formato dd/mm/yyyy.")
            return
        task = {
            "nombre": name,
            "prioridad": priority,
            "fecha_limite": valid_date.strftime("%d/%m/%Y"),
            "completa": isComplete
        }
        tasks.append(task)
        print(f"Tarea agregada: {', '.join(f'{k}: {v}' for k,v in task.items())}")
        dataTask.print_task_list()

#Borra una tarea en base a su nombre
def delete_task(name_to_delete):
    tasks = dataTask.get_task_list()  
    task_to_delete = dataTask.filtrar_by_name(name_to_delete) 

    if task_to_delete:
        tasks.remove(task_to_delete)  
        print(f"Tarea '{name_to_delete}' eliminada.")
    else:
        print(f"No se encontró la tarea con nombre '{name_to_delete}'.")
    dataTask.print_task_list() 

#Marca como completada una tarea, dando su nombre
def set_complete(name):
    task = dataTask.filtrar_by_name(name)  
    if task:
        task['completa'] = True  
        print(f"Tarea '{task['nombre']}' marcada como completada.")
    else:
        print(f"No se encontró la tarea con nombre '{name}'.")
```

## Listar
```python
import dataTask

#Mostrar por pantalla un listado de las tareas que no estan completadas (Resaltando las vencidas por tiempo)
def list_all_tasks_notcomplete():
    result = dataTask.filtrar_task_notcomplete()
    print(result)

#Muestra la tareas vencidas
def expired_tasks():
    print(dataTask.expired_date())
```

## FileManager
```python
import dataTask
import csv

#Guarda las tareas en un archivo CSV
def save_tasks_to_csv(file_path):
    with open(file_path, mode='w', newline='', encoding='utf-8') as file:
        writer = csv.DictWriter(file, fieldnames=["nombre", "prioridad", "fecha_limite", "completa"])
        writer.writeheader()
        writer.writerows(dataTask.get_task_list())  

#Carga las tareas desde un archivo CSV
def load_tasks_from_csv(file_path):
    try:
        with open(file_path, mode='r', encoding='utf-8') as file:
            reader = csv.DictReader(file)
            tasks = []
            for row in reader:
                #Convertir los valores 
                task = {
                    "nombre": row["nombre"],
                    "prioridad": int(row["prioridad"]),
                    "fecha_limite": row["fecha_limite"],
                    "completa": row["completa"].lower() == 'true'
                }
                tasks.append(task)
            dataTask.tasks = tasks 
    except FileNotFoundError:
        print(f"El archivo {file_path} no existe. Se utilizarán las tareas por defecto.")

#Cargar las tareas del archivo CSV (Al iniciar)
csv_file_path = "tasks.csv"
load_tasks_from_csv(csv_file_path)

#Guarda las tareas en el archivo CSV (Al salir)
def save_tasks_exit():
    save_tasks_to_csv(csv_file_path)

```
**DIGULE🦛**