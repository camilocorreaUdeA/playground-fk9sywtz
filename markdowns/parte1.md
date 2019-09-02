# Concepto de Herencia

La Herencia es uno de los conceptos fundamentales de la programación orientada a objetos ya que permite la reusabilidad de variables y funcionalidades que se han definido en otras clases. Para hablar de herencia se deben introducir los conceptos de `clase base` y `clase derivada`. Se conoce como clase base a una clase que va a heredar sus propiedades (variables) y funcionalidades (métodos) a otras clases; por otro lado, se conoce como clase derivada a una clase que se implementa mediante la reutilización de las propiedades y funcionalidades que se heredan de una (o varias) clase base. La herencia contribuye en cierto grado con la escalabilidad de una aplicación ya que cuando se debe modificar o eliminar una variable o un método heredado en todas las clases derivadas, entonces no es necesario que se haga individualmente en cada clase sino que se hace directamente en la clase base y las clases derivadas simplmente heredan la actualización de esos miembros.

La herencia en C++ se expresa en la implmentación de una clase mediante el uso del operador dos puntos `:` seguido del tipo de herencia (que lo veremos más adelante) y del nombre de la clase base de la que se busca heredar. Vale anotar que el tipo de herencia por defecto en C++, cuando no se especifica explicitamente ese campo, es la herencia privada. A continuación se observa la implementación más simple del concepto de herencia en C++:

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
    obj1.unMetodo();
    obj1.unMetodo();
    return 0;
}
```
