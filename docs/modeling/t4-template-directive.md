---
title: Directiva de plantilla T4
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 56332c58c48903a13a5b1538cf18986ba81e20a7
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60059011"
---
# <a name="t4-template-directive"></a>Directiva de plantilla T4

Una plantilla de texto T4 de Visual Studio normalmente comienza con un `template` directiva, que especifica cómo se debe procesar la plantilla. No debería haber más de una directiva de plantilla en una plantilla de texto y cualquier archivo que incluye.

Para obtener una descripción general de la escritura de plantillas de texto, consulte [escribir una plantilla de texto T4](../modeling/writing-a-t4-text-template.md).

## <a name="using-the-template-directive"></a>Usar la directiva de plantilla

```
<#@ template [language="VB"] [compilerOptions="options"] [culture="code"] [debug="true"] [hostspecific="true"] [inherits="templateBaseClass"] [visibility="internal"] [linePragmas="false"] #>
```

La directiva `template` tiene varios atributos que permiten especificar distintos aspectos de la transformación. Todos los atributos son opcionales.

## <a name="compileroptions-attribute"></a>compilerOptions (atributo)

Ejemplo:

`compilerOptions="optimize+"`

Valores válidos:

Cualquier opción del compilador válida.

Se omite para plantillas (preprocesadas) en tiempo de ejecución.

Estas opciones se aplican cuando la plantilla se ha convertido en [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] o [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)], y el código resultante está compilado.

## <a name="culture-attribute"></a>culture (atributo)

Ejemplo:

`culture="de-CH"`

Valores válidos:

"", la referencia cultural, que es la predeterminada.

Una referencia cultural expresada como una cadena con el formato xx-XX. Por ejemplo, es-ES, ja-JP, de-CH, de-DE. Para obtener más información, consulta <xref:System.Globalization.CultureInfo?displayProperty=fullName>.

El atributo culture especifica la referencia cultural para utilizar cuando un bloque de expresión se convierte en texto.

## <a name="debug-attribute"></a>debug (atributo)

Ejemplo:

```
debug="true"
```

Valores válidos:

`true`

`false` (valor predeterminado)

Si el atributo `debug` es `true`, el archivo de código intermedio contiene información que permite al depurador identificar con más precisión la posición de la plantilla donde se produjo una interrupción o una excepción.

Para plantillas en tiempo de diseño se escribirá el archivo de código intermedio para su **% TEMP %** directory.

Para ejecutar una plantilla en tiempo de diseño en el depurador, guarde la plantilla de texto, a continuación, abra el menú contextual de la plantilla de texto en el Explorador de soluciones y elija **depurar plantilla T4**.

## <a name="hostspecific-attribute"></a>hostspecific (atributo)

Ejemplo:

```
hostspecific="true"
```

Valores válidos:

`true`

`false` (valor predeterminado)

`trueFromBase`

Si establece el valor de este atributo en `true`, una propiedad denominada `Host` se agrega a la clase generada por la plantilla de texto. La propiedad es una referencia al host del motor de transformación y se declara como <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. Si ha definido un host personalizado, puede convertirlo al tipo de host personalizado.

Dado que el tipo de esta propiedad depende del tipo de host, solamente es útil si está escribiendo una plantilla de texto que únicamente trabaja con un host concreto. Es aplicable a [plantillas en tiempo de diseño](../modeling/design-time-code-generation-by-using-t4-text-templates.md), pero no [plantillas en tiempo de ejecución](../modeling/run-time-text-generation-with-t4-text-templates.md).

Cuando `hostspecific` es `true` y que está usando Visual Studio, puede convertir `this.Host` a IServiceProvider para tener acceso a características de Visual Studio. También puede utilizar `Host.ResolvePath(filename)` para obtener la ruta de acceso absoluta de un archivo en el proyecto. Por ejemplo:

```csharp
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="EnvDTE" #>
<#@ import namespace="System.IO" #>
<#@ import namespace="Microsoft.VisualStudio.TextTemplating" #>
<# // Get the Visual Studio API as a service:
 DTE dte = ((IServiceProvider)this.Host).GetCOMService(typeof(DTE)) as DTE;
#>
Number of projects in this solution: <#=  dte.Solution.Projects.Count #>

<#
 // Find a path within the current project:
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));
#>
Content of myFile is:
<#= myFile #>
```

Si utiliza los atributos `inherits` y `hostspecific` juntos, especifique host="trueFromBase" en la clase derivada y host=" true" en la clase base. Esto evita una definición doble de la propiedad `Host` en el código generado.

## <a name="language-attribute"></a>language (atributo)

Ejemplo:

`language="VB"`

Valores válidos:

`C#` (valor predeterminado)

`VB`

El `language` atributo especifica el idioma ([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] o [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]) que se utilizará para el código fuente en los bloques de instrucciones y expresiones. El archivo de código intermedio del que se genera el resultado utilizará este lenguaje. Este lenguaje no se relaciona con el lenguaje que genera la plantilla, que puede ser cualquier tipo de texto.

Por ejemplo:

```vb
<#@ template language="VB" #>
<#@ output extension=".txt" #>
Squares of numbers:
<#
  Dim number As Integer
  For number = 1 To 4
#>
  Square of <#= number #> is <#= number * number #>
<#
  Next number
#>
```

