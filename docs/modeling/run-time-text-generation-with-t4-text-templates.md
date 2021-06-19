---
title: Generación de texto en tiempo de ejecución con plantillas de texto T4
description: Obtenga información sobre cómo puede generar cadenas de texto en la aplicación en tiempo de ejecución mediante Visual Studio de texto en tiempo de ejecución.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- Preprocessed Text Template project item
- TextTemplatingFilePreprocessor custom tool
- text templates, TransformText() method
- text templates, generating files at run time
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 96d37bc586f9e8d6134377244c3181a52ec11a84
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387559"
---
# <a name="run-time-text-generation-with-t4-text-templates"></a>Generación de texto en tiempo de ejecución con plantillas de texto T4

Puede generar cadenas de texto en la aplicación en tiempo de ejecución mediante Visual Studio plantillas de texto en tiempo de ejecución. El equipo donde se ejecuta la aplicación no tiene que tener Visual Studio. A veces, las plantillas en tiempo de ejecución se denominan "plantillas de texto preprocesado" porque, en tiempo de compilación, la plantilla genera código que se ejecuta en tiempo de ejecución.

Cada plantilla es una combinación del texto tal como aparecerá en la cadena generada y fragmentos del código del programa. Los fragmentos del programa suministran valores para las partes variables de la cadena y también controlan las partes condicionales y repetidas.

Por ejemplo, la siguiente plantilla podría usarse en una aplicación que crea un informe HTML.

```html
<#@ template language="C#" #>
<html><body>
<h1>Sales for Previous Month</h2>
<table>
    <# for (int i = 1; i <= 10; i++)
       { #>
         <tr><td>Test name <#= i #> </td>
             <td>Test value <#= i * i #> </td> </tr>
    <# } #>
 </table>
This report is Company Confidential.
</body></html>
```

Observe que la plantilla es una página HTML en la que las partes variables se han reemplazado por código de programa. Puede comenzar el diseño de una página de este tipo escribiendo un prototipo estático de la página HTML. A continuación, podría reemplazar la tabla y otras partes variables por código de programa que genere el contenido que varía de una ocasión a la siguiente.

El uso de una plantilla en la aplicación hace que sea más fácil ver la forma final de la salida que en, por ejemplo, una larga serie de instrucciones de escritura. Realizar cambios en la forma de la salida es más fácil y confiable.

## <a name="creating-a-run-time-text-template-in-any-application"></a>Creación de una Run-Time de texto en cualquier aplicación

### <a name="to-create-a-run-time-text-template"></a>Para crear una plantilla de texto en tiempo de ejecución

1. En Explorador de soluciones, en el menú contextual del proyecto, elija **Agregar**  >  **nuevo elemento.**

2. En el cuadro **de diálogo Agregar nuevo** elemento, seleccione Plantilla de texto en tiempo de **ejecución**. (En Visual Basic buscar en **Elementos comunes**  >  **General).**

3. Escriba un nombre para el archivo de plantilla.

    > [!NOTE]
    > El nombre del archivo de plantilla se usará como nombre de clase en el código generado. Por lo tanto, no debe tener espacios ni signos de puntuación.

4. Seleccione **Agregar**.

    Se crea un nuevo archivo que tiene la extensión **.tt**. Su **propiedad Herramienta** personalizada se establece en **TextTemplatingFilePreprocessor.** Contiene las líneas siguientes:

    ```
    <#@ template language="C#" #>
    <#@ assembly name="System.Core" #>
    <#@ import namespace="System.Linq" #>
    <#@ import namespace="System.Text" #>
    <#@ import namespace="System.Collections.Generic" #>
    ```

## <a name="converting-an-existing-file-to-a-run-time-template"></a>Convertir un archivo existente en una plantilla Run-Time existente

Una buena manera de crear una plantilla es convertir un ejemplo existente de la salida. Por ejemplo, si la aplicación va a generar archivos HTML, puede empezar por crear un archivo HTML sin formato. Asegúrese de que funciona correctamente y de que su apariencia es correcta. A continuación, inscluyéndolo Visual Studio proyecto y conviéndolo en una plantilla.

### <a name="to-convert-an-existing-text-file-to-a-run-time-template"></a>Para convertir un archivo de texto existente en una plantilla en tiempo de ejecución

1. Incluya el archivo en el Visual Studio proyecto. En Explorador de soluciones, en el menú contextual del proyecto, elija **Agregar**  >  **elemento existente.**

