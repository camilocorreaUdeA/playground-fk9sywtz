# Concepto de Herencia

La Herencia es uno de los conceptos fundamentales de la programación orientada a objetos ya que permite la reusabilidad de variables y funcionalidades que se han definido en otras clases. Para hablar de herencia se deben introducir los conceptos de `clase base` y `clase derivada`. Se conoce como clase base a una clase que va a heredar sus propiedades (variables) y funcionalidades (métodos) a otras clases; por otro lado, se conoce como clase derivada a una clase que se implementa mediante la reutilización de las propiedades y funcionalidades que se heredan de una (o varias) clase base. La herencia contribuye en cierto grado con la escalabilidad de una aplicación ya que cuando se debe modificar o eliminar una variable o un método heredado en todas las clases derivadas, entonces no es necesario que se haga individualmente en cada clase sino que se hace directamente en la clase base y las clases derivadas simplmente heredan la actualización de esos miembros.

La herencia en C++ se expresa en la implementación de una clase mediante el uso del operador dos puntos `:` seguido del tipo de herencia (que lo veremos más adelante) y del nombre de la clase base de la que se busca heredar. Vale anotar que el tipo de herencia por defecto en C++, cuando no se especifica explicitamente ese campo, es la herencia privada. A continuación se observa la implementación más simple del concepto de herencia en C++:

```C++ runnable
#include<iostream>
using namespace std;

class ClaseBase
{
    protected:
    int unaVar = 0;
    public:
    void unMetodo(void)
    {
        unaVar++;
        cout<<"unaVar = "<<unaVar<<endl;
    }
};

class ClaseDerivada : public ClaseBase  /* Sintaxis para indicar que ClaseDerivada hereda de ClaseBase */
{
    /* Esta clase implementa los miembros de clase que hereda de ClaseBase */
};

int main()
{
    ClaseDerivada obj1;
    obj1.unMetodo(); /* Acceso a los miembros heredados de ClaseBase */
    obj1.unMetodo();
    return 0;
}
```
# Tipos de herencia en C++

Antes de hablar de los tipos de herencia en C++ es necesario introducir el concepto de nivel de acceso protegido, ya antes se había revisado los niveles de acceso público y privado. El nivel de acceso protegido, que en C++ se especifica con la palabra `protected` se comporta de manera similar al nivel de acceso privado con la diferencia de que permite que los miembros de clase con este nivel de acceso puedan ser heredados a clases derivadas. Es importante aclarar que los miembros de una clase con acceso privado <b>NO</b> son heredables, como tampoco lo son los constructores, destructores y operadores sobrecargados. A continuación se listan los 3 tipos de herencia en C++:

<ul>
<li><b>Herencia pública:</b> Se refiere a la herencia en la que todos los miembros públicos y protegidos de la clase base conservan esos mismos niveles de acceso respectivamente en las clases derivadas.</li>

```C++
class ClaseDerivada : public ClaseBase
```

<li><b>Herencia protegida:</b> Se refiere a la herencia en la que todos los miembros públicos de la clase base adquieren el nivel de acceso protegido en las clases derivadas, mientras que los miembros protegidos conservan su nivel de acceso. Lo anterior indica que una clase derivada puede luego heredar a otra clase los miembros protegidos que heredó de su clase base.</li>

```C++
class ClaseDerivada : protected ClaseBase
```

<li><b>Herencia privada:</b> Se refiere a la herencia en la que todos los miembros públicos y protegidos de la clase base adquieren el nivel de acceso privado en las clases derivadas. De ahí se desprende que una clase derivada que haya heredado mediante herencia privada no puede heredar a otras clases los miembros que ha heredado de otras clases.</li>

```C++
class ClaseDerivada : private ClaseBase
```
</ul>

# Inicialización de variables heredadas con el constructor de la clase base

La función principal de los constructores de una clase es la de inicializar las varibles de la clase, sin embargo el constructor de una clase derivada no puede inicializar de manera directa las variables que se han heredado de la clase base. Para que el constructor de la clase derivada pueda inicializar las variables heredadas debe invocar al constructor de la clase base. Esto se logra con el operador dos puntos `:` y ejecutando el constructor de la clase base. Observe el ejemplo a continuación:

```C++ runnable
#include<iostream>
using namespace std;

class ClaseBase
{
    protected:
    int unaVar = 0;
    public:
    ClaseBase(int x):unaVar(x){}
    void unMetodo(void)
    {
        cout<<"unaVar = "<<unaVar<<endl;
    }
};

class ClaseDerivada : public ClaseBase  
{
    public:
    ClaseDerivada(int x):ClaseBase(x){} /* Ejecución del constructor de la clase base para inicializar a unaVar */
};

int main()
{
    ClaseDerivada obj1(50); /* Aquí el constructor de la clase derivada invoca el constructor de la clase base */
    obj1.unMetodo(); 
    return 0;
}
```

?[¿Compilaría exitosamente el siguiente programa?]
-[ ] Sí, se imprime: "My name is: Objeto_1" y "My name is: Objeto_2"
-[ ] Sí, pero solo imprime: "My name is: Objeto_1"
-[x] No, hay varios errores en la definición de las herencias. ¿Cuáles? 

```C++
class ClaseBase
{
    protected:
    std::string name = "";
    public:
    ClaseBase(std::string n):name(n){}
    void showName(){cout<<"My name is: "<<name<<endl;}
};

class DerivadaA: private ClaseBase
{
    public:
    DerivadaA(std::string n):name(n){}
};

class DerivadaB: public DerivadaA
{
};

int main()
{
    DerivadaA obj1("Objeto_1");
    DerivadaB obj2("Objeto_2");
    
    obj1.showName();
    obj2.showName();
}
```



