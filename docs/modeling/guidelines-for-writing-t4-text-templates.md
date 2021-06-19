---
title: Instrucciones para escribir plantillas de texto T4
description: Conozca las directrices generales que son útiles si está generando código de programa u otros recursos de aplicación en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4f043e95ef477558028e634bf6b48aded2960ec2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386662"
---
# <a name="guidelines-for-writing-t4-text-templates"></a>Instrucciones para escribir plantillas de texto T4

Estas directrices generales pueden ser útiles si está generando código de programa u otros recursos de aplicación en Visual Studio. No son reglas fijas.

## <a name="guidelines-for-design-time-t4-templates"></a>Directrices para Design-Time plantillas T4

Las plantillas T4 en tiempo de diseño son plantillas que generan código en el Visual Studio proyecto en tiempo de diseño. Para obtener más información, vea [Generación de código en tiempo de diseño mediante plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

Generar aspectos variables de la aplicación.

La generación de código es más útil para los aspectos de la aplicación que pueden cambiar durante el proyecto o cambiarán entre distintas versiones de la aplicación. Separe estos aspectos variables de los aspectos más invariables para que pueda determinar más fácilmente lo que se debe generar. Por ejemplo, si la aplicación proporciona un sitio web, separe las funciones de servicio de página estándar de la lógica que define las rutas de navegación de una página a otra.

Codifica los aspectos de las variables en uno o varios modelos de origen.

Un modelo es un archivo o base de datos que cada plantilla lee para obtener valores específicos para las partes variables del código que se va a generar. Los modelos pueden ser bases de datos, archivos XML de su propio diseño, diagramas o lenguajes específicos del dominio. Normalmente, un modelo se usa para generar muchos archivos en un Visual Studio proyecto. Cada archivo se genera a partir de una plantilla independiente.

Puede usar más de un modelo en un proyecto. Por ejemplo, puede definir un modelo para la navegación entre páginas web y un modelo independiente para el diseño de las páginas.

Centre el modelo en las necesidades y el vocabulario de los usuarios, no en la implementación.

Por ejemplo, en una aplicación de sitio web, esperaría que el modelo haga referencia a páginas web e hipervínculos.

Idealmente, elija una forma de presentación que se adapte al tipo de información que representa el modelo. Por ejemplo, un modelo de rutas de navegación a través de un sitio web podría ser un diagrama de cuadros y flechas.

Pruebe el código generado.

Use pruebas manuales o automatizadas para comprobar que el código resultante funciona según lo requieran los usuarios. Evite generar pruebas a partir del mismo modelo a partir del cual se genera el código.

En algunos casos, las pruebas generales se pueden realizar directamente en el modelo. Por ejemplo, podría escribir una prueba que garantice que se pueda acceder a todas las páginas del sitio web mediante la navegación desde cualquier otra.

Permitir código personalizado: generar clases parciales.

Permita el código que escriba a mano además del código generado. No es habitual que un esquema de generación de código pueda tener en cuenta todas las variaciones posibles que puedan surgir. Por lo tanto, debe esperar agregar o invalidar parte del código generado. Cuando el material generado está en un lenguaje .NET como C# o Visual Basic, dos estrategias son especialmente útiles:

- Las clases generadas deben ser parciales. Esto le permite agregar contenido al código generado.

- Las clases se deben generar en pares, una que hereda de la otra. La clase base debe contener todos los métodos y propiedades generados, y la clase derivada solo debe contener los constructores. Esto permite que el código escrito a mano invalide cualquiera de los métodos generados.

En otros lenguajes generados, como XML, use la directiva para realizar combinaciones sencillas de contenido escrito a mano `<#@include#>` y generado. En casos más complejos, es posible que tenga que escribir un paso posterior al procesamiento que combine el archivo generado con cualquier archivo escrito a mano.

Mueva el material común a archivos de incluyeción o plantillas en tiempo de ejecución.

Para evitar repetir bloques similares de texto y código en varias plantillas, use la `<#@ include #>` directiva . Para obtener más información, vea [T4 Include Directive](../modeling/t4-include-directive.md).

También puede compilar plantillas de texto en tiempo de ejecución en un proyecto independiente y, a continuación, llamarlas desde la plantilla en tiempo de diseño. Para ello, use la `<#@ assembly #>` directiva para acceder al proyecto independiente.

Considere la posibilidad de mover grandes bloques de código a un ensamblado independiente.

Si tiene bloques de código grandes y bloques de características de clase, puede resultar útil mover parte de este código a métodos que compile en un proyecto independiente. Puede usar la directiva `<#@ assembly #>` para acceder al código de la plantilla. Para obtener más información, vea [T4 Assembly Directive](../modeling/t4-assembly-directive.md).

Puede colocar los métodos en una clase abstracta que la plantilla pueda heredar. La clase abstracta debe heredar de <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName> . Para obtener más información, vea [Directiva de plantilla T4.](../modeling/t4-template-directive.md)

Generar código, no archivos de configuración.

Un método para escribir una aplicación variable es escribir código de programa genérico que acepte un archivo de configuración. Una aplicación escrita de esta manera es muy flexible y se puede volver a configurar cuando cambian los requisitos empresariales, sin volver a generar la aplicación. Sin embargo, un inconveniente de este enfoque es que la aplicación tendrá menos rendimiento que una aplicación más específica. Además, su código de programa será más difícil de leer y mantener, en parte porque siempre tiene que tratar con los tipos más genéricos.

Por el contrario, una aplicación cuyas partes variables se generan antes de la compilación se puede escribir fuertemente. Esto hace que sea mucho más fácil y confiable escribir código escrito a mano e integrarlo con las partes generadas del software.

Para obtener todas las ventajas de la generación de código, intente generar código de programa en lugar de archivos de configuración.

Use una carpeta Código generado.

Coloque las plantillas y los archivos generados en una carpeta de proyecto denominada **Código** generado para dejar claro que no se trata de archivos que se deben editar directamente. Si crea código personalizado para invalidar o agregar a las clases generadas, coloque esas clases en una carpeta denominada **Código personalizado**. La estructura de un proyecto típico tiene el siguiente aspecto:

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

## <a name="guidelines-for-run-time-preprocessed-t4-templates"></a>Directrices para Run-Time plantillas T4 (preprocesadas)

Mueva el material común a plantillas heredadas.

Puede usar la herencia para compartir métodos y bloques de texto entre plantillas de texto T4. Para obtener más información, vea [Directiva de plantilla T4.](../modeling/t4-template-directive.md)

También puede usar archivos de incluir que tengan plantillas en tiempo de ejecución.

Mover grandes cuerpos de código a una clase parcial.

Cada plantilla en tiempo de ejecución genera una definición de clase parcial que tiene el mismo nombre que la plantilla. Puede escribir un archivo de código que contenga otra definición parcial de la misma clase. Puede agregar métodos, campos y constructores a la clase de esta manera. Se puede llamar a estos miembros desde los bloques de código de la plantilla.

Una ventaja de hacerlo es que el código es más fácil de escribir, ya que IntelliSense está disponible. Además, puede lograr una mejor separación entre la presentación y la lógica subyacente.

Por ejemplo, en **MyReportText.tt**:

`The total is: <#= ComputeTotal() #>`

En **MyReportText-Methods.cs**:

`private string ComputeTotal() { ... }`

Permitir código personalizado: proporcione puntos de extensión.

Considere la posibilidad de generar métodos virtuales en \<#+ class feature blocks #> . Esto permite usar una sola plantilla en muchos contextos sin modificaciones. En lugar de modificar la plantilla, puede construir una clase derivada que proporciona la lógica adicional mínima. La clase derivada puede ser código normal o puede ser una plantilla en tiempo de ejecución.

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

Separar la recopilación de datos de la generación de texto.

Intente evitar la combinación de bloques de cálculo y texto. En cada plantilla de texto, use la primera \<# code block #> para establecer variables y realizar cálculos complejos. Desde el primer bloque de texto hasta el final de la plantilla o la primera , evite expresiones largas y evite bucles y condicionales a menos que contengan \<#+ class feature block #> bloques de texto. Esta práctica facilita la lectura y el mantenimiento de la plantilla.

No use para `.tt` incluir archivos.

Use una extensión de nombre de archivo diferente, como `.ttinclude` para los archivos de incluir. Use solo para los archivos que quiera procesar como plantillas de texto en tiempo de ejecución o en `.tt` tiempo de diseño. En algunos casos, Visual Studio reconoce `.tt` archivos y establece automáticamente sus propiedades para su procesamiento.

Inicie cada plantilla como un prototipo fijo.

Escriba un ejemplo del código o texto que desea generar y asegúrese de que es correcto. A continuación, cambie su extensión a .tt e inserte de forma incremental código que modifique el contenido mediante la lectura del modelo.

Considere la posibilidad de usar modelos con tipo.

Aunque puede crear un esquema XML o de base de datos para los modelos, puede resultar útil crear un lenguaje específico de dominio (DSL). Un DSL tiene la ventaja de que genera una clase para representar cada nodo del esquema y las propiedades para representar los atributos. Esto significa que puede programar en términos del modelo de negocio. Por ejemplo:

```
Team Members:
<# foreach (Person p in team.Members)
 { #>
    <#= p.Name #>
<# } #>
```

Considere la posibilidad de usar diagramas para los modelos.

Muchos modelos se presentan y administran de forma más eficaz simplemente como tablas de texto, especialmente si son muy grandes.

Sin embargo, para algunos tipos de requisitos empresariales, es importante aclarar conjuntos complejos de relaciones y flujos de trabajo, y los diagramas son el medio más adecuado. Una ventaja de un diagrama es que es fácil de analizar con los usuarios y otras partes interesadas. Al generar código a partir de un modelo en el nivel de requisitos empresariales, el código se hace más flexible cuando cambian los requisitos.

También puede diseñar su propio tipo de diagrama como un lenguaje específico del dominio (DSL). El código se puede generar a partir de UML y DSL. Para obtener más información, vea [Analizar y modelar arquitectura.](../modeling/analyze-and-model-your-architecture.md)

## <a name="see-also"></a>Vea también

- [Generación de código en tiempo de diseño usando las plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
- [Generación de texto en tiempo de ejecución con plantillas de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md)