2. Establezca la propiedad Herramientas personalizadas **del** archivo **en TextTemplatingFilePreprocessor.** En Explorador de soluciones, en el menú contextual del archivo, elija **Propiedades.**

    > [!NOTE]
    > Si la propiedad ya está establecida, asegúrese de que es **TextTemplatingFilePreprocessor** y no **TextTemplatingFileGenerator.** Esto puede ocurrir si incluye un archivo que ya tiene la extensión **.tt**.

3. Cambie la extensión de nombre de archivo **a .tt**. Aunque este paso es opcional, le ayuda a evitar abrir el archivo en un editor incorrecto.

4. Quite los espacios o signos de puntuación de la parte principal del nombre de archivo. Por ejemplo, "My Web Page.tt" sería incorrecto, pero "MyWebPage.tt" es correcto. El nombre de archivo se usará como nombre de clase en el código generado.

5. Inserte la siguiente línea al principio del archivo. Si está trabajando en un proyecto Visual Basic, reemplace "C#" por "VB".

    `<#@ template language="C#" #>`

## <a name="the-content-of-the-run-time-template"></a>El contenido de la plantilla Run-Time plantilla

### <a name="template-directive"></a>Directiva de plantilla

Mantenga la primera línea de la plantilla tal como estaba cuando creó el archivo:

`<#@ template language="C#" #>`

El parámetro language dependerá del idioma del proyecto.

### <a name="plain-content"></a>Contenido sin formato

Edite **el archivo .tt** para que contenga el texto que desea que genere la aplicación. Por ejemplo:

```html
<html><body>
<h1>Sales for January</h2>
<!-- table to be inserted here -->
This report is Company Confidential.
</body></html>
```

### <a name="embedded-program-code"></a>Código de programa insertado

Puede insertar código de programa entre `<#` y `#>` . Por ejemplo:

```csharp
<table>
    <# for (int i = 1; i <= 10; i++)
       { #>
         <tr><td>Test name <#= i #> </td>
             <td>Test value <#= i * i #> </td> </tr>
    <# } #>
 </table>
```

```vb
<table>
<#
    For i As Integer = 1 To 10
#>
    <tr><td>Test name <#= i #> </td>
      <td>Test value <#= i*i #> </td></tr>
<#
    Next
#>
</table>
```

Observe que las instrucciones se insertan entre `<# ... #>` y las expresiones se insertan entre `<#= ... #>` . Para obtener más información, vea [Escribir una plantilla de texto T4.](../modeling/writing-a-t4-text-template.md)

## <a name="using-the-template"></a>Uso de la plantilla

### <a name="the-code-built-from-the-template"></a>Código creado a partir de la plantilla

Al guardar el **archivo .tt,** se genera **un archivo .cs** o **.vb** subsidiaria. Para ver este archivo en **Explorador de soluciones**, expanda el **nodo de archivo .tt.** En un proyecto Visual Basic, elija primero **Mostrar todos los archivos en** la barra **Explorador de soluciones** herramientas.

Observe que el archivo subsidiaria contiene una clase parcial que contiene un método denominado `TransformText()` . Puede llamar a este método desde la aplicación.

### <a name="generating-text-at-run-time"></a>Generación de texto en tiempo de ejecución

En el código de la aplicación, puede generar el contenido de la plantilla mediante una llamada como esta:

```csharp
MyWebPage page = new MyWebPage();
String pageContent = page.TransformText();
System.IO.File.WriteAllText("outputPage.html", pageContent);
```

```vb
Dim page = New My.Templates.MyWebPage
Dim pageContent = page.TransformText()
System.IO.File.WriteAllText("outputPage.html", pageContent)
```

Para colocar la clase generada en un espacio de nombres determinado, establezca la propiedad Espacio de **nombres** de la herramienta personalizada del archivo de plantilla de texto.

### <a name="debugging-runtime-text-templates"></a>Depurar plantillas de texto en tiempo de ejecución

Depurar y probar plantillas de texto en tiempo de ejecución de la misma manera que el código normal.

Puede establecer un punto de interrupción en una plantilla de texto. Si inicia la aplicación en modo de depuración desde Visual Studio, puede seguir el código y evaluar las expresiones watch de la manera habitual.

### <a name="passing-parameters-in-the-constructor"></a>Pasar parámetros en el constructor

