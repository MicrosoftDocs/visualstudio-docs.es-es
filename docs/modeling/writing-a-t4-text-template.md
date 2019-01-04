---
title: Escribir una plantilla de texto T4
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, syntax
- text templates, guide
- text templates, functions that generate text
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: b78e34205c2b7af36f3c43f2307fd62bfca6fe39
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990521"
---
# <a name="writing-a-t4-text-template"></a>Escribir una plantilla de texto T4
Una plantilla de texto contiene el texto que se generará a partir de ella. Por ejemplo, una plantilla que crea una página web contendrá "\<html >..." y todas las demás partes estándar de una página HTML. Inserta en la plantilla son *bloques de control*, que son fragmentos de código de programa. Los bloques de control proporcionan valores variables y permiten que partes del texto sean condiciones y se repitan.

 Esta estructura hace que una plantilla sea fácil de desarrollar, porque se puede comenzar con un prototipo del archivo generado e incrementalmente insertar bloques de control que modifican el resultado.

 Las plantillas de texto se componen de las siguientes partes:

-   **Directivas** -elementos que controlan cómo se procesa la plantilla.

-   **Bloques de texto** : contenido que se copia directamente en la salida.

-   **Bloques de control** -código de programa que inserta valores variables en el texto y controla las partes condicionales o repetidas del texto.

Para probar los ejemplos de este tema, cópielos en un archivo de plantilla como se describe en [generación de código de tiempo de diseño mediante el uso de plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md). Después de editar el archivo de plantilla, guárdelo y, a continuación, inspeccione la salida **.txt** archivo.

## <a name="directives"></a>Directivas
 Las directivas de plantilla de texto proporcionan instrucciones generales al motor de creación de plantillas de texto sobre cómo generar el código de transformación y el archivo de salida.

 Por ejemplo, la siguiente directiva especifica que el archivo de salida debe tener una extensión .txt:

```
<#@ output extension=".txt" #>
```

 Para obtener más información sobre las directivas, consulte [directivas de plantilla de texto T4](../modeling/t4-text-template-directives.md).

## <a name="text-blocks"></a>Bloques de texto
 Un bloque de texto inserta texto directamente en el archivo de salida. No existe ningún formato especial para los bloques de texto. Por ejemplo, la siguiente plantilla de texto generará un archivo de texto con la palabra "Hello":

```
<#@ output extension=".txt" #>
Hello
```

## <a name="control-blocks"></a>Bloques de control
 Los bloques de control son secciones de código de programa que se utilizan para transformar las plantillas. El lenguaje predeterminado es C#, pero para utilizar [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] puede escribir esta directiva al principio del archivo:

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

 En lugar de utilizar instrucciones `Write()` explícitas, puede intercalar texto y código. En el ejemplo siguiente se imprime "¡Hello!" cuatro veces:

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
>  Al incrustar un bloque de texto dentro de una instrucción compuesta como un bucle o condicional, debe usar siempre corchetes {...} para contener el bloque de texto.

### <a name="expression-control-blocks"></a>Bloques de control de expresiones
 Un bloque de control de expresiones da como resulta una expresión y la convierte en una cadena. Esta cadena se inserta en el archivo de salida.

 Los bloques de control de expresiones se delimitan mediante los símbolos `<#= ... #>`.

 Por ejemplo, el siguiente bloque de control hace que el archivo de salida contenga "5":

