# Herencia virtual

Visualice una situación en la que hay herencia híbrida dada por la combinanción de herencia jerárquica, herencia múltiple y herencia multinivel. En dicha situación dos clases B y C heredan de una clase A, y asu vez una clase D hereda de las clases B y C al tiempo. La situación puede observarse en el siguiente ejemplo, ejecutelo y observe el resultado del proceso de compilación.

```C++ runnable
#include<iostream>

class A
{
    public:
    void unMetodoX(){}
};

class B: public A  
{
    public:
    void unMetodoY(){}
};

class C: public A
{
    public:
    void unMetodoZ(){}
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
