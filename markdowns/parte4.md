# Clases Abstractas e Interfaces

Una clase abstracta es aquella de la que no se pueden declarar instancias, dicho de otra manera no se pueden declarar objetos de una clase abstracta. La finalidad de una clase abstracta es servir como clase base para otras clases a las que generalmente se conoce como clases "concretas". La característica que distingue a una clase abstracta es la de poseer por lo menos un método virtual puro, y de manera equivalente cualquier clase que tenga por lo menos un método virtual puro es considerada abstracta y no pueden declararse objetos de esa clase. Un método virtual puro es un método que ha sido declarado en la clase abstracta base pero que su definición (y redefinición) se deja a las clases concretas que le heredan. <b>NOTA</b>: Si una clase cualquiera hereda de una clase abstracta y no define los métodos virtuales puros heredados entonces esa clase automáticamente se convierte en una clase abstracta también.

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
};

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
};
```

Una interfaz es una clase abstracta pura ya que no tiene variables de clase ni métodos concretos, todos sus métodos son virtuales puros. Este tipo de clases son implementadas comunmente por los arquitectos y diseñadores de software, representan un contrato entre el diseñador y el usuario o desarrollador final de cierta funcionalidad, es decir, en una interfaz el diseñador especifica el nombre del y posiblemente el tipo de retorno y los tipos de los parámetros de entrada del método pero deja a consideración del desarrollador la implementación interna de la funcionalidad. El uso de interfaces es particularmente útil cuando se implementan algunos patrones de diseño de software que involucran clases polimórficas (tema que se trata en la próxima práctica), lo cual es muy común en "frameworks" de desarrollo de software, por ejemplo de interfaces gráficas de usuario (GUIs) donde la mayoría de objetos gráficos que se pueden integrar a la interfaz gráfica implementan interfaces en común que declaran funcionalidades generales de todos los elementos gráficos pero que se implementan con distintas variaciones en cada uno de los elementos gráficos. Ejemplo:

```cpp

/* Interfaz o clase abstracta pura */
class ElementoGraficoGenerico
{
    public:
    virtual void setColor(const double r, const double g, const double b) = 0;
    virtual void setPos(double xpos, double ypos) = 0;
    virtual void setLabel(const string lb) = 0;
    virtual void onClickPressed() = 0;
};

class LineaTexto: public ElementoGraficoGenerico
{
    /* Implementación específica de los métodos virtuales puros heredados */
};

class BotonOKCancel: public ElementoGraficoGenerico
{
    /* Implementación específica de los métodos virtuales puros heredados */
};

class CheckBox: public ElementoGraficoGenerico
{
    /* Implementación específica de los métodos virtuales puros heredados */
};
```
Comprueba lo aprendido...

?[¿Qué pasa cuando una clase implementa un mismo método virtual puro heredado de dos interfaces al mismo tiempo como se muestra en el siguiente fragmento de código?]
-[ ] El compilador arroja un error
-[ ] La clase Concreta es abstracta también porque solo implementa uno de los métodos puros virtuales
-[x] El código compila satisfactoriamente y se imprime en pantalla "Método Virtual Puro Redefinido"
-[ ] Hay una ambigüedad en el método por estar declarado en dos clases al mismo tiempo.

```cpp
class Interfaz1
{
	public:
    virtual void metodoVirtualPuro() const = 0;
};

class Interfaz2
{
	public:
    virtual void metodoVirtualPuro() const = 0;
};

class Concreta: public Interfaz1, public Interfaz2
{
	public:
    void metodoVirtualPuro() const{cout<<"Metodo Virtual Puro Redefinido"<<endl;}
};

int main()
{
	Concreta miObj;
	miObj.metodoVirtualPuro();
	return 0;
}
```






