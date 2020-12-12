---
title: Instrucciones para escribir plantillas de texto T4
description: Obtenga información sobre las directrices generales que resultan útiles si va a generar código de programa u otros recursos de aplicación en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f5f7be4ce9b8beb7699844397de3e1fc206d017c
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363411"
---
# <a name="guidelines-for-writing-t4-text-templates"></a>Instrucciones para escribir plantillas de texto T4

Estas directrices generales pueden resultar útiles si va a generar código de programa u otros recursos de aplicación en Visual Studio. No son reglas fijas.

## <a name="guidelines-for-design-time-t4-templates"></a>Directrices para Design-Time plantillas T4

Las plantillas T4 en tiempo de diseño son plantillas que generan código en el proyecto de Visual Studio en tiempo de diseño. Para obtener más información, vea [Generación de código en tiempo de diseño mediante plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

Generar aspectos variables de la aplicación.

La generación de código es muy útil para los aspectos de la aplicación que pueden cambiar durante el proyecto o cambiará entre versiones diferentes de la aplicación. Separe estos aspectos variables de los aspectos más invariables para que pueda determinar con mayor facilidad lo que se debe generar. Por ejemplo, si la aplicación proporciona un sitio web, separe las funciones de servicio de página estándar de la lógica que define las rutas de navegación de una página a otra.

Codifique los aspectos variables en uno o varios modelos de origen.

Un modelo es un archivo o base de datos que cada plantilla Lee para obtener valores específicos para las partes variables del código que se va a generar. Los modelos pueden ser bases de datos, archivos XML de su propio diseño, diagramas o lenguajes específicos del dominio. Normalmente, se usa un modelo para generar muchos archivos en un proyecto de Visual Studio. Cada archivo se genera a partir de una plantilla independiente.

Puede usar más de un modelo en un proyecto. Por ejemplo, puede definir un modelo para la navegación entre páginas web y un modelo independiente para el diseño de las páginas.

Centre el modelo en las necesidades y el vocabulario de los usuarios, no en su implementación.

Por ejemplo, en una aplicación de sitio web, cabe esperar que el modelo haga referencia a páginas web e hipervínculos.

Idealmente, elija una forma de presentación que se adapte al tipo de información que representa el modelo. Por ejemplo, un modelo de rutas de navegación a través de un sitio web podría ser un diagrama de cuadros y flechas.

Pruebe el código generado.

Use pruebas manuales o automatizadas para comprobar que el código resultante funciona como lo requieren los usuarios. Evite generar pruebas a partir del mismo modelo desde el que se genera el código.

En algunos casos, las pruebas generales se pueden realizar directamente en el modelo. Por ejemplo, puede escribir una prueba que garantice que se puede tener acceso a todas las páginas del sitio web mediante la navegación desde cualquier otro.

Permitir código personalizado: genera clases parciales.

Permite el código que se escribe a mano además del código generado. No es habitual que un esquema de generación de código pueda tener en cuenta todas las posibles variaciones que pueden surgir. Por lo tanto, debe esperar agregar o reemplazar parte del código generado. Cuando el material generado está en un lenguaje .NET como C# o Visual Basic, dos estrategias son especialmente útiles:

- Las clases generadas deben ser parciales. Esto le permite agregar contenido al código generado.

- Las clases deben generarse en pares, una que herede de la otra. La clase base debe contener todos los métodos y propiedades generados, y la clase derivada debe contener solo los constructores. Esto permite que el código escrito a mano invalide cualquiera de los métodos generados.

En otros lenguajes generados como XML, utilice la `<#@include#>` Directiva para crear combinaciones simples de contenido generado y escrito a mano. En casos más complejos, es posible que tenga que escribir un paso posterior al procesamiento que combine el archivo generado con los archivos escritos a mano.

Mueva material común a archivos de inclusión o plantillas en tiempo de ejecución.

Para evitar repetir bloques similares de texto y código en varias plantillas, use la `<#@ include #>` Directiva. Para obtener más información, consulte [la Directiva de inclusión T4](../modeling/t4-include-directive.md).

También puede crear plantillas de texto en tiempo de ejecución en un proyecto independiente y, a continuación, llamarlas desde la plantilla en tiempo de diseño. Para ello, utilice la `<#@ assembly #>` Directiva para tener acceso al proyecto independiente.

Considere la posibilidad de mover grandes bloques de código en un ensamblado independiente.

Si tiene bloques de código y bloques de características de clase de gran tamaño, puede ser útil trasladar parte de este código a métodos que se compilan en un proyecto independiente. Puede utilizar la `<#@ assembly #>` Directiva para tener acceso al código de la plantilla. Para obtener más información, vea [Directiva de ensamblado T4](../modeling/t4-assembly-directive.md).

Puede colocar los métodos en una clase abstracta que la plantilla pueda heredar. La clase abstracta debe heredar de <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName> . Para obtener más información, consulte [Directiva de plantilla T4](../modeling/t4-template-directive.md).

Generar código, no archivos de configuración.

Un método para escribir una aplicación de variables es escribir código de programa genérico que acepte un archivo de configuración. Una aplicación escrita de esta manera es muy flexible y se puede volver a configurar cuando cambien los requisitos empresariales, sin tener que volver a generar la aplicación. Sin embargo, un inconveniente de este enfoque es que la aplicación se ejecutará menos bien que una aplicación más específica. Además, el código del programa será más difícil de leer y mantener, en parte porque siempre tiene que tratar con la mayoría de los tipos genéricos.

Por el contrario, una aplicación cuyas partes variables se generan antes de la compilación puede tener un establecimiento inflexible de tipos. Esto hace que sea mucho más fácil y confiable escribir código escrito a mano e integrarlo con las partes generadas del software.

Para obtener todas las ventajas de la generación de código, intente generar código de programa en lugar de archivos de configuración.

Use una carpeta de código generado.

Coloque las plantillas y los archivos generados en una carpeta de proyecto denominada **código generado**, para aclarar que no son archivos que deben editarse directamente. Si crea código personalizado para invalidar o agregar a las clases generadas, colóquelas en una carpeta denominada **código personalizado**. La estructura de un proyecto típico tiene el siguiente aspecto:

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

## <a name="guidelines-for-run-time-preprocessed-t4-templates"></a>Instrucciones para las plantillas T4 de Run-Time (preprocesadas)

Mueva el material común a las plantillas heredadas.

Puede usar la herencia para compartir métodos y bloques de texto entre plantillas de texto T4. Para obtener más información, consulte [Directiva de plantilla T4](../modeling/t4-template-directive.md).

También puede usar archivos de inclusión que tienen plantillas en tiempo de ejecución.

Mueva grandes cuerpos de código a una clase parcial.

Cada plantilla en tiempo de ejecución genera una definición de clase parcial que tiene el mismo nombre que la plantilla. Puede escribir un archivo de código que contenga otra definición parcial de la misma clase. Puede Agregar métodos, campos y constructores a la clase de esta manera. Se puede llamar a estos miembros desde los bloques de código de la plantilla.

Una ventaja de hacerlo es que el código es más fácil de escribir, ya que IntelliSense está disponible. Además, puede lograr una mejor separación entre la presentación y la lógica subyacente.

Por ejemplo, en **MyReportText.TT**:

`The total is: <#= ComputeTotal() #>`

En **MyReportText-Methods.CS**:

`private string ComputeTotal() { ... }`

Permitir código personalizado: proporcione puntos de extensión.

Considere la posibilidad de generar métodos virtuales en \<#+ class feature blocks #> . Esto permite usar una única plantilla en muchos contextos sin modificarla. En lugar de modificar la plantilla, puede construir una clase derivada que proporcione la lógica adicional mínima. La clase derivada puede ser código normal o puede ser una plantilla en tiempo de ejecución.

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

## <a name="guidelines-for-all-t4-templates"></a>Instrucciones para todas las plantillas T4

Recopilación de datos independientes de la generación de texto.

Intente evitar mezclar el cálculo y los bloques de texto. En cada plantilla de texto, use la primera \<# code block #> para establecer las variables y realizar cálculos complejos. Desde el primer bloque de texto hasta el final de la plantilla o la primera \<#+ class feature block #> , evite expresiones largas y evite los bucles y los condicionales a menos que contengan bloques de texto. Esta práctica facilita la lectura y el mantenimiento de la plantilla.

No use `.tt` para archivos de inclusión.

Use una extensión de nombre de archivo diferente como, por ejemplo, `.ttinclude` para archivos de inclusión. Use `.tt` solo para los archivos que desee procesar como plantillas de texto en tiempo de ejecución o en tiempo de diseño. En algunos casos, Visual Studio reconoce `.tt` los archivos y establece automáticamente sus propiedades para su procesamiento.

Inicie cada plantilla como un prototipo fijo.

Escriba un ejemplo del código o el texto que desea generar y asegúrese de que es correcto. A continuación, cambie su extensión a. TT e inserte de forma incremental el código que modifica el contenido leyendo el modelo.

Considere la posibilidad de usar modelos con tipo.

Aunque puede crear un esquema XML o de base de datos para los modelos, puede ser útil crear un lenguaje específico de dominio (DSL). Un DSL tiene la ventaja de que genera una clase para representar cada nodo en el esquema y las propiedades que representan los atributos. Esto significa que puede programar en función del modelo de negocio. Por ejemplo:

```
Team Members:
<# foreach (Person p in team.Members)
 { #>
    <#= p.Name #>
<# } #>
```

Considere la posibilidad de usar diagramas para los modelos.

Muchos modelos se presentan y administran de forma más eficaz, simplemente como tablas de texto, especialmente si son muy grandes.

Sin embargo, para algunos tipos de requisitos empresariales, es importante aclarar conjuntos complejos de relaciones y flujos de trabajo, y los diagramas son el medio más adecuado. Una ventaja de los diagramas es que resulta fácil hablar con los usuarios y otras partes interesadas. Al generar código a partir de un modelo en el nivel de requisitos empresariales, se hace que el código sea más flexible cuando cambien los requisitos.

También puede diseñar su propio tipo de diagrama como lenguaje específico de dominio (DSL). El código se puede generar a partir de UML y DSL. Para obtener más información, vea [analizar y modelar la arquitectura](../modeling/analyze-and-model-your-architecture.md).

## <a name="see-also"></a>Consulta también

- [Generación de código en tiempo de diseño usando las plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
- [Generación de texto en tiempo de ejecución con plantillas de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md)
