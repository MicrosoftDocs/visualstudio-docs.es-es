---
title: "Run-Time Text Generation with T4 Text Templates | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Preprocessed Text Template project item"
  - "TextTemplatingFilePreprocessor custom tool"
  - "text templates, TransformText() method"
  - "text templates, generating files at run time"
ms.assetid: 79b4b3c6-a9a7-4446-b6fd-e2388fc6b05f
caps.latest.revision: 22
caps.handback.revision: 22
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Run-Time Text Generation with T4 Text Templates
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede generar cadenas de texto en la aplicación en tiempo de ejecución mediante el uso de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] plantillas de texto en tiempo de ejecución.  El equipo donde la aplicación se ejecuta no tiene que tener [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Las plantillas en tiempo de ejecución a veces se denominan "preprocesado plantillas de texto" porque en tiempo de compilación, la plantilla genera código que se ejecuta en tiempo de ejecución.  
  
 Cada plantilla es una mezcla del texto tal y como aparecerá en la cadena generada y de fragmentos de código de programa.  Los fragmentos de programa proporciona valores para las partes variables de la cadena, y también controlan partes condicionales y repetidas.  
  
 Por ejemplo, la siguiente plantilla se podría utilizar en una aplicación que crea un informe HTML.  
  
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
  
 Observe que la plantilla es una página HTML en la que las partes variables se han reemplazado con código de programa.  Podría comenzar el diseño de este tipo de página escribiendo un prototipo estático de la página HTML.  A continuación, podría reemplazar la tabla y otras partes variables con código de programa que genera el contenido que varía de una ocasión a la siguiente.  
  
 Al utilizar una plantilla en la aplicación es más fácil ver la forma final de la salida en un plantilla que lo que podría ver, por ejemplo, en una larga serie de instrucciones write.  Realizar cambios en el formulario del resultado es más fácil y confiable.  
  
## Crear una plantilla de texto en tiempo de ejecución en cualquier aplicación  
  
#### Para crear una plantilla de texto en tiempo de ejecución  
  
1.  En el Explorador de soluciones, en el menú contextual del proyecto, elija  **Agregar**,  **Nuevo elemento**.  
  
2.  En el  **Agregar nuevo elemento** cuadro de diálogo, seleccione  **Plantilla de texto en tiempo de ejecución**.  \(En [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] busque en **Elementos comunes\\General**.\)  
  
3.  Escriba un nombre para el archivo de plantilla.  
  
    > [!NOTE]
    >  El nombre del archivo de plantilla se utilizará como nombre de clase en el código generado.  Por tanto, no debe tener espacios ni puntuación.  
  
4.  Elija  **Agregar**.  
  
     Se crea un nuevo archivo con la extensión **.tt**.  Su propiedad **Herramienta personalizada** se establece en **TextTemplatingFilePreprocessor**.  Contiene las líneas siguientes:  
  
    ```  
    <#@ template language="C#" #>  
    <#@ assembly name="System.Core" #>  
    <#@ import namespace="System.Linq" #>  
    <#@ import namespace="System.Text" #>  
    <#@ import namespace="System.Collections.Generic" #>  
    ```  
  
## Convertir un archivo existente en una plantilla en tiempo de ejecución  
 Una buena forma de crear una plantilla es convertir un ejemplo existente de la salida.  Por ejemplo, si la aplicación generará archivos HTML, puede comenzar creando un archivo HTML sin formato.  Asegúrese de que funciona correctamente y de que su aspecto es correcto.  A continuación, inclúyalo en el proyecto de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y conviértalo en una plantilla.  
  
#### Para convertir un archivo de texto existente en una plantilla en tiempo de ejecución  
  
1.  Incluya el archivo en el proyecto de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  En el Explorador de soluciones, en el menú contextual del proyecto, elija  **Agregar**,  **Elemento existente**.  
  
2.  Establezca la propiedad **Herramienta personalizada** del archivo en **TextTemplatingFilePreprocessor**.  En el Explorador de soluciones, en el menú contextual del archivo, elija  **Propiedades**.  
  
    > [!NOTE]
    >  Si la propiedad ya está establecida, asegúrese de que es **TextTemplatingFilePreprocessor** y no **TextTemplatingFileGenerator**.  Esto puede sucede si incluye un archivo que ya tiene la extensión **.tt**.  
  
3.  Cambie la extensión de nombre de archivo a **.tt**.  Aunque este paso es opcional, sirve de ayuda para evitar abrir el archivo en un editor incorrecto.  
  
4.  Quite cualquier espacio o puntuación de la parte principal del nombre de archivo.  Por ejemplo "Mi página web.tt" sería incorrecto, pero "MiPáginaWeb.tt" es correcto.  El nombre de archivo se utilizará como nombre de clase en el código generado.  
  
5.  Inserte la siguiente línea al principio del archivo.  Si trabaja en un proyecto de Visual Basic, reemplace "C\#" con "VB".  
  
     `<#@ template language="C#" #>`  
  
## Contenido de la plantilla en tiempo de ejecución  
  
### Directiva de plantilla  
 Mantenga la primera línea de la plantilla tal y como estaba cuando creó el archivo:  
  
 `<#@ template language="C#" #>`  
  
 El parámetro de lenguaje dependerá del lenguaje del proyecto.  
  
### Contenido sin formato  
 Edite el archivo **.tt** para incluir el texto que desea que genere la aplicación.  Por ejemplo:  
  
```  
<html><body>  
<h1>Sales for January</h2>  
<!-- table to be inserted here -->  
This report is Company Confidential.  
</body></html>  
```  
  
### Código de programa incrustado  
 Puede insertar código de programa entre `<#` y `#>`.  Por ejemplo:  
  
```c#  
<table>  
    <# for (int i = 1; i <= 10; i++)  
       { #>  
         <tr><td>Test name <#= i #> </td>  
             <td>Test value <#= i * i #> </td> </tr>  
    <# } #>  
 </table>  
```  
  
```vb#  
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
  
 Observe que las instrucciones se insertan entre `<# ... #>` y que las expresiones se insertan entre `<#= ... #>`.  Para obtener más información, vea [Writing a T4 Text Template](../modeling/writing-a-t4-text-template.md).  
  
## Utilizar la plantilla  
  
### Código compilado a partir de la plantilla  
 Siempre que guarda el archivo **.tt**, se genera un archivo **.cs** o **.vb** subsidiario.  Para ver este archivo en el Explorador de soluciones, expanda el nodo del archivo **.tt**.  En un proyecto de Visual Basic, podrá expandir el nodo después de hacer clic en **Mostrar todos los archivos** en la barra de herramientas del Explorador de soluciones.  
  
 Observe que este archivo subsidiario contiene una clase parcial que contiene un método denominado `TransformText()`.  Puede llamar a este método desde la aplicación.  
  
### Generar texto en tiempo de ejecución  
 En el código de aplicación, puede generar el contenido de la plantilla mediante una llamada similar a:  
  
```c#  
MyWebPage page = new MyWebPage();  
String pageContent = page.TransformText();  
System.IO.File.WriteAllText("outputPage.html", pageContent);  
  
```  
  
```vb#  
Dim page = New My.Templates.MyWebPage  
Dim pageContent = page.TransformText()  
System.IO.File.WriteAllText("outputPage.html", pageContent)  
  
```  
  
 Para colocar la clase generada en un espacio de nombres determinado, establezca la propiedad **Espacio de nombres de la herramienta personalizada** del archivo de plantilla de texto.  
  
### Depuración de las plantillas de texto en tiempo de ejecución  
 Depurar y probar las plantillas de texto en tiempo de ejecución de la misma forma que código común.  
  
 Puede establecer un punto de interrupción en una plantilla de texto.  Si la aplicación se inicia en modo de depuración de Visual Studio, puede recorrer el código y evaluar expresiones de inspección de la forma habitual.  
  
### Pasar parámetros en el constructor  
 Normalmente una plantilla debe importar algunos datos de otras partes de la aplicación.  Para que esto resulte más sencillo, el código que compila la plantilla es una clase parcial.  Puede crear otra parte de la misma clase en otro archivo del proyecto.  Este archivo puede incluir un constructor con parámetros, propiedades y funciones a los que pueden tener acceso el código incrustado en la plantilla y el resto de la aplicación.  
  
 Por ejemplo, podría crear un archivo independiente **MyWebPageCode.cs**:  
  
```c#  
partial class MyWebPage  
{  
    private MyData m_data;  
    public MyWebPage(MyData data) { this.m_data = data; }}  
```  
  
 En el archivo de plantilla **MyWebPage.tt**, podría escribir:  
  
```c#  
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
  
 Para utilizar esta plantilla en la aplicación:  
  
```c#  
MyData data = ...;  
MyWebPage page = new MyWebPage(data);  
String pageContent = page.TransformText();  
System.IO.File.WriteAllText("outputPage.html", pageContent);  
```  
  
#### Parámetros de constructor en Visual Basic  
 En [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], el archivo independiente **MyWebPageCode.vb** contiene:  
  
```vb#  
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
  
```vb#  
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
  
 Y la plantilla podría ser invocada pasando el parámetro en el constructor:  
  
```vb#  
Dim data = New My.Templates.MyData  
    ' Add data values here ....  
Dim page = New My.Templates.MyWebPage(data)  
Dim pageContent = page.TransformText()  
System.IO.File.WriteAllText("outputPage.html", pageContent)  
  
```  
  
#### Pasar datos en las propiedades de plantilla  
 Un método alternativo de pasar datos a la plantilla es agregar las propiedades públicas a la clase de plantilla en una definición de clase parcial.  La aplicación puede establecer las propiedades antes de invocar `TransformText()`.  
  
 También puede agregar campos a la clase de plantilla en una definición parcial.  Esto le permitiría pasar datos entre las ejecuciones sucesivas de la plantilla.  
  
### Utilizar clases parciales para el código  
 Muchos desarrolladores prefieren evitar escribir cuerpos grandes de código en plantillas.  En su lugar, defina métodos en una clase parcial que tiene el mismo nombre que el archivo de plantilla.  Llame a esos métodos desde la plantilla.  De esta manera, la plantilla muestra más claramente el aspecto de la cadena de salida de destino.  Debates sobre la apariencia del resultado pueden separarse de la lógica de la creación de datos que muestran.  
  
### Ensamblados y referencias  
 Si desea que el código de plantilla haga referencia a .NET u otro ensamblado como **System.Xml.dll**, debe agregarlo a las **referencias** del proyecto de la manera habitual.  
  
 Si desea importar un espacio de nombres de la misma manera que una instrucción `using`, puede hacerlo con la directiva `import`:  
  
```  
<#@ import namespace="System.Xml" #>  
```  
  
 Estas directivas se deben colocar al principio del archivo, inmediatamente después de la directiva `<#@template`.  
  
### Contenido compartido  
 Si tiene texto compartido entre varias plantillas, puede colocarlo en un archivo independiente e incluir este en cada archivo donde debe aparecer:  
  
```  
<#@include file="CommonHeader.txt" #>  
```  
  
 El contenido incluido puede contener cualquier mezcla de código de programa y texto sin formato, y puede contener otras directivas de inclusión y otras directivas.  
  
 La directiva de inclusión se puede utilizar en cualquier lugar dentro del texto de un archivo de plantilla o de un archivo incluido.  
  
### Herencia entre plantillas de texto en tiempo de ejecución  
 Puede compartir el contenido entre plantillas en tiempo de ejecución escribiendo una plantilla de clase base, que puede ser abstracta.  Uso del `inherits` parámetro de la `<@#template#>` la directiva para hacer referencia a otra clase de plantilla en tiempo de ejecución.  
  
#### Modelo de herencia: fragmentos en métodos base  
 En el modelo utilizado en el ejemplo que aparece a continuación, observe los siguientes puntos:  
  
-   La clase base `SharedFragments` define los métodos dentro de los bloques de características de clase `<#+ ... #>`.  
  
-   La clase base no contiene ningún texto libre.  En su lugar, todos sus bloques de texto se producen dentro de los métodos de característica de clase.  
  
-   La clase derivada invoca a los métodos definidos en `SharedFragments`.  
  
-   La aplicación llama al método `TextTransform()` de la clase derivada, pero no transforma la clase base `SharedFragments`.  
  
-   Las clases base y derivadas son las plantillas de texto en tiempo de ejecución: es decir, el  **Herramienta personalizada** está establecida en  **TextTemplatingFilePreprocessor**.  
  
 **SharedFragments.tt:**  
  
```c#  
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
  
```c#  
<#@ template language="C#" inherits="SharedFragments" #>  
begin 1  
   <# SharedText(2); #>  
end 1  
  
```  
  
 **MyProgram.cs:**  
  
```c#  
...   
MyTextTemplate1 t1  = new MyTextTemplate1();  
string result = t1.TransformText();  
Console.WriteLine(result);  
```  
  
 **Resultado que se obtiene:**  
  
```  
begin 1  
    Shared Text 2  
end 1  
```  
  
#### Modelo de herencia: texto en el cuerpo base  
 En este enfoque alternativo al uso de la herencia de plantillas, la mayor parte del texto está definida en la plantilla base.  Las plantillas derivadas proporcionan datos y fragmentos de texto que se ajustan en el contenido base.  
  
 **AbstractBaseTemplate1.tt:**  
  
```c#  
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
  
```c#  
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
  
```c#  
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
  
## Temas relacionados  
 Plantillas en tiempo de diseño: si desea utilizar una plantilla para generar código que pase a formar parte de la aplicación, vea [Design\-Time Code Generation by using T4 Text Templates](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
 Las plantillas en tiempo de ejecución pueden utilizarse en cualquier aplicación donde se determinan las plantillas y su contenido en tiempo de compilación.  Pero si desea escribir una extensión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que genere texto a partir de plantillas que cambian en tiempo de ejecución, vea [Invoking Text Transformation in a VS Extension](../modeling/invoking-text-transformation-in-a-vs-extension.md).  
  
## Vea también  
 [Code Generation and T4 Text Templates](../modeling/code-generation-and-t4-text-templates.md)   
 [Writing a T4 Text Template](../modeling/writing-a-t4-text-template.md)   
 [Comprensión T4: Preprocesa las plantillas de texto mediante la sincronización de directorios de Oleg](http://www.olegsych.com/2009/09/t4-preprocessed-text-templates/)