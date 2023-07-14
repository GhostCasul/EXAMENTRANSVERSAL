import datetime 
from colorama import init, Fore, Back, Style

pisos = 10
departamentos_por_piso = 4
precios = {'A': 3800, 'B': 3000, 'C': 2800, 'D': 3500}
departamentos_disponibles = [[True] * departamentos_por_piso for _ in range(pisos)]
departamentos_vendidos = [[None] * departamentos_por_piso for _ in range(pisos)]
compradores = {}

print(Fore.MAGENTA + Style.DIM +"Welcome to inmobiliaria CASA FELIZ!! ")
nombre = input(Fore.MAGENTA + Style.DIM + "Ingrese su nombre: ")
apellido = input("Ingrese su apellido: ")

def mostrar_menu():
    print(Fore.MAGENTA + Style.DIM +"****************** MENÚ ***********************")
    print("1. Comprar departamento")
    print("2. Mostrar departamentos disponibles")
    print("3. Ver listado de compradores")
    print("4. Mostrar ganancias totales")
    print("5. Salir")

def comprar_departamento():
    print("Departamentos disponibles:")
    for piso in range(pisos):
        for depto in range(departamentos_por_piso):
            if departamentos_disponibles[piso][depto]:
                print(f"Piso {piso+1}: Departamento {chr(65+depto)}{piso+1}")

    piso = int(input("Ingresar el piso que desea: ")) - 1
    tipo = input("Ingrese el tipo de departamento (A, B, C o D): ").upper()
    departamento = f"{tipo}{piso+1}"

    if not (1 <= piso+1 <= pisos) or tipo not in precios:
        print("Opción incorrecta, intentar denuevo.")
        return

    if not departamentos_disponibles[piso][ord(tipo)-65]:
        print("El departamento seleccionado no esta disponible.")
        return

    run = input("Ingrese el rut del comprador(sin guiones ni puntos): ")
    if not run.isdigit() or len(run) < 7 or len(run) > 8:
        print("Run incorrecto, intentar denuevo.")
        return

    departamento_index = ord(tipo) - 65
    departamentos_disponibles[piso][departamento_index] = False
    departamentos_vendidos[piso][departamento_index] = departamento
    compradores[run] = departamento

    print("Operación realizada")

def deptos_disponibles():
    print("Departamentos disponibles:")
    for piso in range(pisos):
        for depto in range(departamentos_por_piso):
            if departamentos_disponibles[piso][depto]:
                print(f"Piso {piso+1}: Departamento {chr(65+depto)}{piso+1}")
            else:
                print(f"Piso {piso+1}: Departamento {chr(65+depto)}{piso+1} (Vendido)")

def listado_compradores():
    if len(compradores) == 0:
        print("No hay ninguna compra activa")
    else:
        print("Lista de compradores:")
        for run in sorted(compradores.keys()):
            print(f"RUN: {run}, Departamento: {compradores[run]}")

def ganancias_totales():
    total_por_tipo = {tipo: 0 for tipo in precios.keys()}

    for piso in range(pisos):
        for depto in range(departamentos_por_piso):
            departamento = departamentos_vendidos[piso][depto]
            if departamento:
                tipo = departamento[0]
                total_por_tipo[tipo] += precios[tipo]

    total_general = sum(total_por_tipo.values())

    print("Ventas totales:")
    print("Tipo de Departamento Cantidad Total")
    for tipo, total in total_por_tipo.items():
        cantidad = departamentos_vendidos.count(tipo)
        print(f"Tipo {tipo} {precios[tipo]} UF {cantidad} {total} UF")
    print(f"TOTAL {sum(total_por_tipo.values())} UF")

def salir():
    nombre = input("Ingrese su nombre: ")
    apellido = input("Ingrese su apellido: ")
    print(f"Saliendo del sistema, {nombre} {apellido}!")
    print("Fecha: ", date.today())
    exit()

def obtener_fecha_actual():
    fecha_actual = datetime.datetime.now()
    return fecha_actual.strftime("%Y-%m-%d")  

def main():
    while True:
        mostrar_menu()
        opcion = input("Seleccione una opción: ")
        if opcion == "1":
            comprar_departamento()
        elif opcion == "2":
            deptos_disponibles()
        elif opcion == "3":
            listado_compradores()
        elif opcion == "4":
            ganancias_totales()
        elif opcion == "5":
            fecha_actual = obtener_fecha_actual()      
            print(Fore.MAGENTA + Style.DIM +"Saliendo de el portal inmobiliaria Casa Feliz""\n""Desarrollador : Lucas_Marchant_PGY1121_004_V ""\n" "Nombre: {}, Apellido: {}, Fecha: {}".format(nombre, apellido, fecha_actual))            
            exit()
        else:
            print("Opción inválida. Intente nuevamente.")
main()