```
<#= 2 + 3 #>
```

 Observe que el símbolo de apertura tiene tres caracteres "<#=".

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
 Un bloque de control de características de clase define propiedades, métodos o cualquier otro código que no se debe incluir en la transformación principal. Los bloques de características de clase se utilizan con frecuencia para las funciones del asistente.  Normalmente, los bloques de características de clase se colocan en archivos independientes para que se pueden [incluyen](#Include) por más de una plantilla de texto.

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

 Para obtener más información acerca de los bloques de control, vea [bloques de Control de plantilla de texto](../modeling/text-template-control-blocks.md).

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

 La directiva de ensamblado no tiene ningún efecto un [plantilla de texto preprocesada](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Para obtener más información, consulte [directiva de ensamblado T4](../modeling/t4-assembly-directive.md).

### <a name="namespaces"></a>Espacios de nombres
 La directiva de importación es igual que la cláusula `using` en C# o la cláusula `imports` en Visual Basic. Permite hacer referencia a tipos del código sin utilizar un nombre completo:

```
<#@ import namespace="System.Xml" #>
```

 Puede utilizar tantas directivas `assembly` e `import` como desee. Debe colocarlas antes de los bloques del texto y de control.

 Para obtener más información, consulte [directiva de importación T4](../modeling/t4-import-directive.md).

### <a name="Include"></a> Incluir código y texto
 La directiva `include` inserta texto de otro archivo de plantilla. Por ejemplo, esta directiva inserta el contenido de `test.txt`.

```
<#@ include file="c:\test.txt" #>
```

 El contenido incluido se procesa casi como si formase parte de la plantilla de texto que lo incluye. Sin embargo, puede incluir un archivo que contenga un bloque de características de clase `<#+...#>` aunque la directiva de inclusión vaya seguida de texto normal y de bloques de control estándar.

 Para obtener más información, consulte [directiva Include de T4](../modeling/t4-include-directive.md).

### <a name="utility-methods"></a>Métodos de utilidad
 Existen varios métodos como `Write()` que siempre están disponibles en un bloque de control. Incluyen métodos para ayudarle a aplicar sangría al resultado y para notificar errores.

 También puede escribir su propio conjunto de métodos de utilidad.

 Para obtener más información, consulte [métodos de utilidad de plantilla de texto](../modeling/text-template-utility-methods.md).

## <a name="transforming-data-and-models"></a>Transformar datos y modelos
 La aplicación más útil para una plantilla de texto consiste en generar material basado en el contenido de un origen como un modelo, una base de datos o un archivo de datos. La plantilla extrae y cambia el formato de los datos. Una colección de plantillas puede transformar este origen en varios archivos.

 Hay varios enfoques para leer el archivo de origen.

 **Leer un archivo en la plantilla de texto**. Esta es manera más sencilla de incluir los datos en la plantilla:

```
<#@ import namespace="System.IO" #>
<# string fileContent = File.ReadAllText(@"C:\myData.txt"); ...
```

 **Cargar un archivo como un modelo navegable**. Un método más eficaz consiste en leer los datos como un modelo, en el que el código de la plantilla de texto puede navegar. Por ejemplo, puede cargar un archivo XML y navegar en él con expresiones XPath. También puede usar [xsd.exe](http://go.microsoft.com/fwlink/?LinkId=178765) para crear un conjunto de clases con las que puede leer los datos XML.

 **Edite el archivo de modelo en un diagrama o formulario.** [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] proporciona herramientas que permiten editar un modelo como un diagrama o formulario de Windows. Así resulta más fácil analizar el modelo con los usuarios de la aplicación generada. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] también crea un conjunto de clases fuertemente tipadas que reflejan la estructura del modelo. Para obtener más información, consulte [generar código desde un lenguaje específico de dominio](../modeling/generating-code-from-a-domain-specific-language.md).

### <a name="relative-file-paths-in-design-time-templates"></a>Rutas de acceso de archivo relativas en plantillas en tiempo de diseño
 En un [plantilla de texto en tiempo de diseño](../modeling/design-time-code-generation-by-using-t4-text-templates.md), si desea hacer referencia a un archivo en una ubicación relativa a la plantilla de texto, use `this.Host.ResolvePath()`. También debe establecer `hostspecific="true"` en la directiva `template`:

```
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

Además, puede obtener otros servicios que proporciona el host. Para obtener más información, consulte [acceso a Visual Studio u otros Hosts desde una plantilla](/previous-versions/visualstudio/visual-studio-2010/gg604090\(v\=vs.100\)).

### <a name="design-time-text-templates-run-in-a-separate-appdomain"></a>Plantillas de texto en tiempo de diseño que se ejecutan en un AppDomain independiente

 Debe tener en cuenta que un [plantilla de texto en tiempo de diseño](../modeling/design-time-code-generation-by-using-t4-text-templates.md) se ejecuta en un AppDomain que es independiente de la aplicación principal. En la mayoría de los casos esto no es importante, pero se pueden detectar restricciones en ciertos casos complejos. Por ejemplo, si desea pasar datos dentro o fuera de la plantilla de un servicio independiente, el servicio debe proporcionar una API serializable.

 (Esto no es verdadero para un [plantilla de texto de tiempo de ejecución](../modeling/run-time-text-generation-with-t4-text-templates.md), que proporciona el código que se compila junto con el resto del código.)

## <a name="editing-templates"></a>Editar plantillas
 Se pueden descargar editores de plantillas del texto especializados de la Galería en línea del Administrador de extensiones. En el **herramientas** menú, haga clic en **Administrador de extensiones**. Haga clic en **Galería en línea**y, a continuación, use la herramienta de búsqueda.

## <a name="related-topics"></a>Temas relacionados

|Tarea|Tema|
|-|-|
|Escribir una plantilla.|[Instrucciones para escribir plantillas de texto T4](../modeling/guidelines-for-writing-t4-text-templates.md)|
|Genere texto utilizando código de programa.|[Estructura de la plantilla de texto](../modeling/writing-a-t4-text-template.md)|
|Generar archivos en una solución de Visual Studio.|[Generación de código en tiempo de diseño mediante plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Ejecute la generación de texto fuera de Visual Studio.|[Generar archivos con la utilidad TextTransform](../modeling/generating-files-with-the-texttransform-utility.md)|
|Transforme los datos al formato de un lenguaje específico de dominio.|[Generar código a partir de lenguajes específicos de dominio](../modeling/generating-code-from-a-domain-specific-language.md)|
|Escriba procesadores de directivas para transformar sus propios orígenes de datos.|[Personalizar la transformación de texto T4](../modeling/customizing-t4-text-transformation.md)|
