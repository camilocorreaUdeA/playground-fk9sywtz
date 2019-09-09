# Clases Abstractas e Interfaces

Una clase abstracta es aquella de la que no se pueden declarar instancias, dicho de otra manera no se pueden declarar objetos de una clase abstracta. La finalidad de una clase abstracta es servir como clase base para otras clases a las que generalmente se conoce como clases "concretas". La característica que distingue a una clase abstracta es la de poseer por lo menos un método virtual puro, y de manera equivalente cualquier clase que tenga por lo menos un método virtual puro es considerada abstracta y no pueden declararse objetos de esa clase. Un método virtual puro es un método que ha sido declarado en la clase abstracta base pero que su definición (y redefinición) se deja a las clases concretas que le heredan. NOTA: Si una clase cualquiera hereda de una clase abstracta y no define los métodos virtuales puros heredados entonces esa clase automáticamente se convierte en una clase abstracta también.

Un método virtual puro es un método que se declara utilizando la palabra reservada `virtual` e igualando su definición a cero (sí, utilizando el operador de asignación `=` en la declaración del método). De modo que este método se define en las clases concretas herederas. Observe la implementación de una clase abstracta y una clase concreta en el ejemplo a continuación:

```cpp
class Poligono
{
    int num_lados;
    public:
    void setNumLados(int n){ num_lados = n; } /* Método concreto */
    virtual double calcularArea() = 0; /* Método virtual puro o abstracto */
    virtual double calcularPerimetro() = 0; /* Método virtual puro o abstracto */
};

class Triangulo: public Poligono
{
    public:
    double calcularArea()
    {
        /* Implementacion específica de la clase Triangulo */
    }
    
    double calcularPerimetro()
    {
        /* Implementacion específica de la clase Triangulo */
    }
}

class Hexagono: public Poligono
{
    public:
    double calcularArea()
    {
        /* Implementacion específica de la clase Hexagono */
    }
    
    double calcularPerimetro()
    {
        /* Implementacion específica de la clase Hexagono */
    }
}
```


