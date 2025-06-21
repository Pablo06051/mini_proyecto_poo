def get_puede_votar(self):
        if self.__edad >= 18:
            return (f"el estudiante {self.__nombre} puede votar")
        else:
            return (f"el estudiante {self.__nombre} no puede votar")
        
    def obtener_nota(self):
        if self.__nota >= 6:
            return (f"el estudiante {self.__nombre} aprueba la materia")
        else:
            return (f"el estudiante {self.__nombre} no aprueba la materia")
        
class materia:
    def __init__(self, nombre, creditos, docente):
        self.__nombre = nombre
        self.__creditos = creditos
        self.__docente = docente
        self.__alumnos = []

    def get_nombre(self):
        return self.__nombre
    def get_creditos(self):
        return self.__creditos
    def get_docente(self):
        return self.__docente
    
    def agregar_alumno(self, alumno):
        self.__alumnos.append(alumno)
        print(f"Alumno {alumno.get_nombre()} asignado a la materia {self.__nombre}")

    def listar_alumnos(self):
        if self.__alumnos:
            print(f"Alumnos en la materia {self.__nombre}:")
            for alumno in self.__alumnos:
                print(alumno.get_nombre())
        else:
            print(f"No hay alumnos asignados a la materia {self.__nombre}")

   
class sistemaAcademico:
    def __init__(self):
        self.__materias = []


    def agregar_materia(self, materia):
        self.__materias.append(materia)
        print(f"Materia {materia.get_nombre()} agregada al sistema académico.")

    def listar_materias(self):
        if self.__materias:
            print("Materias en el sistema académico:")
            for materia in self.__materias:
                print(f"- {materia.get_nombre()}")
        else:
            print("No hay materias en el sistema académico.")
    
    def buscar_materia(self, nombre):
        for materia in self.__materias:
            if materia.get_nombre() == nombre:
                return materia
        print(f"No se encontró la materia con nombre {nombre}.")
        return None
    

# Ejemplo de uso

alumno1 = alumno("12345", "Juan Perez", 20, 7.5)
alumno2 = alumno("67890", "Maria Lopez", 17, 8.0)
alumno3 = alumno("54321", "Carlos Gomez", 19, 5.5)
alumno1.set_nota(8.5)
alumno2.set_nota(5.0)
alumno3.set_nota(6.0)
print(f"{alumno1.get_nombre()} puede votar: {alumno1.get_puede_votar()}")
print(f"{alumno2.get_nombre()} puede votar: {alumno2.get_puede_votar()}")
print(f"{alumno3.get_nombre()} puede votar: {alumno3.get_puede_votar()}")
print(f"{alumno1.get_nombre()} aprueba la materia: {alumno1.obtener_nota()}")
print(f"{alumno2.get_nombre()} aprueba la materia: {alumno2.obtener_nota()}")
print(f"{alumno3.get_nombre()} aprueba la materia: {alumno3.obtener_nota()}")



sistema = sistemaAcademico()
materia1 = materia("Matemáticas", 3, "Dr. Smith")
materia2 = materia("Historia", 4, "Prof. Johnson")
sistema.agregar_materia(materia1)
sistema.agregar_materia(materia2)
sistema.listar_materias()
materia1.agregar_alumno(alumno1)
materia1.agregar_alumno(alumno2)
materia1.listar_alumnos()
materia2.agregar_alumno(alumno1)
materia2.listar_alumnos()
materia_encontrada = sistema.buscar_materia("Matemáticas")
if materia_encontrada:
    print(f"Materia encontrada: {materia_encontrada.get_nombre()}")
    