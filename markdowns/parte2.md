# Redefinición de métodos

Los métodos que se heredan de una clase base no necesariamente deben conservar la misma definición/implementación en las clases derivadas, es decir, un método heredado puede ser redefinido en la clase derivada de modo que se conserve la misma firma (declaración) pero que el código que implementa la funcionalidad sea distinto, o bien agregue modificaciones a la implementación original de la clase base. Ejemplo:

```C++ runnable
#include<iostream>
using namespace std;

class ClaseBase
{
    public:
	void unMetodoCualquiera(std::string str)
	{
	    for(int i=0; i<str.size(); ++i)
	        cout<<str[i]<<"__";
	       
	    cout<<times<<endl;
	}
};

class ClaseDerivada: public ClaseBase
{
    public:
	void unMetodoCualquiera(std::string str)
	{
	    for(int i=0; i<5; ++i)
	        cout<<str<<endl;
	}
};

int main()
{
	ClaseBase miObjeto;
	ClaseDerivada otroObjeto;
	miObjeto.unMetodoCualquiera("Programacion");
	cout<<"------------------------------------------"<<endl;
	otroObjeto.unMetodoCualquiera("Programacion");
	return 0;
}
```
