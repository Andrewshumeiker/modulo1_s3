# modulo1_s3
estudiantes = { }                                           # Se crea el diccionario vacío para ingresar como key estudiante                       
wile_agregar_estudiante_menu = True                                  
nota = int                                                  #se define nota como un entero                                           
lista_notas = []                                                #se crea la lista vacía para las notas 
                                        
while wile_agregar_estudiante_menu:                     #while para devolverse a ingresar otro estudiante 
    wile_seguir_agregando_estudiante = True                          
    while wile_seguir_agregando_estudiante:             #se crea el while para seguir agregando estudiante
        estudiante_repetido = True
        while estudiante_repetido:                      #se crea el while por si el estudiante ya estaba en la lista
            estudiante = input("ingrese el nombre completo del estudiante: \n")   
                                                                
            if estudiante in estudiantes:           #se crea la condicion para ver si ya estaba el estudiante en la lista
                print("Este estudiante ya se encuentra en la lista, si hay dos estudiantes con el mismo nombre, \ningresale a uno algo que lo distinga")       
            else: 
                estudiantes[estudiante] =  []                   #si el estudiante no estaba en la lista, se agrega el nombre del estudiante como key y se indica que su valor es una lista vacía por el momento
                estudiante_repetido = False
        for nombre, lista_notas in estudiantes.items():                 #se recorre el diccionario y su lista luego se imprime                  
            print(f"{nombre}: {[]}")                                                          
        wile_respuesta_no_valida_seguir_agregando_estudiantes = True                           
        while wile_respuesta_no_valida_seguir_agregando_estudiantes:                    #se crea el while por si la respuesta de seguir agregando estudiantes no es valida
        
            agregar_estudiante = input("desea seguir agregando estudiantes? (si/no)\n")         
            
            if agregar_estudiante == "si":                  #si desea seguir agregando estudiantes hacer:
                print("")
                wile_respuesta_no_valida_seguir_agregando_estudiantes = False
            elif agregar_estudiante == "no":                #si no desea seguir agregando notas hacer: 
                print("Estudiante/s agregado/s con exito ")
                wile_respuesta_no_valida_seguir_agregando_estudiantes = False
                wile_agregar_estudiante_menu = False
                wile_seguir_agregando_estudiante = False
            else: 
                print("respuesta no valida, intentelo de nuevo ")
    
    wile_volver_menu = True                                     
    while wile_volver_menu:                                 #se crea el while para volver al menu
        print("---"*30)
        menu = int(input("--Que desea hacer-- \n(1) Ingresar otro estudiante \n(2) Asignar notas a estudiante \n"
        "(3) Buscar esudiante \n(4) Listar estudiantes y mostrar notas\n(5) Sacar promedio de estudiante/s\n(6) Eliminar estudiante o nota de estudiante\n"
        "(7) Ingresar un valor y contar cuantas calificaciones son mayores a este valor \n(8) Contar cuantas veces está una calificacion especifica\n"))
        print ("---"*30)
        wile_agregar_estudiante_menu = True                
        if menu == 1:                                               #si la respuesta del menu es 1 se devuelve a crear otro estudiante 
            print("")
            wile_volver_menu = False                       
        elif menu == 2:                 #si la respuesta del menu es 2 hacer:

            notas_otro_estudiante = True                  
            while notas_otro_estudiante:                    #se crea el while por si quiere agregarle notas a otro estudiante diferente 

                nombre_no_encontrado = True                     
                while nombre_no_encontrado:                     #se crea el while por si no se encuentra el nombre en la lista

                    nombre_buscar = input("Ingrese el nombre del estudiante para asignarle notas: \n")
                    if not nombre_buscar in estudiantes:            #aca se pone la condicion, si no se encuentra el estudiante volver a preguntar
                        print("estudiante no encontrado o mal escrito, intentelo de nuevo")
                        print("---"*30)
                    elif nombre_buscar in estudiantes:                  #si estudiante esta en el diccionario estudiantes hacer: 
                        nombre_no_encontrado = False
                valores_nombre = estudiantes.get(nombre_buscar)               #en la variable se almacena la lista de notas que se llama con el .get de un estudiante en especifico
                print(nombre_buscar,valores_nombre)                             #se imprime el estudiante en especifico y su lista de notas

                ingresar_mas_notas_while = True   
                while ingresar_mas_notas_while:                             #se crea el while por si desea agregarle mas notas al estudiante 
                    notas_input_validas = True
                    while notas_input_validas:
                        notas_input = input("Ingrese las notas del estudiante separadas por comas y sin espacios por favor: \n")
                        try:
                            notas_lista = [int(nota.strip()) for nota in notas_input.split(',')]
                            if all(0 <= nota <= 100 for nota in notas_lista):
                                estudiantes[nombre_buscar].extend(notas_lista)
                                notas_input_validas = False
                            else:
                                print("Todas las notas deben estar entre 0 y 100, Inténtelo de nuevo")
                        except ValueError:
                            print("Asegúrese de ingresar solo números separados por comas.")

                    valores_nombre = estudiantes.get(nombre_buscar)     
                    print(nombre_buscar,valores_nombre)
                    ingresar_mas_notas_no_valida = True
                    while ingresar_mas_notas_no_valida:
                        ingresar_mas_notas = input("Desea ingresar mas notas? (si/no)\n")         
                        if ingresar_mas_notas == "si":
                            print("")
                            ingresar_mas_notas_no_valida = False
                        
                        elif ingresar_mas_notas == "no":
                            ingresar_mas_notas_while = False
                            ingresar_mas_notas_no_valida = False
                        else:
                            print("Respuesta no valida, intentalo de nuevo")

                ingresar_notas_otro_estudiante = input("Desea ingresar notas de otro estudiante? (si/no)\n")

                if ingresar_notas_otro_estudiante== "si":
                    print("")
                elif ingresar_notas_otro_estudiante == "no":
                    notas_otro_estudiante = False
        elif menu == 3: 
            buscar_mas_estudiantes = True
            while buscar_mas_estudiantes: 

                estudiante_no_encontrado = True
                while estudiante_no_encontrado:
                    menu_buscar_nombre = input("Ingrese el nombre del estudiante que desea buscar: \n")
                    if menu_buscar_nombre in estudiantes:
                        mostrar_lista = estudiantes.get(menu_buscar_nombre)
                        print(menu_buscar_nombre , mostrar_lista)
                        estudiante_no_encontrado = False

                    elif not menu_buscar_nombre in estudiantes:
                        print("estudiante no encontrado o mal escrito, intentelo de nuevo")
                        print("---"*30)

                respuesta_no_valida = True
                while respuesta_no_valida:
                    desea_buscar_mas = input("Desea buscar mas estudiantes? (si/no) \n")
                    
                    if desea_buscar_mas == "si":
                        print("")
                        respuesta_no_valida = False
                    elif desea_buscar_mas == "no":
                        respuesta_no_valida = False
                        buscar_mas_estudiantes = False
                    else:
                        print("Esa respuesta no es valida")
                        print("---"*30)
     
        elif menu == 4:
            for nombre, lista_notas in estudiantes.items(): 
                mostrar = estudiantes.get(nombre)
                print(nombre , mostrar)

        elif menu == 5:
            estudiante_no_encontrado_pal_promedio = True
            while estudiante_no_encontrado_pal_promedio:
                promedio_estudiante = input("ingrese de que estudiante desea sacar el promedio: \n")
                if not promedio_estudiante in estudiantes:
                    print("no se ha encontrado ese estudiante, intentelo de nuevo")
                    print("--"*15)
                else: 
                    estudiante_no_encontrado_pal_promedio = False

            lista_pa_promedio = estudiantes.get(promedio_estudiante)
            cantidad_notas = len(lista_pa_promedio)
            notas_sumadas = 0
            for conta in lista_pa_promedio:
                notas_sumadas = notas_sumadas + conta
            promedio_total_estudiante = notas_sumadas / cantidad_notas
            print("--"*15)
            print (f"ESTUDIANTE:  {promedio_estudiante} ")
            print("--"*15)
            print(f"NOTAS:  {lista_pa_promedio}")
            print("--"*15)
            print(f"PROMEDIO:  {promedio_total_estudiante}")
            print("--"*15)
            if promedio_total_estudiante < 60: 
                print(f"ESTADO DEL ESTUDIANTE EN LA MATERIA: REPROBADO")
            else:
                print(f"ESTADO DEL ESTUDIANTE EN LA MATERIA: APROBADO")


        elif menu == 6:
            valor_o_caracter_no_valido = True
            while valor_o_caracter_no_valido:
                try:
                    menu_opcion_6 = int(input("--Que desea hacer?-- \n(1)  Eliminar una nota especifica de un estudiante \n(2) Eliminar estudiante por completo \n(3) volver al menù \n"))
                    if menu_opcion_6 == 1:
                        volver_eliminar_nota = True
                        el_estudiante = input("Ingrese el nombre del estudiante al que lequiere eliminar nota: \n")
                        el_lista_estu = estudiantes.get(el_estudiante)
                        while volver_eliminar_nota:
                            print(el_lista_estu) 
                            cant_notas = len(el_lista_estu)
                            indice = list(range(1,cant_notas+1))
                            for n in indice:
                                print(f" {n}  ", end='')
                            indice_elim = int(input("\nIndique la nota que desea eliminar segun el indice que aparece abajo de esta \n"))
                            not_eliminada = el_lista_estu.pop(indice_elim - 1)
                            print(f"{not_eliminada} se borrò de la lista de notas, La lista de {el_estudiante} quedò: ")
                            print( el_lista_estu)
                            respuesta_no_valida2 = True
                            while respuesta_no_valida2:
                                pregunt_volver_eliminar_nota = input(f"Desea eliminar otra nota de {el_estudiante}? (si/no) \n")
                                if pregunt_volver_eliminar_nota == "si":
                                    print("")
                                    respuesta_no_valida2 = False
                                elif pregunt_volver_eliminar_nota == "no": 
                                    volver_eliminar_nota = False
                                    respuesta_no_valida2 = False
                                    valor_o_caracter_no_valido = False

                                else: 
                                    print("Respuesta no valida, intentelo de nuevo ")
                    

                    elif menu_opcion_6 == 2:
                        eliminar_mas = True
                        while eliminar_mas:
                            elim_estudiante = input("Digite el nombre del estudiante al cual desea eliminar por completo \n")
                            segur_elim =True
                            while segur_elim:
                                seguro_elim = input (f"Esta seguro que quiere eliminar a: {elim_estudiante}? (si/no) \n")
                                if seguro_elim == "si":
                                    del estudiantes[elim_estudiante]
                                    print("asì quedò la lista de estudiantes: ")
                                    print("---"*30)
                                    for nombre, lista_notas in estudiantes.items(): 
                                        mostrar = estudiantes.get(nombre)
                                        print(nombre , mostrar)
                                    print("---"*30)
                                    segur_elim = False
                                    eliminar_mas = False
                                    valor_o_caracter_no_valido = False

                                elif seguro_elim == "no":
                                    eliminar_mas = False
                                    segur_elim = False
                                    valor_o_caracter_no_valido = False
                                else:
                                    print("Respuesta no valida, intentelo de nuevo ")
                    elif menu_opcion_6 == 3:
                        print("")
                        valor_o_caracter_no_valido = False

                    else:
                        print("Valor o caracter no valido")
                        valor_o_caracter_no_valido = False
                except ValueError:
                    print("No se pueden ingresar letras")

        elif menu == 7:
            num_mayor = True
            while num_mayor:
                lista_mayor = []
                estu_cal_mayor = input("Ingrese el estudiante al cual desea ver las calificaciones mayores que su numero: \n")
                cali_mayor = int(input("Ingrese una calificacion para ver cuantas calificaciones de la lista\n" \
                "son mayores a esta: \n"))  
                lista_not_mayor = estudiantes.get(estu_cal_mayor)
                print(lista_not_mayor)
                for n in lista_not_mayor:
                    if n>cali_mayor:
                        lista_mayor.append(n)
                        cantidad_mayores = len(lista_mayor)
                    
                print (f"lista de notas mayores a su numero \n {lista_mayor}")
                print(f"La cantidad de notas mayores a su numero es: {cantidad_mayores}")
                res_inco = True
                while res_inco:
                    volver_num_may = input("Desea volver a escribir otro numero para comparar? (si/no) \n")
                    if volver_num_may == "si":
                        print("")
                        res_inco = False
                    elif volver_num_may == "no":
                        num_mayor = False
                        res_inco = False
                    else: 
                        print("Respuesta incorrecta, intentelo de nuevo")

        elif menu == 8:
            buscar_otro = True
            while buscar_otro:
                nom_cal_especifica = input("Ingrese el nombre del estudiante al que quiere ver cuantas veces esta la calificacion en su lista de notas \n")
                lista_cal_especifi = estudiantes.get(nom_cal_especifica)
                no_aparece = True
                while no_aparece:
                    calificacion_especifica = int(input(f"Ingrese la calificacion que desea buscar en la lista de: {nom_cal_especifica} \n"))
                    if calificacion_especifica in lista_cal_especifi:
                        veces_que_aparece = lista_cal_especifi.count(calificacion_especifica)
                        print(f"La nota {calificacion_especifica} en las notas de {nom_cal_especifica} aparecen: {veces_que_aparece} veces")
                        print(lista_cal_especifi)

                        respuesta_no_valida3 = True
                        while respuesta_no_valida3:
                            otra_nota_especi = input("Desea buscar otra nota? (si/no)\n")

                            if otra_nota_especi =="si":      
                                no_aparece = False
                                respuesta_no_valida3 = False

                            elif otra_nota_especi == "no":
                                no_aparece = False
                                buscar_otro = False
                                respuesta_no_valida3 = False

                            else:
                                print("Esa respuesta no es valida, intentelo de nuevo ")

                    else:
                        print("Esa nota no aparece, intentelo de nuevo")
                        print("---"*30)
