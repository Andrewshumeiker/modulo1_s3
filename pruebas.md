###pruebas
```python
def saludar(nombre:str=""):
    return f"hola {nombre}"
def suma(numero1:int=0,numero2:int=0):
    return numero1 + numero2
def area (radio:int=0):
    pi = 3.1416
    return radio**2*pi
def par(numero1):
    if numero1 % 2 == 0:
        return "True"
    else:
        return "False"   
def mayor_de_tres(a:int,b:int,c:int):
    return max(a,b,c)
def contar_vocales(texto):
    vocales="aeiouAEIOU"
    contador = 0
    for letra in texto:
        if letra in vocales:
            contador +=1
    return contador
def factorial(n):
    if n < 0:
        return "n no está definido"
    resultado = 1
    for i in range (1,n+1):
        resultado *= i
    return resultado
def es_palindromo(texto):
    texto = texto.lower().replace(" ","")
    return texto == texto[::-1]
def fibonacci(n):
    a = 0
    b = 1
    if n < 0:
        print("incorrect input")
    elif n == 0:
        return 0
    elif n == 1:
        return b
    else:
        for i in range (1,n):
            c = a+b
            a = b 
            b = c
        return b
for i in range (10):
    print(fibonacci(i))
def celsius_a_fahrenheit(c):
    fahrenheit = ((c*9)/5 + 32)
    return fahrenheit
def main():
    print(saludar("andres"))
    print (suma(6,3))
    print(area(5))
    print(f"el numero 7 es par: {par(7)}")
    print(f"el numero mayor es: {mayor_de_tres(2,3,4)}")
    print(f"el numero de vocales es: {contar_vocales("arepa")}")
    print(f"el factorial es {factorial(5)}")
    print(f"el texto reconocer es palindromo: {es_palindromo("reconocer")}")

    print(f"los 10 primeros terminos de la serie de fibonacci son:  {fibonacci(10)}")
    print(f"el valor en fahrenheit es: {celsius_a_fahrenheit(0)}")
main()
```
###libros
```python
def condicion ():
def main ():
    while True:
    print("\nmenú de opciones")
    print("1. Registrar nuevos libros")
    print("2. Buscar libros")
    print("3. Actualizar información")
    print("4. Eliminar libros")
    print("5. Generar reporte")
    
    if opcion == "1":
        registrar()
    elif opcion == "2":
        search()
    elif opcion == "3":
        area_cricle()
    elif opcion == "4":
        par()
    elif opcion == "5":
        elderly()

        
main()
```
