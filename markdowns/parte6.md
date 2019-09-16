# Ejercicios Prácticos

<ol>
<li>
Una utilidad interesante e importante de la herencia que se manifiesta a través del uso de interfaces (clases virtuales puras) es que existe la posibilidad de crear funciones "genéricas" que pueden invocar los métodos de distintas clases al tiempo, siempre y cuando dichas clases estén relacionadas a través herencia teniendo como ancestro en común una misma interfaz. Implemente las siguientes clases:

<ul>
<li>Una interfaz SerVivo que tiene los siguientes métodos virtuales puros: Respiro, MeAlimento, Habito, MeReproduzco, MeDesplazo. Estos métodos no tienen parámetros de entrada ni retornan valor alguno.
</ul>
<li>
Las clases Ave, Mamifero, Reptil, Anfibio, Pez e Insecto que heredan de la interfaz SerVivo. Estas clases deben contener variables privadas heradables para los atributos característicos de cada especie, por ejemplo: número de patas, si tiene alas, tipo de piel (pelaje, plumas, escamas, etc.), si es acuático, terrestre o aéreo, si pone huevos o no, si tiene branquias o nariz, si camina, nada o vuela, lugar que habita (selvas, lagos, árboles, etc.), tipo de alimentación (si es carnívoro, herbívoro, etc.), de que se alimenta (frutos, hierba, otros animales), si es venenoso o no, etc. Estas clases deben contar con constructores públicos (parametrizado o de copia) para inicializar todas las variables. 
</li>
<li>
Implemente una clase que herede de cada una de las clases del punto anterior, ejemplo: Sardina hereda de Pez y así con las demás clases. Estas clases deben contar con variables de clase para almacenar atributos adicionales que los diferencien de otros seres vivos de su misma especie (por ejemplo: un león y un orangután son ambos mamíferos pero son completamente distintos). Estas clases deben implementar los métodos heredados de la interfaz SerVivo para que impriman un informe con la información concerniente a la temática a la que refiere el título del método, por ejemplo una clase Chimpance en su método Habito debería imprimir: "Los chimpances habitamos generalmente en: " + valor_variable_lugar_que_habita (que podría tener uno de estos valores por ejemplo: "bosques de montaña", "montañas del sudeste Africano", etc.). Estas clases deben contar con constructores públicos (parametrizado o de copia) para la incialización de todas las variables que almacenan las características del ser vivo en particular.
</li>
<li>
Implemente una función ImprimirConsolidadoSerVivo que no tiene valor de retorno y recibe como parámetro de entrada una referencia a un objeto del tipo de la interfaz SerViVo. Esta función invoca los métodos de las clases anteriores a través del objeto que se le pasa por referencia, dando como resultado la impresión de las distintas características que prevalecen en un ser vivo en particular de cierta especie.
</li>
<li>
En una pequela aplicación instancie objetos para cada una de las clases de ser vivo que haya diseñado y luego invoque la función ImprimirConsolidadoSerVivo para cada uno de estos objetos.
</li>
</li>
</ol>
