---
title: Writing a T4 Text Template | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, syntax
- text templates, guide
- text templates, functions that generate text
ms.assetid: 94328da7-953b-4e92-9587-648543d1f732
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bcd5a4996db4a5e374baabe4f52d5fd1dbac2e5e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301115"
---
# <a name="writing-a-t4-text-template"></a>Escribir una plantilla de texto T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Una plantilla de texto contiene el texto que se generará a partir de ella. For example, a template that creates a web page will contain "\<html>…" and all the other standard parts of an HTML page. Inserted into the template are *control blocks*, which are fragments of program code. Los bloques de control proporcionan valores variables y permiten que partes del texto sean condiciones y se repitan.

 Esta estructura hace que una plantilla sea fácil de desarrollar, porque se puede comenzar con un prototipo del archivo generado e incrementalmente insertar bloques de control que modifican el resultado.

 Las plantillas de texto se componen de las siguientes partes:

- **Directives** - elements that control how the template is processed.

- **Text blocks** - content that is copied directly to the output.

- **Control blocks** - program code that inserts variable values into the text, and controls conditional or repeated parts of the text.

  To try the examples in this topic, copy them into a template file as described in [Design-Time Code Generation by using T4 Text Templates](../modeling/design-time-code-generation-by-using-t4-text-templates.md). After editing the template file, save it, and then inspect the output **.txt** file.

## <a name="directives"></a>Directivas
 Las directivas de plantilla de texto proporcionan instrucciones generales al motor de creación de plantillas de texto sobre cómo generar el código de transformación y el archivo de salida.

 Por ejemplo, la siguiente directiva especifica que el archivo de salida debe tener una extensión .txt:

```

<#@ output extension=".txt" #>
```

 For more information about directives, see [T4 Text Template Directives](../modeling/t4-text-template-directives.md).

## <a name="text-blocks"></a>Bloques de texto
 Un bloque de texto inserta texto directamente en el archivo de salida. No existe ningún formato especial para los bloques de texto. Por ejemplo, la siguiente plantilla de texto generará un archivo de texto con la palabra "Hello":

```
<#@ output extension=".txt" #>
Hello
```

## <a name="control-blocks"></a>Bloques de control
 Los bloques de control son secciones de código de programa que se utilizan para transformar las plantillas. El lenguaje predeterminado es C#, pero para utilizar [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] puede escribir esta directiva al principio del archivo:

```
<#@ template language="VB" #>
```

 El lenguaje en el que escribe el código de los bloques de control no está relacionado con el lenguaje del texto que se genera.

### <a name="standard-control-blocks"></a>Bloques de control estándar
 Un bloque de control estándar es una sección de código de programa que genera parte del archivo de salida.

 Puede mezclar cualquier número de bloques de texto y bloques de control estándar en un archivo de plantilla. Sin embargo, no puede colocar un bloque de control dentro de otro. Cada bloque de control estándar se delimita con los símbolos `<# ... #>`.

 Por ejemplo, los bloques siguientes de control y de texto establecen que el archivo de salida contenga la línea "0, 1, 2, 3, 4 Hello!":

```

      <#
    for(int i = 0; i < 4; i++)
    {
        Write(i + ", ");
    }
    Write("4");
#> Hello!
```

 En lugar de utilizar instrucciones `Write()` explícitas, puede intercalar texto y código. The following example prints "Hello!" four times:

```
<#
    for(int i = 0; i < 4; i++)
    {
#>
Hello!
<#
    }
#>
```

 Puede insertar un bloque de texto en cualquier posición del código donde se podría incluir una instrucción `Write();`.

> [!NOTE]
> When you embed a text block within a compound statement such as a loop or conditional, always use braces {...} to contain the text block.

### <a name="expression-control-blocks"></a>Bloques de control de expresiones
 Un bloque de control de expresiones da como resulta una expresión y la convierte en una cadena. Esta cadena se inserta en el archivo de salida.

 Los bloques de control de expresiones se delimitan mediante los símbolos `<#= ... #>`.

 Por ejemplo, el siguiente bloque de control hace que el archivo de salida contenga "5":

```
<#= 2 + 3 #>
```

 Notice that the opening symbol has three characters "<#=".

 La expresión puede incluir cualquier variable que esté en el ámbito. Por ejemplo, este bloque imprime líneas con números:

```
<#@ output extension=".txt" #>
<#
    for(int i = 0; i < 4; i++)
    {
#>
This is hello number <#= i+1 #>: Hello!
<#
    }
#>
```

