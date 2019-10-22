---
title: Generación de texto en tiempo de ejecución con plantillas de texto T4 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Preprocessed Text Template project item
- TextTemplatingFilePreprocessor custom tool
- text templates, TransformText() method
- text templates, generating files at run time
ms.assetid: 79b4b3c6-a9a7-4446-b6fd-e2388fc6b05f
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 37b8b89f1dfc8d3539101080ebbed20615da2c01
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671243"
---
# <a name="run-time-text-generation-with-t4-text-templates"></a>Generación de texto en tiempo de ejecución con plantillas de texto T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede generar cadenas de texto en la aplicación en tiempo de ejecución mediante [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] plantillas de texto en tiempo de ejecución. No es necesario que el equipo en el que se ejecuta la aplicación tenga [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Las plantillas en tiempo de ejecución a veces se denominan "plantillas de texto preprocesadas" porque, en tiempo de compilación, la plantilla genera código que se ejecuta en tiempo de ejecución.

 Cada plantilla es una combinación del texto tal como aparecerá en la cadena generada y fragmentos de código de programa. Los fragmentos del programa suministran valores para las partes variables de la cadena y controlan también las partes condicionales y repetidas.

 Por ejemplo, la siguiente plantilla podría usarse en una aplicación que crea un informe HTML.

```
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

 Observe que la plantilla es una página HTML en la que las partes variables se han reemplazado por código de programa. Puede comenzar el diseño de dicha página escribiendo un prototipo estático de la página HTML. A continuación, podría reemplazar la tabla y otras partes variables por el código de programa que genera el contenido que varía de una ocasión a la siguiente.

 El uso de una plantilla en la aplicación facilita la visualización de la forma final de la salida, por ejemplo, una larga serie de instrucciones Write. Realizar cambios en el formato de la salida es más fácil y confiable.

## <a name="creating-a-run-time-text-template-in-any-application"></a>Crear una plantilla de texto en tiempo de ejecución en cualquier aplicación

#### <a name="to-create-a-run-time-text-template"></a>Para crear una plantilla de texto en tiempo de ejecución

1. En Explorador de soluciones, en el menú contextual del proyecto, elija **Agregar**, **nuevo elemento**.

2. En el cuadro de diálogo **Agregar nuevo elemento** , seleccione **plantilla de texto en tiempo de ejecución**. (En [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] mire en **Common Items\General**).

3. Escriba un nombre para el archivo de plantilla.

    > [!NOTE]
    > El nombre del archivo de plantilla se usará como nombre de clase en el código generado. Por lo tanto, no debe contener espacios ni signos de puntuación.

4. Haga clic en **Agregar**.

     Se crea un nuevo archivo que tiene la extensión **. TT**. Su propiedad de **herramienta personalizada** está establecida en **TextTemplatingFilePreprocessor**. Contiene las siguientes líneas:

    ```
    <#@ template language="C#" #>
    <#@ assembly name="System.Core" #>
    <#@ import namespace="System.Linq" #>
    <#@ import namespace="System.Text" #>
    <#@ import namespace="System.Collections.Generic" #>
    ```

## <a name="converting-an-existing-file-to-a-run-time-template"></a>Convertir un archivo existente en una plantilla en tiempo de ejecución
 Una buena manera de crear una plantilla es convertir un ejemplo existente de la salida. Por ejemplo, si la aplicación va a generar archivos HTML, puede empezar por crear un archivo HTML sin formato. Asegúrese de que funciona correctamente y de que su apariencia es correcta. Después, inclúyalo en el proyecto de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] y conviértalo en una plantilla.

#### <a name="to-convert-an-existing-text-file-to-a-run-time-template"></a>Para convertir un archivo de texto existente en una plantilla en tiempo de ejecución

1. Incluya el archivo en el proyecto de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. En Explorador de soluciones, en el menú contextual del proyecto, elija **Agregar**, **elemento existente**.

2. Establezca la propiedad **herramientas personalizadas** del archivo en **TextTemplatingFilePreprocessor**. En Explorador de soluciones, en el menú contextual del archivo, elija **propiedades**.

    > [!NOTE]
    > Si ya se ha establecido la propiedad, asegúrese de que es **TextTemplatingFilePreprocessor** y no **TextTemplatingFileGenerator**. Esto puede ocurrir si incluye un archivo que ya tiene la extensión **. TT**.

3. Cambie la extensión de nombre de archivo a **. TT**. Aunque este paso es opcional, le ayuda a evitar abrir el archivo en un editor incorrecto.

4. Quite los espacios o signos de puntuación de la parte principal del nombre de archivo. Por ejemplo, "mi Web Page.tt" sería incorrecto, pero "MyWebPage.tt" es correcto. El nombre de archivo se utilizará como nombre de clase en el código generado.

5. Inserte la siguiente línea al principio del archivo. Si está trabajando en un proyecto de Visual Basic, reemplace "C#" por "VB".

     `<#@ template language="C#" #>`

