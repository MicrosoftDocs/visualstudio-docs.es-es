---
title: Generación de texto en tiempo de ejecución con plantillas de texto T4
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- Preprocessed Text Template project item
- TextTemplatingFilePreprocessor custom tool
- text templates, TransformText() method
- text templates, generating files at run time
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 5b39437dc5f81b17c0bcfe27dbb7b8d99bebbc87
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31953120"
---
# <a name="run-time-text-generation-with-t4-text-templates"></a>Generación de texto en tiempo de ejecución con plantillas de texto T4

Puede generar cadenas de texto en la aplicación en tiempo de ejecución mediante el uso de plantillas de texto en tiempo de ejecución de Visual Studio. El equipo donde se ejecuta la aplicación no tiene que tiene Visual Studio. Plantillas en tiempo de ejecución a veces se denominan "preprocesadas plantillas de texto" porque en tiempo de compilación, la plantilla genera código que se ejecuta en tiempo de ejecución.

Cada plantilla es una mezcla del texto tal y como aparecerá en la cadena generada y fragmentos de código de programa. Los fragmentos de programa suministran valores para las partes variables de la cadena y también controlan las partes condicionales y repetidas.

Por ejemplo, la plantilla siguiente podría usarse en una aplicación que crea un informe HTML.

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

Observe que la plantilla es una página HTML en el que las partes de la variable se han reemplazado por código de programa. Puede empezar el diseño de dicha página escribiendo un prototipo estático de la página HTML. A continuación, podría reemplazar la tabla y otras partes variables con código de programa que genera el contenido que varía de una de las ocasiones a la siguiente.

Mediante una plantilla en los facilita la aplicación sea más fácil ver la forma final de la salida que se puede realizar en, por ejemplo, una larga serie de instrucciones de escritura. Realizar cambios en el formulario de la salida es más fácil y confiable.

## <a name="creating-a-run-time-text-template-in-any-application"></a>Crear una plantilla de texto en tiempo de ejecución en cualquier aplicación

### <a name="to-create-a-run-time-text-template"></a>Para crear una plantilla de texto en tiempo de ejecución

1. En el Explorador de soluciones, en el menú contextual del proyecto, elija **agregar**, **nuevo elemento**.

2. En el **Agregar nuevo elemento** cuadro de diálogo, seleccione **plantilla de texto en tiempo de ejecución**. (En Visual Basic, mire debajo **elementos comunes** > **General**.)

3. Escriba un nombre para el archivo de plantilla.

    > [!NOTE]
    > El nombre de archivo de plantilla se utilizará como un nombre de clase en el código generado. Por lo tanto, no debería tener espacios o signos de puntuación.

4. Haga clic en **Agregar**.

    Se crea un nuevo archivo con extensión **.tt**. Su **herramienta personalizada** propiedad está establecida en **TextTemplatingFilePreprocessor**. Contiene las siguientes líneas:

    ```
    <#@ template language="C#" #>
    <#@ assembly name="System.Core" #>
    <#@ import namespace="System.Linq" #>
    <#@ import namespace="System.Text" #>
    <#@ import namespace="System.Collections.Generic" #>
    ```

## <a name="converting-an-existing-file-to-a-run-time-template"></a>Convertir un archivo existente en una plantilla en tiempo de ejecución

Una buena manera de crear una plantilla consiste en convertir un ejemplo existente de la salida. Por ejemplo, si la aplicación generará archivos HTML, puede iniciar mediante la creación de un archivo HTML normal. Asegúrese de que funciona correctamente y que su aspecto es correcto. A continuación, incluya en su proyecto de Visual Studio y convertirla en una plantilla.

### <a name="to-convert-an-existing-text-file-to-a-run-time-template"></a>Para convertir un archivo de texto existente en una plantilla en tiempo de ejecución

1. Incluya el archivo en su proyecto de Visual Studio. En el Explorador de soluciones, en el menú contextual del proyecto, elija **agregar** > **elemento existente**.

2. Establecer el archivo **Custom Tools** propiedad **TextTemplatingFilePreprocessor**. En el Explorador de soluciones, en el menú contextual del archivo, elija **propiedades**.

    > [!NOTE]
    > Si ya se ha establecido la propiedad, asegúrese de que es **TextTemplatingFilePreprocessor** y no **TextTemplatingFileGenerator**. Esto puede ocurrir si incluye un archivo que ya tiene la extensión **.tt**.

3. Cambie la extensión de nombre de archivo a **.tt**. Aunque este paso es opcional, le ayuda a evitar que se abra el archivo en un editor incorrecto.