Normalmente, una plantilla debe importar algunos datos de otras partes de la aplicación. Para facilitar esto, el código generado por la plantilla es una clase parcial. Puede crear otra parte de la misma clase en otro archivo del proyecto. Ese archivo puede incluir un constructor con parámetros, propiedades y funciones a los que se puede acceder tanto mediante el código insertado en la plantilla como por el resto de la aplicación.

Por ejemplo, podría crear un archivo **independiente MyWebPageCode.cs**:

```csharp
partial class MyWebPage
{
    private MyData m_data;
    public MyWebPage(MyData data) { this.m_data = data; }}
```

En el archivo de **MyWebPage.tt**, puede escribir:

```html
<h2>Sales figures</h2>
<table>
<# foreach (MyDataItem item in m_data.Items)
   // m_data is declared in MyWebPageCode.cs
   { #>
      <tr><td> <#= item.Name #> </td>
          <td> <#= item.Value #> </td></tr>
<# } // end of foreach
#>
</table>
```

Para usar esta plantilla en la aplicación:

```csharp
MyData data = ...;
MyWebPage page = new MyWebPage(data);
String pageContent = page.TransformText();
System.IO.File.WriteAllText("outputPage.html", pageContent);
```

#### <a name="constructor-parameters-in-visual-basic"></a>Parámetros de constructor en Visual Basic

En Visual Basic, el archivo **independiente MyWebPageCode.vb** contiene:

```vb
Namespace My.Templates
  Partial Public Class MyWebPage
    Private m_data As MyData
    Public Sub New(ByVal data As MyData)
      m_data = data
    End Sub
  End Class
End Namespace
```

El archivo de plantilla podría contener:

```html
<#@ template language="VB" #>
<html><body>
<h1>Sales for January</h2>
<table>
<#
    For Each item In m_data.Items
#>
    <tr><td>Test name <#= item.Name #> </td>
      <td>Test value <#= item.Value #> </td></tr>
<#
    Next
#>
</table>
This report is Company Confidential.
</body></html>
```

La plantilla se puede invocar pasando el parámetro en el constructor:

```vb
Dim data = New My.Templates.MyData
    ' Add data values here ....
Dim page = New My.Templates.MyWebPage(data)
Dim pageContent = page.TransformText()
System.IO.File.WriteAllText("outputPage.html", pageContent)
```

#### <a name="passing-data-in-template-properties"></a>Pasar datos en propiedades de plantilla

Una manera alternativa de pasar datos a la plantilla es agregar propiedades públicas a la clase de plantilla en una definición de clase parcial. La aplicación puede establecer las propiedades antes de invocar `TransformText()` .

También puede agregar campos a la clase de plantilla en una definición parcial. Esto le permite pasar datos entre ejecuciones sucesivas de la plantilla.

### <a name="use-partial-classes-for-code"></a>Usar clases parciales para el código

Muchos desarrolladores prefieren evitar escribir grandes cuerpos de código en plantillas. En su lugar, puede definir métodos en una clase parcial que tenga el mismo nombre que el archivo de plantilla. Llame a esos métodos desde la plantilla. De esta manera, la plantilla muestra más claramente el aspecto de la cadena de salida de destino. Las discusiones sobre la apariencia del resultado se pueden separar de la lógica de creación de los datos que muestra.

### <a name="assemblies-and-references"></a>Ensamblados y referencias

Si desea que el código de plantilla haga referencia a un .NET u otro  ensamblado, como **System.Xml.dll**, agrégrelo a las referencias del proyecto de la manera habitual.

Si desea importar un espacio de nombres de la misma manera que una `using` instrucción , puede hacerlo con la directiva `import` :

```
<#@ import namespace="System.Xml" #>
```

Estas directivas deben colocarse al principio del archivo, inmediatamente después de la `<#@template` directiva .

### <a name="shared-content"></a>Contenido compartido

Si tiene texto que se comparte entre varias plantillas, puede colocarlo en un archivo independiente e incluirlo en cada archivo en el que debería aparecer:

```
<#@include file="CommonHeader.txt" #>
```

El contenido incluido puede contener cualquier combinación de código de programa y texto sin formato, y puede contener otras directivas include y otras directivas.

La directiva include se puede usar en cualquier parte del texto de un archivo de plantilla o de un archivo incluido.

