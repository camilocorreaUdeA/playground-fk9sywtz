# Herencia virtual

Visualice una situación en la que hay herencia híbrida dada por la combinanción de herencia jerárquica, herencia múltiple y herencia multinivel. En dicha situación dos clases B y C heredan de una clase A, y asu vez una clase D hereda de las clases B y C al tiempo. La situación puede observarse en el siguiente gráfico y en el siguiente coódigo de ejemplo.Por favor ejecutelo y observe el resultado al final de la ejecución.

<img src="markdowns/class_diamond.png">

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
};

class C: public A
{
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
Como puede observar el código ha sido compilado pero en tiempo de ejecución la llamada al método "unMetodoX" es ambigua ya que la clase D lo hereda directamente de B y C, pero también a través de esas clases lo hereda de la clase A. De modo que no sabe cuál de los 3 debería ejecutar. Esta es una situación poco común en una aplicación real desarrollada en C++ ya que los cánones de buenas prácticas de programación sugieren que se evite a toda costa la herencia múltiple, de hecho otros lenguajes de programación orientada a objetos como por ejemplo Java no permiten implementar herencia múltiple. Pero en caso de que por alguna razón se vea obligado a implmentar una estructura jerárquica de ese tipo se sugiere el uso de la palabra reservada `virtual` en la herencia de las clases intermedias B y C. Lo anterior corrige el problema de la ambigüedad y ya no se dará el error y se ejecutará el método heredado desde la clase A.

```C++ runnable
#include<iostream>
using namespace std;

class A
{
    public:
    void unMetodoX(){cout<<"Soy de la clase A"<<endl;}
};

class B: virtual public A  /* Agregando 'virtual' a la herencia de las clases derivadas intermedias */
{
};

class C: virtual public A /* Agregando 'virtual' a la herencia de las clases derivadas intermedias */
{
};

class D: public B, public C
{
};

int main()
{
    D obj;
    obj.unMetodoX(); /* En este caso no habrá ambigüedad */
    return 0;
};
```
Considere que se implementó la herencia virtual para evitar el problema de ambigüedad, luego responda a las siguientes inquietudes:

?[¿Qué pasa cuándo una de las dos clases B y C (pero no las dos al tiempo) redefine el método unMetodoX?]
-[ ] De nuevo hay ambigüedad
-[ ] Se sigue ejecutando la definición del método en la clase A
-[x] Se ejecuta la redefinición del método en la clase intermedia.
-[ ] Es una situación con un comportamiento indefinido

?[¿Qué pasa cuándo ambas clases B y C redefinen el método unMetodoX?]
-[x] De nuevo hay ambigüedad
-[ ] Se sigue ejecutando la definición del método en la clase A
-[ ] Se ejecuta la redefinición del método en la clase intermedia que está de primera en orden en la herencia de la clase D.
-[ ] Es una situación con un comportamiento indefinido
