---
title: Bloques de Control de plantilla de texto | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- text templates, template code
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: aea2d274e209c6ea0493da4bd743b008c9a5921f
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="text-template-control-blocks"></a>Bloques de control de las plantillas de texto
Bloques de control le permite escribir código en su plantilla de texto para variar el resultado. Hay tres tipos de bloques de control, que se distinguen por los corchetes de apertura:  
  
-   `<# Standard control blocks #>` puede contener instrucciones.  
  
-   `<#= Expression control blocks #>` puede contener expresiones.  
  
-   `<#+ Class feature control blocks #>` puede contener métodos, campos y propiedades.  
  
## <a name="standard-control-block"></a>Bloque de control estándar  
 Los bloques de control estándar contienen instrucciones. Por ejemplo, el siguiente bloque estándar obtiene los nombres de todos los atributos del documento XML:  
  
```  
<#@ assembly name="System.Xml.dll" #>  
<#@ import namespace="System.Xml" #>  
  
<#  
    List<string> allAttributes = new List<string>();  
    XmlDocument xDoc = new XmlDocument();  
    xDoc.Load(@"E:\CSharp\Overview.xml");  
    XmlAttributeCollection attributes = xDoc.Attributes;  
    if (attributes.Count > 0)  
    {  
       foreach (XmlAttribute attr in attributes)  
       {  
           allAtributes.Add(attr.Name);  
       }  
     }    
#>  
```  
  
 Puede insertar texto sin formato dentro de una instrucción compuesta como `if` o `for`. Por ejemplo, este fragmento genera una línea de salida de cada iteración del bucle:  
  
```  
<#  
       foreach (XmlAttribute attr in attributes)  
       {  
#>  
Found another one!  
<#  
           allAtributes.Add(attr.Name);  
       }  
#>  
```  
  
> [!WARNING]
>  Utilice siempre {...} para delimitar instrucciones anidadas que contengan texto sin formato insertado. El siguiente ejemplo podría no funcionar correctamente:  
>   
>  `<# if (ShouldPrint) #> Some text. -- WRONG`  
>   
>  En su lugar, debe incluir {llaves}, como sigue:  
  
```  
  
<#  
 if (ShouldPrint)  
 {   //  "{" REQUIRED  
#>  
Some text.  
<#  
 }   
#>  
  
```  
  
## <a name="expression-control-block"></a>Bloque de control de expresiones  
 Los bloques de control de expresiones se utilizan para el código que proporciona cadenas que se deben escribir en el archivo de salida. Por ejemplo, con el ejemplo anterior, puede imprimir los nombres de los atributos en el archivo de salida modificando el bloque de código como sigue:  
  
```  
<#  
    XmlDocument xDoc = new XmlDocument();  
    xDoc.Load(@"E:\CSharp\Overview.xml");  
    XmlAttributeCollection attributes = xDoc.Attributes;  
    if (attributes != null)  
    {  
       foreach (XmlAttribute attr in attributes)  
       {   
#><#= attr.Name #><#  
       }  
    }  
#>  
```  
  
## <a name="class-feature-control-block"></a>Bloque de control de características de clase  
 Puede utilizar los bloques de control de características de clase para agregar a su plantilla de texto métodos, propiedades, campos o incluso clases anidadas. El uso más común de los bloques de características de clase es proporcionar funciones auxiliares para el código en otras partes de la plantilla de texto. Por ejemplo, el siguiente bloque de características de clase pone en mayúscula la primera letra del nombre del atributo (o, si el nombre contiene espacios en blanco, pone en mayúscula la primera letra de cada palabra):  
  
```  
<#@ import namespace="System.Globalization" #>  
```  
  
```  
<#+  
    private string FixAttributeName(string name)  
    {  
        return CultureInfo.CurrentCulture.TextInfo.ToTitleCase(name);  
    }  
#>  
```  
  
> [!NOTE]
>  Un bloque de control de características de clase no debe ir seguido de bloques de control estándar en el mismo archivo de plantilla. Sin embargo, esta restricción no se aplica al resultado del uso de directivas `<#@include#>`. Cada archivo incluido puede tener bloques estándar seguidos de bloques de características de clase.  
  
 Puede crear una función que genere el resultado insertando bloques de texto y de expresiones dentro de un bloque de control de características de clase. Por ejemplo:  
  
```  
<#+  
    private void OutputFixedAttributeName(string name)  
    {  
#>  
 Attribute:  <#= CultureInfo.CurrentCulture.TextInfo.ToTitleCase(name) #>  
<#+  // <<< Notice that this is also a class feature block.  
    }  
#>  
```  
  
 Podría llamar a esta función desde un bloque estándar o desde otro bloque de características de clase:  
  
```  
<# foreach (Attribute attribute in item.Attributes)  
{  
  OutputFixedAttributeName(attribute.Name);  
}  
#>  
```  
  
## <a name="how-to-use-control-blocks"></a>Cómo usar los bloques de control  
 Todo el código de todos los bloques de control estándar y de expresiones de una única plantilla (incluido el código de las plantillas incluidas) se combina para formar el método `TransformText()` del código generado. (Para obtener más información acerca de cómo incluir otras plantillas de texto con el `include` directiva, consulte [directivas de plantilla de texto T4](../modeling/t4-text-template-directives.md).)  
  
 Cuando utilice bloques de control, debe tener en cuenta las siguientes consideraciones:  
  
-   **Language.** En una plantilla de texto puede utilizar el código C# o Visual Basic. El lenguaje predeterminado es C#, pero puede especificar Visual Basic con el parámetro `language` de la directiva `template`. (Para obtener más información sobre la `template` directiva, consulte [directivas de plantilla de texto T4](../modeling/t4-text-template-directives.md).)  
  
     El lenguaje que usa en los bloques de control no tiene nada que ver con el lenguaje o el formato del texto que genera en una plantilla de texto. Puede generar C# usando el código Visual Basic o viceversa.  
  
     Solo puede usar un lenguaje en una plantilla de texto determinada, incluidas todas las plantillas de texto que incluya con la directiva `include`.  
  
-   **Variables locales.** Puesto que todo el código de los bloques de control estándar y de expresiones de una plantilla de texto se genera como un único método, debe asegurarse de que no existe ningún conflicto con los nombres de las variables locales. Si va a incluir otras plantillas de texto, debe asegurarse de que los nombres de variable sean únicos en todas las plantillas incluidas. Una manera de asegurarse de esto es agregar una cadena a cada nombre de variable local que identifique la plantilla de texto en la que se ha declarado.  
  
     También es una buena idea inicializar las variables locales en valores razonables al declararlas, especialmente cuando incluya varias plantillas de texto.  
  
-   **Anidamiento de bloques de control.** Los bloques de control no pueden anidarse dentro de otros bloques de control. Siempre debe finalizar un bloque de control determinado antes de abrir otro. Por ejemplo, a continuación se muestra cómo imprimir algún texto en un bloque de expresiones como parte de un bloque de control estándar.  
  
    ```  
    <#   
    int x = 10;  
    while (x-- > 0)  
    {  
    #>  
    <#= x #>  
    <# } #>  
    ```  
  
-   **La refactorización.** Para conseguir que las plantillas de texto sean breves y fáciles de entender, se recomienda evitar un código repetitivo factorizando el código reutilizable en funciones auxiliares en los bloques de características de clase, o bien creando su propia clase de plantilla de texto que herede de la clase Microsoft.VisualStudio.TextTemplating.TextTransformation.