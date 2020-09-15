---
title: Generar una plantilla de texto a partir de una plantilla de texto
description: Proporciona información sobre cómo generar una plantilla de texto a partir de otra plantilla de texto mediante secuencias de escape.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, generating templates from templates
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: d7ef983525842023247433e7a3c2b51e206a1cee
ms.sourcegitcommit: a18c7e9b367c2f92f6e54c3eaef442775d457667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/15/2020
ms.locfileid: "90100766"
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>Cómo: Generar plantillas desde otras plantillas mediante secuencias de escape
Puede crear una plantilla de texto que cree otra plantilla de texto como salida de texto generada. Para ello, debe usar secuencias de escape para delimitar las etiquetas de la plantilla de texto. Si no usa secuencias de escape, la plantilla de texto generada tendrá un significado predefinido. Para obtener más información sobre el uso de secuencias de escape en las plantillas de texto, vea [usar secuencias de escape en las plantillas de texto](../modeling/using-escape-sequences-in-text-templates.md).

### <a name="to-generate-a-text-template-from-within-a-text-template"></a>Para generar una plantilla de texto desde una plantilla de texto

- Use la barra diagonal inversa ( \\ ) como carácter de escape para generar las etiquetas de marcado necesarias dentro de la plantilla de texto para las directivas, instrucciones, expresiones y características de clase en un archivo de plantilla de texto independiente.

    ```
    \<#@ directive \#>
    \<# statement \#>
    \<#= expression \#>
    \<#+ classfeature \#>
    ```

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se utilizan caracteres de escape para generar una plantilla de texto a partir de una plantilla de texto. La `output` Directiva establece el tipo de archivo de destino en el tipo de archivo de plantilla de texto (. TT).

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

 La salida de texto generada es una plantilla de texto.

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
