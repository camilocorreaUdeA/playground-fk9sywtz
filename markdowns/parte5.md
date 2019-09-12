# Herencia virtual

Visualice una situación en la que hay herencia híbrida dada por la combinanción de herencia jerárquica, herencia múltiple y herencia multinivel. En dicha situación dos clases B y C heredan de una clase A, y asu vez una clase D hereda de las clases B y C al tiempo. La situación puede observarse en el siguiente ejemplo, ejecutelo y observe el resultado del proceso de compilación.

```C++ runnable
#include<iostream>
using namespace std;

class A
{
    public:
    void unMetodoX(){cout<<"Soy de la clase A"<<endl;}
};

class B: public A  
{
    public:
    void unMetodoX(){cout<<"Soy de la clase B"<<endl;}
};

class C: public A
{
    public:
    void unMetodoX(){cout<<"Soy de la clase C"<<endl;}
};

class D: public B, public C
{
};

int main()
{
    D obj;
    obj.unMetodoX();
    return 0;
};
```
Como puede observar el código ha sido compilado pero en tiempo de ejecución la llamada al método "unMetodoX" es ambigua ya que la clase D lo hereda directamente de B y C, pero también a través de esas clases lo hereda de la clase A. De modo que no sabe cuál de los 3 debería ejecutar. Esta es una situación poco común en una aplicación real desarrollada en C++ ya que los cánones de buenas prácticas de programación sugieren que se evite a toda costa la herencia múltiple, de hecho otros lenguajes de programación orientada a objetos como por ejemplo Java no permiten implementar herencia múltiple. Pero en caso de que por alguna razón se vea obligado a implmentar una estructura jerárquica de ese tipo se sugiere el uso de la palabra reservada `virtual` en la herencia de las clases intermedias B y C. Lo anterior corrige el problema de la ambigüedad y ya no se dará el error, pero resta un aspecto y este depende enteramente del compilador ¿Cuál de todos los métodos será el escogido para correr en tiempo de ejecución?

```C++ runnable
#include<iostream>
using namespace std;

class A
{
    public:
    void unMetodoX(){cout<<"Soy de la clase A"<<endl;}
};

class B: virtual public A  
{
    public:
    void unMetodoX(){cout<<"Soy de la clase B"<<endl;}
};

class C: virtual public A
{
    public:
    void unMetodoX(){cout<<"Soy de la clase C"<<endl;}
};

class D: public B, public C
{
};

int main()
{
    D obj;
    obj.unMetodoX();
    return 0;
};
```
