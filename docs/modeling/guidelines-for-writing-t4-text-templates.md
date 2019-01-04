---
title: Instrucciones para escribir plantillas de texto T4
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: c0b7e1c151333a3afd0fe93fe533913f6f6d3fbd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53911629"
---
# <a name="guidelines-for-writing-t4-text-templates"></a>Instrucciones para escribir plantillas de texto T4
Estas directrices generales pueden resultar útiles si va a generar código de programa u otros recursos de la aplicación en Visual Studio. Las reglas no son fijas.

## <a name="guidelines-for-design-time-t4-templates"></a>Directrices para las plantillas T4 en tiempo de diseño
 Plantillas T4 en tiempo de diseño son plantillas que generan código en el proyecto de Visual Studio en tiempo de diseño. Para obtener más información, consulte [generación de código de tiempo de diseño mediante el uso de plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

 Genere aspectos variables de la aplicación.
Generación de código es muy útil para los aspectos de la aplicación que pueden cambiar durante el proyecto o cambiará entre diferentes versiones de la aplicación. Separar estos aspectos variables de los aspectos más invariables para que se puede determinar con mayor facilidad lo que se va a generar. Por ejemplo, si la aplicación proporciona un sitio Web, separe la página estándar que proporciona funciones de la lógica que define las rutas de navegación de una página a otra.

 Codifique los aspectos variables en uno o varios modelos de origen.
Un modelo es un archivo o una base de datos que lee cada plantilla para obtener los valores específicos para las partes variables del código que se va a generar. Los modelos pueden ser bases de datos, archivos XML de su propio diseño, los diagramas o lenguajes específicos de dominio. Normalmente, un modelo se usa para generar varios archivos en un proyecto de Visual Studio. Cada archivo se genera a partir de una plantilla independiente.

 Puede usar más de un modelo en un proyecto. Por ejemplo, podría definir un modelo para la navegación entre páginas web y un modelo independiente para el diseño de las páginas.

 Centrar el modelo de necesidades de los usuarios y el vocabulario y no de su implementación.
Por ejemplo, en una aplicación de sitio Web, cabría esperar el modelo para hacer referencia a las páginas web e hipervínculos.

 Lo ideal es elegir un formato de presentación que se adapte a la clase de información que representa el modelo. Por ejemplo, un modelo de rutas de navegación a través de un sitio Web podría ser un diagrama de cuadros y flechas.

 Probar el código generado.
Use pruebas manuales o automatizadas para comprobar que el código resultante funciona según los usuarios necesitan. Evite la generación de pruebas desde el mismo modelo desde el que se genera el código.

 En algunos casos, las pruebas generales pueden realizarse directamente en el modelo. Por ejemplo, podría escribir una prueba que garantiza que todas las páginas en el sitio Web se pueden llegar desde desde cualquier otro.

 Permitir código personalizado: generar clases parciales.
Permitir el código que se escribe a mano además del código generado. Es raro que un esquema de generación de código que pueda tener en cuenta todas las variaciones posibles que pueden surgir. Por lo tanto, debe esperar agregar o reemplazar parte del código generado. Donde el material generado está en un lenguaje .NET como [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], dos estrategias son especialmente útiles:

- Las clases generadas deben ser parciales. Esto permite agregar contenido al código generado.

- Las clases deben generarse en parejas, uno heredar de la otra. La clase base debe contener todos los métodos generados y las propiedades y la clase derivada debe contener solo los constructores. Esto permite que el código escrito a mano reemplazar cualquiera de los métodos generados.

  En otros lenguajes generados como XML, utilice el `<#@include#>` directiva para realizar combinaciones simples de contenido escrito a mano y generado. En casos más complejos, es posible que deba escribir un paso posterior al procesamiento que combina el archivo generado con los archivos escritos a mano.

  Mover material común a los archivos de inclusión o plantillas en tiempo de ejecución para evitar repetir similar bloques de texto y código en varias plantillas, usan el `<#@ include #>` directiva. Para obtener más información, consulte [directiva Include de T4](../modeling/t4-include-directive.md).

  Puede también crear plantillas de texto en tiempo de ejecución en un proyecto independiente y, a continuación, llame a partir de la plantilla en tiempo de diseño. Para ello, use el `<#@ assembly #>` directiva de acceso al proyecto independiente. Para obtener ejemplos, vea ["Herencia en plantillas de texto" en el Blog de Gareth Jones](http://go.microsoft.com/fwlink/?LinkId=208373).

  Considere la posibilidad de mover grandes cantidades de código en un ensamblado independiente.
  Si dispone de los bloques de código de gran tamaño y bloques de características de clase, podría ser útil mover parte de este código en métodos que se compilación en un proyecto independiente. Puede usar el `<#@ assembly #>` directiva tener acceso al código en la plantilla. Para obtener más información, consulte [directiva de ensamblado T4](../modeling/t4-assembly-directive.md).

  Puede colocar los métodos en una clase abstracta que puede heredar la plantilla. La clase abstracta debe heredar de <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName>. Para obtener más información, consulte [directiva de plantilla T4](../modeling/t4-template-directive.md).

  Generar código, no archivos un método de configuración de la escritura de una aplicación de la variable es escribir código de programa genérico que acepta un archivo de configuración. Una aplicación escrita de esta manera es muy flexible y puede configurarse cuando cambian los requisitos empresariales, sin volver a generar la aplicación. Sin embargo, un inconveniente de este enfoque es que la aplicación llevará a cabo bien que una aplicación más específica. Además, su código de programa será más difícil de leer y mantener, en parte porque siempre tiene que tratar con los tipos genéricos más.

  Por el contrario, una aplicación cuyas partes variables se generan antes de la compilación puede estar fuertemente tipada. Esto facilita mucho más fáciles y más confiables para escribir código escrito a mano y cómo integrarlo con generado partes del software.

  Para obtener todas las ventajas de la generación de código, intente generar código de programa en lugar de los archivos de configuración.

  Use una carpeta Generated Code coloque las plantillas y los archivos generados en una carpeta de proyecto denominada **código generado**, para asegurarse de desactive que estos no son archivos que deben editarse directamente. Si crea código personalizado para invalidar o agregar a las clases generadas, coloque estas clases en una carpeta que se denomina **código personalizado**. La estructura de un proyecto típico tiene este aspecto:

```
MyProject
   Custom Code
      Class1.cs
      Class2.cs
   Generated Code
      Class1.tt
          Class1.cs
      Class2.tt
          Class2.cs
   AnotherClass.cs
```

## <a name="guidelines-for-run-time-preprocessed-t4-templates"></a>Directrices para las plantillas T4 de tiempo de ejecución (preprocesada)
 Mover material común en las plantillas heredadas puede usar la herencia para compartir los métodos y los bloques de texto entre las plantillas de texto T4. Para obtener más información, consulte [directiva de plantilla T4](../modeling/t4-template-directive.md).

 También puede usar incluyen archivos que tienen plantillas en tiempo de ejecución.

 Mover grandes cantidades de código en una clase parcial.
Cada plantilla en tiempo de ejecución genera una definición de clase parcial que tiene el mismo nombre que la plantilla. Puede escribir un archivo de código que contiene otra definición parcial de la misma clase. Puede agregar métodos, campos y constructores para la clase de esta manera. Estos miembros pueden llamarse desde los bloques de código en la plantilla.

 Una ventaja de hacerlo es que el código es más fácil de escribir, porque IntelliSense está disponible. Además, puede lograr una mejor separación entre la presentación y la lógica subyacente.

 Por ejemplo, en **MyReportText.tt**:

 `The total is: <#= ComputeTotal() #>`

 En **MyReportText Methods.cs**:

 `private string ComputeTotal() { ... }`

 Permitir código personalizado: proporcionar puntos de extensión que considere la posibilidad de generación de métodos virtuales en \<bloquea la característica de clase #+ #>. Esto permite que una sola plantilla para su uso en muchos contextos sin ninguna modificación. En lugar de modificar la plantilla, puede construir una clase derivada que proporciona la lógica adicional mínima. La clase derivada puede ser cualquier código normal, o puede ser una plantilla en tiempo de ejecución.

 Por ejemplo, en MyStandardRunTimeTemplate.tt:

```
This page is copyright <#= CompanyName() #>.
<#+ protected virtual string CompanyName() { return ""; } #>
```

 En el código de una aplicación:

```
class FabrikamTemplate : MyStandardRunTimeTemplate
{
  protected override string CompanyName() { return "Fabrikam"; }
}
...
  string PageToDisplay = new FabrikamTemplate().TextTransform();
```

## <a name="guidelines-for-all-t4-templates"></a>Directrices para todas las plantillas T4
 Recopilación de datos independiente de la generación de texto intentan evitar la mezcla de cálculo y bloques de texto. En cada plantilla de texto, use la primera \<código # Bloquear #> para establecer las variables y realizar cálculos complejos. Desde el primer bloque de texto hasta el final de la plantilla o la primera \<característica de clase #+ Bloquear #>, evitar expresiones largas y evitar instrucciones condicionales y bucles a menos que contengan los bloques de texto. Esta práctica hace que sea más fácil de leer y mantener la plantilla.

 No use `.tt` para incluir archivos de usan una extensión de nombre de archivo diferente, como `.ttinclude` archivos de inclusión. Use `.tt` solamente los archivos que desea que se puede procesan las plantillas de texto como tiempo de ejecución o tiempo de diseño. En algunos casos, Visual Studio reconoce `.tt` archivos y automáticamente se establecen sus propiedades para su procesamiento.

 Cada plantilla de inicio como un prototipo fijo.
Escribir un ejemplo del código o el texto que desea generar y asegúrese de que es correcta. A continuación, cambie su extensión a .tt e incrementalmente insertar código que modifica el contenido, lea el modelo.

 Considere la posibilidad de usar modelos tipados.
Aunque puede crear un esquema XML o base de datos para los modelos, podría ser útil crear un lenguaje específico de dominio (DSL). Un DSL no tiene la ventaja que genera una clase para representar cada nodo en el esquema y propiedades para representar los atributos. Esto significa que se puede programar en términos del modelo de negocio. Por ejemplo:

```
Team Members:
<# foreach (Person p in team.Members)
 { #>
    <#= p.Name #>
<# } #>
```

 Considere el uso de diagramas para los modelos.
Muchos modelos se presenta la forma más eficaz y se administran simplemente como tablas de texto, especialmente si son muy grandes.

 Sin embargo, para algunos tipos de requisitos empresariales, es importante aclarar conjuntos complejos de relaciones y flujos de trabajo y los diagramas son el mejor medio adecuado. Una ventaja de un diagrama es que resulta fácil de tratar con los usuarios y otras partes interesadas. Al generar código a partir de un modelo en el nivel de los requisitos empresariales, hará que el código más flexible cuando cambien los requisitos.

 También puede diseñar su propio tipo de diagrama como un lenguaje específico de dominio (DSL). Puede generar código de UML y lenguajes DSL. Para obtener más información, consulte [analizar y modelar la arquitectura](../modeling/analyze-and-model-your-architecture.md).

## <a name="see-also"></a>Vea también

- [Generación de código en tiempo de diseño mediante plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
- [Generación de texto en tiempo de ejecución con plantillas de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md)