## <a name="the-content-of-the-run-time-template"></a>El contenido de la plantilla en tiempo de ejecución

### <a name="template-directive"></a>Directiva de plantilla
 Mantenga la primera línea de la plantilla tal como estaba al crear el archivo:

 `<#@ template language="C#" #>`

 El parámetro Language dependerá del lenguaje del proyecto.

### <a name="plain-content"></a>Contenido sin formato
 Edite el archivo **. TT** para que contenga el texto que desea que genere la aplicación. Por ejemplo:

```
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

 Observe que las instrucciones se insertan entre `<# ... #>` y se insertan expresiones entre `<#= ... #>`. Para obtener más información, vea [escribir una plantilla de texto T4](../modeling/writing-a-t4-text-template.md).

## <a name="using-the-template"></a>Uso de la plantilla

### <a name="the-code-built-from-the-template"></a>Código generado a partir de la plantilla
 Siempre que guarde el archivo **. TT** , se generará un archivo subsidiario **. CS** o **. VB** . Para ver este archivo en Explorador de soluciones, expanda el nodo del archivo **. TT** . En un proyecto de Visual Basic, podrá expandir el nodo después de hacer clic en **Mostrar todos los archivos** en la barra de herramientas de explorador de soluciones.

 Tenga en cuenta que este archivo subsidiario contiene una clase parcial que contiene un método denominado `TransformText()`. Puede llamar a este método desde la aplicación.

### <a name="generating-text-at-run-time"></a>Generar texto en tiempo de ejecución
 En el código de la aplicación, puede generar el contenido de la plantilla mediante una llamada como la siguiente:

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

 Para colocar la clase generada en un espacio de nombres determinado, establezca la propiedad espacio de nombres de la **herramienta personalizada** del archivo de plantilla de texto.

### <a name="debugging-runtime-text-templates"></a>Depuración de plantillas de texto en tiempo de ejecución
 Depure y pruebe las plantillas de texto en tiempo de ejecución del mismo modo que el código normal.

 Puede establecer un punto de interrupción en una plantilla de texto. Si inicia la aplicación en modo de depuración desde Visual Studio, puede recorrer el código y evaluar las expresiones de inspección de la manera habitual.

### <a name="passing-parameters-in-the-constructor"></a>Pasar parámetros en el constructor
 Normalmente, una plantilla debe importar algunos datos de otras partes de la aplicación. Para facilitar esta tarea, el código generado por la plantilla es una clase parcial. Puede crear otra parte de la misma clase en otro archivo del proyecto. Ese archivo puede incluir un constructor con parámetros, propiedades y funciones a las que puede tener acceso el código que está incrustado en la plantilla y el resto de la aplicación.

 Por ejemplo, puede crear un archivo **MyWebPageCode.CS**independiente:

```csharp
partial class MyWebPage
{
    private MyData m_data;
    public MyWebPage(MyData data) { this.m_data = data; }}
```

 En el archivo de plantilla **MyWebPage.TT**, puede escribir:

```csharp
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
 En [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], el archivo independiente **MyWebPageCode. VB** contiene:

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

```vb
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

 Y la plantilla se invocará pasando el parámetro en el constructor:

```vb
Dim data = New My.Templates.MyData
    ' Add data values here ....
Dim page = New My.Templates.MyWebPage(data)
Dim pageContent = page.TransformText()
System.IO.File.WriteAllText("outputPage.html", pageContent)

```

#### <a name="passing-data-in-template-properties"></a>Pasar datos en propiedades de plantilla
 Un método alternativo para pasar datos a la plantilla es agregar propiedades públicas a la clase de plantilla en una definición de clase parcial. La aplicación puede establecer las propiedades antes de invocar `TransformText()`.

 También puede agregar campos a la clase de plantilla en una definición parcial. Esto le permitirá pasar datos entre ejecuciones sucesivas de la plantilla.