### <a name="class-feature-control-blocks"></a>Bloques de control de características de clase
 Un bloque de control de características de clase define propiedades, métodos o cualquier otro código que no se debe incluir en la transformación principal. Los bloques de características de clase se utilizan con frecuencia para las funciones del asistente.  Typically, class feature blocks are placed in separate files so that they can be [included](#Include) by more than one text template.

 Los bloques de control de características de clase se delimitan con los símbolos `<#+ ... #>`.

 Por ejemplo, el siguiente archivo de plantilla declara y utiliza un método:

```
<#@ output extension=".txt" #>
Squares:
<#
    for(int i = 0; i < 4; i++)
    {
#>
    The square of <#= i #> is <#= Square(i+1) #>.
<#
    }
#>
That is the end of the list.
<#+   // Start of class feature block
private int Square(int i)
{
    return i*i;
}
#>
```

 Las características de clase se deben colocar al final del archivo donde se escriben. Sin embargo, puede utilizar `<#@include#>` para un archivo que incluye una característica de clase, aunque la directiva `include` vaya seguida de bloques estándar y texto.

 For more information about control blocks, see [Text Template Control Blocks](../modeling/text-template-control-blocks.md).

### <a name="class-feature-blocks-can-contain-text-blocks"></a>Los bloques de características de clase pueden contener bloques de texto
 Puede escribir un método que genere texto. Por ejemplo:

```
List of Squares:
<#
   for(int i = 0; i < 4; i++)
   {  WriteSquareLine(i); }
#>
End of list.
<#+   // Class feature block
private void WriteSquareLine(int i)
{
#>
   The square of <#= i #> is <#= i*i #>.
<#+
}
#>
```

 Resulta especialmente útil para colocar un método que genera texto en un archivo independiente que se puede incluir con más de una plantilla.

## <a name="using-external-definitions"></a>Utilizar definiciones externas

### <a name="assemblies"></a>Ensamblados
 Los bloques de código de la plantilla pueden utilizar tipos que se definen en los ensamblados de uso más frecuente de .NET, como System.dll. Además, puede hacer referencia a otros ensamblados .NET o a sus propios ensamblados. Puede proporcionar un nombre de ruta de acceso o el nombre seguro de un ensamblado:

```
<#@ assembly name="System.Xml" #>
```

 Debería utilizar nombres de ruta de acceso absolutos o utilizar nombres de macro estándar en el nombre de ruta. Por ejemplo:

```
<#@ assembly name="$(SolutionDir)library\MyAssembly.dll" #>
```

 For a list of macros, see [Common Macros for Build Commands and Properties](https://msdn.microsoft.com/library/239bd708-2ea9-4687-b264-043f1febf98b).

 The assembly directive has no effect in a [preprocessed text template](../modeling/run-time-text-generation-with-t4-text-templates.md).

 For more information, see [T4 Assembly Directive](../modeling/t4-assembly-directive.md).

### <a name="namespaces"></a>Espacios de nombres
 La directiva de importación es igual que la cláusula `using` en C# o la cláusula `imports` en Visual Basic. Permite hacer referencia a tipos del código sin utilizar un nombre completo:

```
<#@ import namespace="System.Xml" #>
```

 Puede utilizar tantas directivas `assembly` e `import` como desee. Debe colocarlas antes de los bloques del texto y de control.

 For more information, see [T4 Import Directive](../modeling/t4-import-directive.md).

### <a name="Include"></a> Including code and text
 La directiva `include` inserta texto de otro archivo de plantilla. Por ejemplo, esta directiva inserta el contenido de `test.txt`.

 `<#@ include file="c:\test.txt" #>`

 El contenido incluido se procesa casi como si formase parte de la plantilla de texto que lo incluye. Sin embargo, puede incluir un archivo que contenga un bloque de características de clase `<#+...#>` aunque la directiva de inclusión vaya seguida de texto normal y de bloques de control estándar.

 For more information, see [T4 Include Directive](../modeling/t4-include-directive.md).

### <a name="utility-methods"></a>Métodos de utilidad
 Existen varios métodos como `Write()` que siempre están disponibles en un bloque de control. Incluyen métodos para ayudarle a aplicar sangría al resultado y para notificar errores.

 También puede escribir su propio conjunto de métodos de utilidad.

 For more information, see [Text Template Utility Methods](../modeling/text-template-utility-methods.md).

## <a name="transforming-data-and-models"></a>Transformar datos y modelos
 La aplicación más útil para una plantilla de texto consiste en generar material basado en el contenido de un origen como un modelo, una base de datos o un archivo de datos. La plantilla extrae y cambia el formato de los datos. Una colección de plantillas puede transformar este origen en varios archivos.

 Hay varios enfoques para leer el archivo de origen.

 **Read a file in the text template**. Esta es manera más sencilla de incluir los datos en la plantilla:

```
<#@ import namespace="System.IO" #>
<# string fileContent = File.ReadAllText(@"C:\myData.txt"); ...
```

 **Load a file as a navigable model**. Un método más eficaz consiste en leer los datos como un modelo, en el que el código de la plantilla de texto puede navegar. Por ejemplo, puede cargar un archivo XML y navegar en él con expresiones XPath. You could also use [xsd.exe](https://go.microsoft.com/fwlink/?LinkId=178765) to create a set of classes with which you can read the XML data.

 **Edit the model file in a diagram or form.** [!INCLUDE[dsl](../includes/dsl-md.md)] provides tools that let you edit a model as a diagram or Windows form. Así resulta más fácil analizar el modelo con los usuarios de la aplicación generada. [!INCLUDE[dsl](../includes/dsl-md.md)] también crea un conjunto de clases fuertemente tipadas que reflejan la estructura del modelo. For more information, see [Generating Code from a Domain-Specific Language](../modeling/generating-code-from-a-domain-specific-language.md).

 **Use a UML model**. Puede generar código a partir de un modelo UML. Esto ofrece la ventaja de que el modelo se puede editar como un diagrama en una notación familiar. Además, no tiene que diseñar el diagrama. For more information, see [Generate files from a UML model](../modeling/generate-files-from-a-uml-model.md).

### <a name="relative-file-paths-in-design-time-templates"></a>Rutas de acceso de archivo relativas en plantillas en tiempo de diseño
 In a [design-time text template](../modeling/design-time-code-generation-by-using-t4-text-templates.md), if you want to reference a file in a location relative to the text template, use `this.Host.ResolvePath()`. También debe establecer `hostspecific="true"` en la directiva `template`:

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.IO" #>
<#
 // Find a path within the same project as the text template:
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));
#>
Content of MyFile.txt is:
<#= myFile #>

```

 Además, puede obtener otros servicios que proporciona el host. For more information, see [Accessing Visual Studio or other Hosts from a Template](https://msdn.microsoft.com/0556f20c-fef4-41a9-9597-53afab4ab9e4).

### <a name="design-time-text-templates-run-in-a-separate-appdomain"></a>Plantillas de texto en tiempo de diseño que se ejecutan en un AppDomain independiente
 You should be aware that a [design-time text template](../modeling/design-time-code-generation-by-using-t4-text-templates.md) runs in an AppDomain that is separate from the main application. En la mayoría de los casos esto no es importante, pero se pueden detectar restricciones en ciertos casos complejos. Por ejemplo, si desea pasar datos dentro o fuera de la plantilla de un servicio independiente, el servicio debe proporcionar una API serializable.

 (This isn’t true of a [run-time text template](../modeling/run-time-text-generation-with-t4-text-templates.md), which provides code that is compiled along with the rest of your code.)

## <a name="editing-templates"></a>Editar plantillas
 Se pueden descargar editores de plantillas del texto especializados de la Galería en línea del Administrador de extensiones. On the **Tools** menu, click **Extension Manager**. Click **Online Gallery**, and then use the search tool.

## <a name="related-topics"></a>Temas relacionados

|Tarea|Tema|
|----------|-----------|
|Escribir una plantilla.|[Instrucciones para escribir plantillas de texto T4](../modeling/guidelines-for-writing-t4-text-templates.md)|
|Genere texto utilizando código de programa.|[Text Template Structure](../modeling/writing-a-t4-text-template.md)|
|Genere archivos en una solución de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|[Generación de código en tiempo de diseño mediante plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Ejecute la generación de texto fuera de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|[Generar archivos con la utilidad TextTransform](../modeling/generating-files-with-the-texttransform-utility.md)|
|Transforme los datos al formato de un lenguaje específico de dominio.|[Generar código a partir de lenguajes específicos de dominio](../modeling/generating-code-from-a-domain-specific-language.md)|
|Escriba procesadores de directivas para transformar sus propios orígenes de datos.|[Personalizar la transformación de texto T4](../modeling/customizing-t4-text-transformation.md)|