4. Quite los espacios o signos de puntuación de la parte principal del nombre de archivo. Por ejemplo "Mi página Web.tt" sería incorrecto, pero "MiPáginaWeb.tt" es correcto. El nombre de archivo se utilizará como un nombre de clase en el código generado.

5. Inserte la siguiente línea al principio del archivo. Si está trabajando en un proyecto de Visual Basic, reemplace "C#" con "VB".

    `<#@ template language="C#" #>`

## <a name="the-content-of-the-run-time-template"></a>El contenido de la plantilla en tiempo de ejecución

### <a name="template-directive"></a>Directiva de plantilla

Mantener la primera línea de la plantilla como se encontraba cuando se creó el archivo:

`<#@ template language="C#" #>`

El parámetro language dependerán del lenguaje del proyecto.

### <a name="plain-content"></a>Contenido simple

Editar la **.tt** archivo para que contenga el texto que desea que genere la aplicación. Por ejemplo:

```html
<html><body>
<h1>Sales for January</h2>
<!-- table to be inserted here -->
This report is Company Confidential.
</body></html>
```

### <a name="embedded-program-code"></a>Código de programa incrustado

Puede insertar código de programa entre `<#` y `#>`. Por ejemplo:

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

Tenga en cuenta que las instrucciones se insertan entre `<# ... #>` y expresiones se insertan entre `<#= ... #>`. Para obtener más información, consulte [escribir una plantilla de texto T4](../modeling/writing-a-t4-text-template.md).

## <a name="using-the-template"></a>Uso de la plantilla

### <a name="the-code-built-from-the-template"></a>El código compilado a partir de la plantilla

Cuando se guarda el **.tt** de archivos, una subsidiaria **.cs** o **.vb** se genera el archivo. Para ver este archivo en el Explorador de soluciones, expanda la **.tt** nodo del archivo. En un proyecto de Visual Basic, elija **mostrar todos los archivos** en la barra de herramientas del explorador de soluciones.

Tenga en cuenta que el archivo subsidiario contiene una clase parcial que contiene un método denominado `TransformText()`. Puede llamar a este método desde su aplicación.

### <a name="generating-text-at-run-time"></a>Generar texto en tiempo de ejecución

En el código de aplicación, puede generar el contenido de la plantilla mediante una llamada similar al siguiente:

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

Para colocar la clase generada en un espacio de nombres determinado, establezca el **personalizado herramienta Namespace** propiedad del archivo de plantilla de texto.

### <a name="debugging-runtime-text-templates"></a>Depuración de plantillas de texto en tiempo de ejecución

Depurar y probar las plantillas de texto en tiempo de ejecución de la misma manera como código normal.

Puede establecer un punto de interrupción en una plantilla de texto. Si la aplicación se inicia en modo de depuración de Visual Studio, puede recorrer el código y evaluar expresiones de inspección de la manera habitual.

### <a name="passing-parameters-in-the-constructor"></a>Pasar parámetros en el constructor

Normalmente una plantilla debe importar algunos datos de otras partes de la aplicación. Para facilitar este proceso, el código generado por la plantilla es una clase parcial. Puede crear otra parte de la misma clase en otro archivo en el proyecto. Este archivo puede incluir un constructor con parámetros, propiedades y funciones que pueden acceder a él tanto el código que está incrustado en la plantilla y el resto de la aplicación.

Por ejemplo, podría crear un archivo independiente **MyWebPageCode.cs**:

```csharp
partial class MyWebPage
{
    private MyData m_data;
    public MyWebPage(MyData data) { this.m_data = data; }}
```

En el archivo de plantilla **MiPáginaWeb.tt**, podría escribir:

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

#### <a name="constructor-parameters-in-visual-basic"></a>Parámetros del constructor en Visual Basic

En Visual Basic, el archivo independiente **MyWebPageCode.vb** contiene:

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

Podría contener el archivo de plantilla:

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

Puede invocar la plantilla, pase el parámetro en el constructor:

```vb
Dim data = New My.Templates.MyData
    ' Add data values here ....
Dim page = New My.Templates.MyWebPage(data)
Dim pageContent = page.TransformText()
System.IO.File.WriteAllText("outputPage.html", pageContent)
```

#### <a name="passing-data-in-template-properties"></a>Pasar datos en Propiedades de la plantilla

Una manera alternativa de pasar los datos a la plantilla es agregar propiedades públicas a la clase de plantilla en una definición de clase parcial. La aplicación puede establecer las propiedades antes de invocar `TransformText()`.