### <a name="use-partial-classes-for-code"></a>Usar clases parciales para el código
 Muchos desarrolladores prefieren evitar escribir grandes cuerpos de código en las plantillas. En su lugar, defina métodos en una clase parcial que tenga el mismo nombre que el archivo de plantilla. Llame a esos métodos desde la plantilla. De este modo, la plantilla muestra más claramente cuál será el aspecto de la cadena de salida de destino. Las discusiones sobre la apariencia del resultado pueden separarse de la lógica de creación de los datos que muestra.

### <a name="assemblies-and-references"></a>Ensamblados y referencias
 Si desea que el código de plantilla haga referencia a un ensamblado .NET u otro ensamblado como **System. Xml. dll**, debe agregarlo a las **referencias** del proyecto de la manera habitual.

 Si desea importar un espacio de nombres de la misma manera que una instrucción `using`, puede hacerlo con la Directiva `import`:

```
<#@ import namespace="System.Xml" #>
```

 Estas directivas deben colocarse al principio del archivo, inmediatamente después de la Directiva de `<#@template`.

### <a name="shared-content"></a>Contenido compartido
 Si tiene texto que se comparte entre varias plantillas, puede colocarlo en un archivo independiente e incluirlo en cada archivo en el que debe aparecer:

```
<#@include file="CommonHeader.txt" #>
```

 El contenido incluido puede contener cualquier combinación de código de programa y texto sin formato, y puede contener otras directivas Include y otras directivas.

 La directiva Include se puede usar en cualquier parte del texto de un archivo de plantilla o un archivo incluido.

### <a name="inheritance-between-run-time-text-templates"></a>Herencia entre plantillas de texto en tiempo de ejecución
 Puede compartir contenido entre plantillas en tiempo de ejecución escribiendo una plantilla de clase base, que puede ser abstracta. Use el parámetro `inherits` de la Directiva `<@#template#>` para hacer referencia a otra clase de plantilla en tiempo de ejecución.

#### <a name="inheritance-pattern-fragments-in-base-methods"></a>Patrón de herencia: fragmentos en métodos base
 En el patrón que se usa en el ejemplo siguiente, tenga en cuenta los puntos siguientes:

- La clase base `SharedFragments` define métodos dentro de los bloques de características de clase `<#+ ... #>`.

- La clase base no contiene ningún texto libre. En su lugar, todos los bloques de texto se producen dentro de los métodos de características de clase.

- La clase derivada invoca los métodos definidos en `SharedFragments`.

- La aplicación llama al método `TextTransform()` de la clase derivada, pero no transforma la clase base `SharedFragments`.

- Las clases base y derivadas son plantillas de texto en tiempo de ejecución: es decir, la propiedad **herramienta personalizada** está establecida en **TextTemplatingFilePreprocessor**.

  **SharedFragments.tt:**

```csharp
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

```csharp
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

#### <a name="inheritance-pattern-text-in-base-body"></a>Patrón de herencia: texto en cuerpo base
 En este enfoque alternativo al uso de la herencia de plantilla, la mayor parte del texto se define en la plantilla base. Las plantillas derivadas proporcionan datos y fragmentos de texto que caben en el contenido base.

 **AbstractBaseTemplate1.tt:**

```csharp
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

```csharp
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

 **Código de la aplicación:**

```csharp
...
DerivedTemplate1 t1 = new DerivedTemplate1();
string result = t1.TransformText();
Console.WriteLine(result);
```

 **Salida resultante:**

```
Here is the description for this derived template:
  Description for this derived class

Here is the fragment specific to this derived template:
     Specific to DerivedTemplate1 : 42
End of common template.
End material for DerivedTemplate1.
```

## <a name="related-topics"></a>Temas relacionados
 Plantillas de tiempo de diseño: Si quiere usar una plantilla para generar código que se convierte en parte de la aplicación, consulte [generación de código en tiempo de diseño mediante plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

 Las plantillas en tiempo de ejecución se pueden usar en cualquier aplicación donde las plantillas y su contenido se determinan en tiempo de compilación. Pero si desea escribir una extensión de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que genere texto a partir de plantillas que cambian en tiempo de ejecución, consulte [invocar la transformación de texto en una extensión de vs](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="see-also"></a>Vea también
 [Generación de código y plantillas de texto T4](../modeling/code-generation-and-t4-text-templates.md) [escribir una plantilla de texto T4](../modeling/writing-a-t4-text-template.md) [Descripción de T4: plantillas de texto preprocesadas por Oleg Sych](https://github.com/olegsych/T4Toolbox)
