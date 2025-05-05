##example code
```python
# Función para validar el tipo de dato ingresado por el usuario
def Cond(tipo_dato, mensaje_peticion, mensaje_error):
    while True:  # Repite hasta que el usuario ingrese un dato válido
        try:
            valor = tipo_dato(input(mensaje_peticion))  # Intenta convertir la entrada al tipo de dato especificado (int, float, etc.)
            return valor  # Si tiene éxito, devuelve el valor convertido
        except ValueError:  # Si ocurre un error por entrada inválida (por ejemplo, letras cuando se espera un número)
            print(mensaje_error)  # Muestra mensaje de error
        except TypeError:  # Por si ocurre otro tipo de error (menos común)
            print(mensaje_error)  # Muestra mensaje de error

# Función que convierte una cadena con números separados por comas en una lista de floats (sin usar .split())
def convertir_lista(cadena):
    lista = []  # Lista donde se almacenarán los números convertidos
    numero = ''  # Cadena temporal para construir cada número
    for caracter in cadena:  # Recorre cada caracter de la cadena
        if caracter == ' ':
            continue  # Ignora los espacios
        elif caracter != ',':
            numero += caracter  # Agrega el caracter al número actual
        else:  # Si se encuentra una coma
            if numero != '':  # Si se ha acumulado un número
                lista.append(float(numero))  # Convierte el número a float y lo añade a la lista
                numero = ''  # Reinicia para el siguiente número
    if numero != '':  # Agrega el último número si existe
        lista.append(float(numero))
    return lista  # Devuelve la lista de calificaciones

# Función que calcula la suma manual de una lista (sin usar sum())
def suma_manual(lista):
    total = 0  # Variable para acumular la suma
    for numero in lista:  # Recorre cada número en la lista
        total += numero  # Suma cada número al total
    return total  # Devuelve el total acumulado

# Función que determina si una calificación está aprobada o reprobada
def Determinar_Estado_Aprobacion():
    Calificaciones = Cond(float, "Ingresa una calificación (0 a 100): ", "Error ingrese una calificación valida.")  # Solicita una calificación y la convierte a float
    if Calificaciones >= 60:  # Si la calificación es mayor o igual a 60
        print("¡Felicidades! Has aprobado.")  # Muestra mensaje de aprobación
    else:
        print("Lo siento, has reprobado.")  # Muestra mensaje de reprobación

# Función que calcula el promedio de una lista de calificaciones
def Calcular_promedio_calificaciones():
    lista = input("Ingresa una lista de calificaciones separadas por comas: ")  # Pide al usuario una cadena de calificaciones
    Calificaciones = convertir_lista(lista)  # Convierte la cadena en lista de floats
    promedio = suma_manual(Calificaciones) / len(Calificaciones)  # Calcula el promedio sin usar sum()
    print(f"El promedio de las calificaciones es: {promedio:.2f}")  # Muestra el promedio con 2 decimales

# Función que cuenta cuántas calificaciones son mayores a un valor dado
def Calcular_calificaciones_mayores():
    lista = input("Ingresa una lista de calificaciones separadas por comas: ")  # Solicita una cadena de calificaciones
    Calificaciones = convertir_lista(lista)  # Convierte la cadena a lista de floats
    valor = float(input("Ingresa un valor específico: "))  # Solicita el valor umbral
    contador = 0  # Inicializa el contador
    for x in Calificaciones:  # Recorre cada calificación
        if x > valor:  # Si la calificación es mayor al valor ingresado
            contador += 1  # Incrementa el contador
    print(f"Hay {contador} calificaciones mayores a {valor}.")  # Muestra el total encontrado

# Función que calcula el promedio de calificaciones (similar a la anterior)
def Calcular_calificaciones_especificas():
    lista = input("Ingresa una lista de calificaciones separadas por comas: ")  # Solicita la lista
    Calificaciones = convertir_lista(lista)  # Convierte a lista de floats
    promedio = suma_manual(Calificaciones) / len(Calificaciones)  # Calcula el promedio
    print(f"El promedio de las calificaciones ingresadas es: {promedio:.2f}")  # Muestra el resultado

# Función principal que muestra el menú y gestiona las opciones del usuario
def menu():
    while True:  # Ciclo infinito hasta que se elija salir
        print("\nMenú de opciones:")  # Muestra las opciones disponibles
        print("1. Determinar el estado de aprobación")
        print("2. Calcular el promedio de calificaciones")
        print("3. Contar calificaciones mayores a un valor")
        print("4. Verificar y contar calificaciones específicas")
        print("5. Salir")
        opcion = input("Elige una opción (1-5): ")  # Pide al usuario una opción
        if opcion == "1":
            Determinar_Estado_Aprobacion()  # Llama a la función correspondiente
        elif opcion == "2":
            Calcular_promedio_calificaciones()
        elif opcion == "3":
            Calcular_calificaciones_mayores()
        elif opcion == "4":
            Calcular_calificaciones_especificas()
        elif opcion == "5":
            print("¡Hasta luego!")  # Mensaje de salida
            break  # Sale del bucle y termina el programa
        else:
            print("Opción no válida, intenta de nuevo.")  # Mensaje si la opción es incorrecta

# Llamada a la función principal para ejecutar el programa
menu()
```
#example functions
```python
def greet ():
    nombre=str(input("Dame tu nombre"))
    print(f"Bienvenido {nombre}")

def addition():
    number1=float(input("Dame el primer numero: "))
    number2=float(input("Dame el segundo numero: "))
    result=number1+number2
    print(f"La multipicacion es : {result}") 

def area_cricle():
    radio=float(input("Dame el radio del circulo: "))
    area=3.1416*(radio**2)
    print(f"El area es igual a: {area}")
    
def par():
    number1=float(input("Dame el numero: "))
    if number1 % 2 == 0:
        print("El numero es par") 
    else:
        print("El numero es impar")            

def elderly():
    number1=float(input("Dame el primer numero: "))
    number2=float(input("Dame el segundo numero: "))
    number3=float(input("Dame el tercer numero: "))
    if number1 > number2 and number1 > number3:
        print(f"El numero mayor es {number1}")
    elif number2 > number1 and number2 > number3:
        print(f"El numero mayor es {number2}")
    else:        
        print(f"El numero mayor es {number3}")    

def count():
    texto=str(input("Dame un texto: "))
    vocales = "aeiouAEIOU"
    contador = 0
    for letra in texto:
        if letra in vocales:
            contador += 1
    print(f"la cantidad de vocales son: {contador}")
    
def facto():
    number1=int(input("Dame el numero: "))
    resultado = 1
    for i in range(2, number1 + 1):
        resultado *= i
    print(f"El numero factorial de {number1} es de: {resultado}")
    
def palin():
    palabra=str(input("Dame una palabra: "))
    palabra = palabra.lower().replace(" ", "") 
    if palabra == palabra:
        print("Es palindroma")
    else:
        print("No es palindroma")
            
def Fibonacci():
    number1=int(input("Dame el numero: "))  
    a, b = 0, 1  
    for i in range(number1):  
        print(a)  
        a, b = b, a + b    
       
def Cel():
    number1=float(input("Dame el numero: ")) 
    Fa=(number1*(9/5))+32 
    print(f"La temperatura en Fahrenheit es: {Fa}")       
        
def main():
    
    while True:  
        print("\nMenú de opciones:")  
        print("1. Saludar")
        print("2. Sumar dos numeros")
        print("3. Calcular el area de un circulo")
        print("4. Verificar si un numero es par")
        print("5. Encontrar el numero mayor de tres numeros")
        print("6. Contar las vocales de un texto")
        print("7. Calcular factorial")
        print("8. Verificar una palabra palindroma")
        print("9. Secuencia de Fibonacci")
        print("10. Conversion de Celsius a Fahrenheit")
        print("11. Salir")
        opcion = input("Elige una opción (1-11): ")  
        if opcion == "1":
            greet()  
        elif opcion == "2":
            addition()
        elif opcion == "3":
            area_cricle()
        elif opcion == "4":
            par()
        elif opcion == "5":
            elderly()
        elif opcion == "6":
            count()
        elif opcion == "7":
            facto()
        elif opcion == "8":
            palin()
        elif opcion == "9":
            Fibonacci()
        elif opcion == "10":
            Cel()                
        elif opcion == "11":
            print("¡Hasta luego!")  
            break  
        else:
            print("Opción no válida, intenta de nuevo.")  
main()
```
