# Composición de Clases

Otra forma conocida de reutilizar código que se ha implementado previamente en otras clases es a tráves de lo que se conoce como Composición de Clases. Es similar a la herencia con la principal excepción (entre algunas otras) de que no se utiliza una sintaxis explícita para indicar que se está implementando una composición, simplemente se declaran objetos de distintas clases (comunmente conocidos como partes) al interior de la definición de una nueva clase (conocida como el todo). De esta forma y de manera indirecta la nueva clase adhiere las propiedades y métodos de las clases que la componen. Se puede observar que la composición no solo contribuye a la reusabilidad de código existente sino que también hace que el código sea escalable ya que al no existir una relación estrecha de dependencia entre las clases se pueden implementar cambios en clases individuales para que se vean reflejados en las clases compuestas por objetos de esas clases. El siguiente ejemplo clarifica el concepto que se acaba de exponer:

```cpp
class UnaClase
{
    private:
    int unaVar;
    public:
    void setVar(int x){unaVar = x;}
    int getVar(){return unaVar;}
};

class OtraClase
{
    private:
    UnaClase unObj;
    public:
    void setVar(int x){unObj.setVar(x);}
    int getVar(){return unObj.getVar();}
    
};

class OtraClaseMas
{
    private:
    UnaClase otroObj;
    public:
    void setVar(int x){otroObj.setVar(x);}
    int getVar(){return otroObj.getVar();}
    
};

int main()
{
    OtraClase obj;
    OtraClaseMas ojt;
    obj.setVar(5);
    ojt.setVar(25);
    cout<<obj.getVar()<<endl;
    cout<<ojt.getVar()<<endl;
    
    return 0;
}
```
# Adicional: Paso de objetos temporales como parámetros de entrada de funciones (métodos).

El paso de parámetros por referencia con el calificador `const`, tal cual como se pasa un objeto a un constructor de copia, permite hacer el paso de objetos temporales. Un objeto temporal es un objeto que no se declara ya que solo se invoca a través de una expresión o como parámetro de entrada de una función y cuyo tiempo de vida es muy corto.En particular la duración de un objeto temporal es el mismo de la ejecución de la expresión que lo invoca. Lo anterior quiere decir que un objeto temporal solo existe mientras la operación o función que lo invoca toma su valor y luego es destruido en memoria.

Los objetos temporales solo se pueden pasar como parámetros de entrada a funciones que tienen un paso por referencia a objetos de este tipo y calificado con `const`. Observe el siguiente ejemplo en el que se pasa un objeto temporal al constructor de otro objeto de una clase compuesta, ponga especial atención en la ejecución del constructor y el destructor del objeto temporal:

```C++ runnable
#include<iostream>
using namespace std;

class UnaClase
{
    public:
    int unaVar;
    UnaClase(int x):unaVar(x){cout<<"UnaClase construido"<<endl;}
    ~UnaClase(){cout<<"UnaClase destruido"<<endl;}
};

class OtraClase
{
    private:
    UnaClase unObj;
    public:
    OtraClase(const UnaClase& oVar):unObj(oVar.unaVar){}
    int getVar(){return unObj.unaVar;}
};

int main()
{
    OtraClase obj(UnaClase(5));
    cout<<obj.getVar()<<endl;
    
    return 0;
}
```

```C++ runnable
#include<iostream>
using namespace std;

#define False 0
#define True 1

class Turbinas
{
    public:
    int num_turbinas = 0;
    Turbinas(int n):num_turbinas(n){}
};

class Helices
{
    public:
    int num_helices = 0;
    Helices(int n):num_helices(n){}
};

class TrendeAterrizaje
{
    public:
    int num_neumaticos = 0;
    int num_amortiguadores = 0;
    bool fijo_retractil = False;
    TrendeAterrizaje(int a, int b, bool c):num_neumaticos(a), num_amortiguadores(b), fijo_retractil(c){}
};

class Alas
{
    public:
    int num_alas_frente = 0;
    int num_alas_cola = 0;
    Alas(int m, int n):num_alas_frente(m), num_alas_cola(n){}
};

class Cubierta
{
    public:
    bool cabina_tripulacion = False;
    bool cabina_vuelo = False;
    bool sistema_emergencia = False;
    int num_combustible = 0;
    int num_asientos = 0;
    bool cocineta = 0;
    int num_banios = 0;
    int num_salidas = 0;
    Cubierta(bool a, bool b, bool c, int m, int n, bool x, int y, int z)
    {
        cabina_tripulacion = a;
        cabina_vuelo = b;
        sistema_emergencia = c;
        num_combustible = m;
        num_asientos = n
        cocineta = x;
        num_banios = y;
        num_salidas = z;
};

class Aeroplano
{
    
};

class Jet
{
};

class Dron
{
};

int main()
{
    Aeroplano airplane();
    Jet boeing777();
    Dron vigilanteNoTripulado();
    
    airplane.printInfo();
    boeing777.printInfo();
    vigilanteNoTripulado.printInfo();
    
    return 0;
}
```
