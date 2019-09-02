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
	        
	    cout<<endl;
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

# Orden de ejecución de constructores y destructores en una clase derivada

Cuando se instancia un objeto del tipo de una clase derivada se ejecuta de manera implícita el constructor de la clase base justo antes de que se ejecute el constructor de la clase derivada. De manera análoga sucede con los destructores, pero en este caso se ejecuta primero el destructor de la clase derivada y luego el constructor de la clase base. El siguiente ejemplo ilustra el comportamiento descrito:


```C++ runnable
#include<iostream>
using namespace std;

class ClaseBase
{
    public:
    static int inst;
	ClaseBase()
	{
	    cout<<"Hola, soy la clase Base"<<endl;
    }
    
    ~ClaseBase()
	{
	    cout<<"Adios, era la clase Base"<<endl;
    }
};

int ClaseBase::inst = 0;

class ClaseDerivada: public ClaseBase
{
    public:
	ClaseDerivada()
	{
	    cout<<"Hola, soy la clase Derivada obj"<<(++inst)<<endl;
    }
    
    ~ClaseDerivada()
	{
	    cout<<"Adios, era la clase Derivada obj"<<(++inst)<<endl;
    }
};

int main()
{
	ClaseDerivada obj1;
	{
	    ClaseDerivada obj2;
	}
	return 0;
}