También puede agregar campos a la clase de plantilla en una definición parcial. Esto le permite pasar datos entre ejecuciones sucesivas de la plantilla.

### <a name="use-partial-classes-for-code"></a>Utilizar clases parciales para el código

Muchos desarrolladores prefieren evitar escribir grandes cuerpos de código en las plantillas. En su lugar, puede definir métodos en una clase parcial que tiene el mismo nombre que el archivo de plantilla. Llamar a dichos métodos desde la plantilla. De esta manera, la plantilla se muestra más claramente la cadena de salida del destino será similar. Debates sobre el aspecto del resultado se pueden separar de la lógica de creación de los datos que muestra.

### <a name="assemblies-and-references"></a>Ensamblados y referencias

Si desea que el código de plantilla para hacer referencia a otro ensamblado o .NET como **System.Xml.dll**, agregar a su proyecto **referencias** de la manera habitual.

Si desea importar un espacio de nombres de la misma manera que una `using` (instrucción), puede hacerlo con el `import` directiva:

```
<#@ import namespace="System.Xml" #>
```

Estas directivas deben colocarse al principio del archivo, inmediatamente después de la `<#@template` directiva.

### <a name="shared-content"></a>Contenido compartido

Si tiene texto que se comparte entre varias plantillas, puede colocarlo en un archivo independiente y se incluyen en cada archivo en el que debe aparecer:

```
<#@include file="CommonHeader.txt" #>
```

El contenido incluido puede contener cualquier combinación de código de programa y texto sin formato, y puede contener otras directivas de inclusión y otras directivas.

La directiva de inclusión se puede usar en cualquier lugar dentro del texto de un archivo de plantilla o un archivo incluido.

### <a name="inheritance-between-run-time-text-templates"></a>Herencia entre plantillas de texto en tiempo de ejecución

También puede compartir el contenido entre plantillas en tiempo de ejecución mediante la escritura de una plantilla de clase base, que puede ser abstracta. Use la `inherits` parámetro de la `<@#template#>` directiva para hacer referencia a otra clase de plantilla en tiempo de ejecución.

#### <a name="inheritance-pattern-fragments-in-base-methods"></a>Patrón de herencia: fragmentos en los métodos Base

En el patrón que se utiliza en el ejemplo siguiente, tenga en cuenta lo siguiente:

- La clase base `SharedFragments` define los métodos dentro de bloques de características de clase `<#+ ... #>`.

- La clase base no contiene ningún texto sin formato. En su lugar, todos los bloques de texto se producen dentro de los métodos de la característica de clase.

- La clase derivada, invoca los métodos definidos en `SharedFragments`.

- La aplicación llama el `TextTransform()` método de la clase derivada, pero no transforma la clase base `SharedFragments`.

- Las clases base y derivadas son plantillas de texto en tiempo de ejecución; es decir, el **herramienta personalizada** propiedad está establecida en **TextTemplatingFilePreprocessor**.

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

**El resultado:**

```
begin 1
    Shared Text 2
end 1
```

#### <a name="inheritance-pattern-text-in-base-body"></a>Patrón de herencia: Texto en el cuerpo de la Base

En este enfoque alternativo a usar la herencia de plantilla, la mayor parte del texto se define en la plantilla base. Las plantillas derivadas proporcionan datos y fragmentos de texto caben en el contenido de la base.

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

**Resultado:**

```
Here is the description for this derived template:
  Description for this derived class

Here is the fragment specific to this derived template:
     Specific to DerivedTemplate1 : 42
End of common template.
End material for DerivedTemplate1.
```

## <a name="related-topics"></a>Temas relacionados

Plantillas en tiempo de diseño: si desea usar una plantilla para generar el código que pasa a formar parte de la aplicación, consulte [generación de código en tiempo de diseño mediante el uso de plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

Plantillas en tiempo de ejecución se pueden usar en cualquier aplicación donde las plantillas y su contenido se determinan en tiempo de compilación. Sin embargo, si desea escribir una extensión de Visual Studio que genera texto a partir de plantillas que cambian en tiempo de ejecución, consulte [invocar la transformación de texto en una extensión de VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="see-also"></a>Vea también

- [Generación de código y plantillas de texto T4](../modeling/code-generation-and-t4-text-templates.md)
- [Escribir una plantilla de texto T4](../modeling/writing-a-t4-text-template.md)
- [Cuadro de herramientas de T4](http://olegsych.com/T4Toolbox/)