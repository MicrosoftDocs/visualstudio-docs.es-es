---
title: Filtrar Generar plantillas desde otras plantillas mediante secuencias de escape
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, generating templates from templates
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6c50fb897e3374eccca60f3fc05591bbf221670e
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55926039"
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>Filtrar Generar plantillas desde otras plantillas mediante secuencias de escape
Puede crear una plantilla de texto que se crea otra plantilla de texto como salida de texto generada. Para ello, debe usar las secuencias de escape para delinear las etiquetas de la plantilla de texto. Si no usa secuencias de escape, la plantilla de texto generada tendrá un significado definido previamente. Para obtener más información sobre el uso de secuencias de escape en plantillas de texto, consulte [utilizando las secuencias de Escape en plantillas de texto](../modeling/using-escape-sequences-in-text-templates.md).

### <a name="to-generate-a-text-template-from-within-a-text-template"></a>Para generar una plantilla de texto desde dentro de una plantilla de texto

-   Utilice la barra diagonal inversa (\\) como carácter de escape para producir las etiquetas de marcado necesario dentro de la plantilla de texto para las directivas, instrucciones, expresiones y funciones en un archivo de plantilla de texto independiente de la clase.

    ```
    \<#@ directive \#>
    \<# statement \#>
    \<#= expression \#>
    \<#+ classfeature \#>
    ```

## <a name="example"></a>Ejemplo
 El ejemplo siguiente utiliza caracteres de escape para generar una plantilla de texto desde una plantilla de texto. El `output` Directiva establece el tipo de archivo de destino en el tipo de archivo de plantilla de texto (.tt).

```csharp
\<#@ output extension=".tt" \#>
\<#@ assembly name="System.Xml.dll" \#>
\<#@ import namespace="System.Xml" \#>
\<#
XmlDocument xDoc = new XmlDocument();
//System.Diagnostics.Debugger.Break();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {\#>
           \<#= attr.Name \#>
       \<#}
     }
\#>
```

 La salida de texto generado es una plantilla de texto.

```
<#@ output extension=".tt" #>
<#@ assembly name="System.Xml.dll" #>
<#@ import namespace="System.Xml" #>
<#
XmlDocument xDoc = new XmlDocument();
//System.Diagnostics.Debugger.Break();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {#>
           <#= attr.Name #>
       <#}
     }
#>
```