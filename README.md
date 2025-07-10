#include <iostream>   // Incluye la biblioteca para entrada y salida estándar
#include <string>     // Incluye la biblioteca para usar cadenas de texto (string)
using namespace std;  // Permite usar los elementos del espacio de nombres std sin escribir std::
// Clase base abstracta 'persona'
class persona {
protected:
    string nombre;  // Nombre de la persona (protegido para que lo puedan usar las clases hijas)
    int edad;       // Edad de la persona
public:
    // Constructor de la clase persona
    persona(string nombre, int edad) : nombre(nombre), edad(edad) {}
    // Método virtual puro que obliga a las clases derivadas a implementarlo
    virtual void mostrarInformacion() const = 0;
    // Método para obtener el nombre
    string obtenerNombre() const {
        return nombre;
    }
    // Método para obtener la edad
    int obtenerEdad() const {
        return edad;
    }
    // Destructor virtual (buena práctica en clases con herencia)
    virtual ~persona() {}
};
// Clase derivada 'Estudiante' que hereda de 'persona'
class Estudiante : public persona {
private:
    string carrera;   // Carrera universitaria del estudiante
    int matricula;    // Número de matrícula del estudiante
public:
    // Constructor de Estudiante que llama al constructor de persona
    Estudiante(string nombre, int edad, string carrera, int matricula)
        : persona(nombre, edad), carrera(carrera), matricula(matricula) {}
    // Implementación del método virtual para mostrar información del estudiante
    void mostrarInformacion() const override {
        cout << "Estudiante: " << nombre << endl;
        cout << "Edad: " << edad << endl;
        cout << "Carrera: " << carrera << endl;
        cout << "Matricula: " << matricula << endl; 
    }
};
// Clase derivada 'Profesor' que hereda de 'persona'
class Profesor : public persona {
private:
    string departamento;  // Departamento al que pertenece el profesor
    double salario;       // Salario del profesor
public:
    // Constructor de Profesor que llama al constructor de persona
    Profesor(string nombre, int edad, string departamento, double salario)
        : persona(nombre, edad), departamento(departamento), salario(salario) {}

    // Implementación del método virtual para mostrar información del profesor
    void mostrarInformacion() const override {
        cout << "Profesor: " << nombre << endl;
        cout << "Edad: " << edad << endl;
        cout << "Departamento: " << departamento << endl;
        cout << "Salario: " << salario << endl;
    }
};
// Función principal del programa
int main() {
    // Crear un objeto de tipo Estudiante
    Estudiante estudiante1("Ana Figuerado", 20, "Ingenieria en Sistemas", 12345);
    // Crear un objeto de tipo Profesor
    Profesor profesor1("Carlos Ramirez", 45, "Ciencias de la Computacion", 55000);  
    // Mostrar la información del estudiante
    estudiante1.mostrarInformacion();
    cout << endl; // Línea en blanco para separar las salidas
    // Mostrar la información del profesor
    profesor1.mostrarInformacion();
    return 0; // Fin del programa
}