### <a name="inheritance-between-run-time-text-templates"></a>Herencia entre Run-Time de texto

Puede compartir contenido entre plantillas en tiempo de ejecución escribiendo una plantilla de clase base, que puede ser abstracta. Use el `inherits` parámetro de la directiva para hacer referencia a otra clase de plantilla en tiempo de `<@#template#>` ejecución.

#### <a name="inheritance-pattern-fragments-in-base-methods"></a>Patrón de herencia: fragmentos en métodos base

En el patrón utilizado en el ejemplo siguiente, observe los puntos siguientes:

- La clase base define `SharedFragments` métodos dentro de bloques de características de clase `<#+ ... #>` .

- La clase base no contiene texto libre. En su lugar, todos sus bloques de texto se producen dentro de los métodos de características de clase.

- La clase derivada invoca los métodos definidos en `SharedFragments` .

- La aplicación llama `TextTransform()` al método de la clase derivada, pero no transforma la clase base `SharedFragments` .

- Las clases base y derivada son plantillas de texto en tiempo de ejecución; Es decir, la **propiedad Herramienta** personalizada se establece **en TextTemplatingFilePreprocessor.**

**SharedFragments.tt:**

```
<#@ template language="C#" #>
<#+
protected void SharedText(int n)
{
#>
   Shared Text <#= n #>
<#+
}
// Insert more methods here if required.
#>
```

**MyTextTemplate1.tt:**

```
<#@ template language="C#" inherits="SharedFragments" #>
begin 1
   <# SharedText(2); #>
end 1
```

**MyProgram.cs:**

```csharp
...
MyTextTemplate1 t1  = new MyTextTemplate1();
string result = t1.TransformText();
Console.WriteLine(result);
```

**La salida resultante:**

```
begin 1
    Shared Text 2
end 1
```

#### <a name="inheritance-pattern-text-in-base-body"></a>Patrón de herencia: texto en el cuerpo base

En este enfoque alternativo al uso de la herencia de plantillas, la mayor parte del texto se define en la plantilla base. Las plantillas derivadas proporcionan fragmentos de datos y texto que caben en el contenido base.

**AbstractBaseTemplate1.tt:**

```
<#@ template language="C#" #>

Here is the description for this derived template:
  <#= this.Description #>

Here is the fragment specific to this derived template:
<#
  this.PushIndent("  ");
  SpecificFragment(42);
  this.PopIndent();
#>
End of common template.
<#+
  // State set by derived class before calling TextTransform:
  protected string Description = "";
  // 'abstract' method to be defined in derived classes:
  protected virtual void SpecificFragment(int n) { }
#>
```

**DerivedTemplate1.tt:**

```
<#@ template language="C#" inherits="AbstractBaseTemplate1" #>
<#
  // Set the base template properties:
  base.Description = "Description for this derived class";

  // Run the base template:
  base.TransformText();

#>
End material for DerivedTemplate1.

<#+
// Provide a fragment specific to this derived template:

protected override void SpecificFragment(int n)
{
#>
   Specific to DerivedTemplate1 : <#= n #>
<#+
}
#>
```

**Código de aplicación:**

```csharp
...
DerivedTemplate1 t1 = new DerivedTemplate1();
string result = t1.TransformText();
Console.WriteLine(result);
```

**Resultado que se obtiene:**

```
Here is the description for this derived template:
  Description for this derived class

Here is the fragment specific to this derived template:
     Specific to DerivedTemplate1 : 42
End of common template.
End material for DerivedTemplate1.
```

## <a name="related-topics"></a>Temas relacionados

Plantillas en tiempo de diseño: si desea usar una plantilla para generar código que forma parte de la aplicación, vea Generación de código en tiempo de diseño mediante plantillas [de texto T4.](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

Las plantillas en tiempo de ejecución se pueden usar en cualquier aplicación donde las plantillas y su contenido se determinen en tiempo de compilación. Pero si desea escribir una extensión de Visual Studio que genera texto a partir de plantillas que cambian en tiempo de ejecución, vea [Invoking Text Transformation in a VS Extension](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="see-also"></a>Vea también

- [Generación de código y plantillas de texto T4](../modeling/code-generation-and-t4-text-templates.md)
- [Escribir una plantilla de texto T4](../modeling/writing-a-t4-text-template.md)
- [Cuadro de herramientas T4](http://olegsych.com/T4Toolbox/)