## <a name="inherits-attribute"></a>inherits (atributo)

Puede especificar que el código de programa de su plantilla puede heredar de otra clase, que también se puede generar a partir de una plantilla de texto.

### <a name="inheritance-in-a-run-time-preprocessed-text-template"></a>Herencia en una plantilla de texto (preprocesada) en tiempo de ejecución

Puede utilizar la herencia entre plantillas de texto en tiempo de ejecución para crear una plantilla básica con algunas variantes derivadas. Plantillas en tiempo de ejecución son aquellos que tienen el **Custom Tool** propiedad establecida en **TextTemplatingFilePreprocessor**. Una plantilla en tiempo de ejecución genera el código al que puede llamar en la aplicación para crear el texto definido en la plantilla. Para obtener más información, consulte [generación de texto en tiempo de ejecución con plantillas de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

Si no especifica un atributo `inherits`, se generan una clase base y una clase derivada en la plantilla de texto. Al especificar un atributo `inherits`, únicamente se genera la clase derivada. Puede escribir una clase base a mano, pero debe proporcionar los métodos que utiliza la clase derivada.

Por lo general, se especifica otra plantilla preprocesada como la clase base. La plantilla base proporciona bloques de texto comunes, que pueden intercalarse con texto en las plantillas derivadas. Puede utilizar bloques de característica de clase `<#+ ... #>` para definir métodos que contienen fragmentos de texto. Por ejemplo, puede colocar el marco del texto de salida en la plantilla base, proporcionando métodos virtuales que se pueden invalidar en plantillas derivadas:

Plantilla de texto (preprocesada) en tiempo de ejecución BaseTemplate.tt:

```scr
This is the common header.
<#
  SpecificFragment1();
#>
A common central text.
<#
  SpecificFragment2();
#>
This is the common footer.
<#+
  // Declare abstract methods
  protected virtual void SpecificFragment1() { }
  protected virtual void SpecificFragment2() { }
#>
```

Plantilla de texto (preprocesada) en tiempo de ejecución DerivedTemplate1.tt:

```csharp
<#@ template language="C#" inherits="BaseTemplate" #>
<#
  // Run the base template:
  base.TransformText();
#>
<#+
// Provide fragments specific to this derived template:
protected override void SpecificFragment1()
{
#>
   Fragment 1 for DerivedTemplate1
<#+
}
protected override void SpecificFragment2()
{
#>
   Fragment 2 for DerivedTemplate1
<#+
}
#>
```

Código de aplicación para invocar a DerivedTemplate1:

```csharp
Console.WriteLine(new DerivedTemplate().TransformText());
```

Resultado que se obtiene:

```
This is the common header.
   Fragment 1 for DerivedTemplate1
A common central text.
   Fragment 2 for DerivedTemplate1
This is the common footer.
```

Puede compilar las clases derivadas y base en proyectos diferentes. No olvide agregar el proyecto base o ensamblado a las referencias del proyecto derivado.

También puede utilizar una clase normal escrita a mano como la clase base. La clase base debe proporcionar los métodos que usa la clase derivada.

> [!WARNING]
> Si utiliza los atributos `inherits` y `hostspecific` juntos, especifique hostspecific="trueFromBase" en la clase derivada y host=" true" en la clase base. Esto evita una definición doble de la propiedad `Host` en el código generado.

### <a name="inheritance-in-a-design-time-text-template"></a>Herencia en una plantilla de texto en tiempo de diseño

Una plantilla de texto en tiempo de diseño es un archivo para el que **Custom Tool** está establecido en **TextTemplatingFileGenerator**. La plantilla genera un archivo de salida de código o texto, que forma parte del proyecto de Visual Studio. Para generar el archivo de salida, la plantilla primero se traduce en un archivo de código de programa intermedio, que normalmente no ve. El atributo `inherits` especifica la clase base para este código intermedio.

Para una plantilla de texto en tiempo de diseño, puede especificar cualquier clase base que se derive de <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName>. Utilice la directiva `<#@assembly#>` para cargar el ensamblado o proyecto que contiene la clase base.

Para obtener más información, consulte ["Herencia en plantillas de texto" en el Blog de Gareth Jones](http://go.microsoft.com/fwlink/?LinkId=208373).

## <a name="linepragmas-attribute"></a>linePragmas attribute

Ejemplo:

`linePragmas="false"`

Valores válidos:

`true` (valor predeterminado)

`false`

Al establecer este atributo en false se quitan las etiquetas que identifican los números de línea en el código generado. Esto significa que el compilador notificará cualquier error utilizando los números de línea del código generado. Esto proporciona más opciones de depuración, ya que puede elegir entre depurar la plantilla de texto o el código generado.

Este atributo también puede ayudar si se detecta que los nombres de archivo absolutas en las directivas pragma están produciendo combinaciones confusas bajo control de código fuente.

## <a name="visibility-attribute"></a>Atributo de visibilidad

Ejemplo:

`visibility="internal"`

Valores válidos:

`public` (valor predeterminado)

`internal`

En una plantilla de texto en tiempo de ejecución, establece el atributo de visibilidad de la clase generada. De forma predeterminada, la clase forma parte de la API pública del código, pero si se establece `visibility="internal"`, puede asegurarse de que solo el código pueda utilizar la clase de generación de texto.
