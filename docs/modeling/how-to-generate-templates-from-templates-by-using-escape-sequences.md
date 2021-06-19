---
title: Generación de una plantilla de texto a partir de una plantilla de texto
description: Proporciona información sobre cómo generar una plantilla de texto a partir de otra plantilla de texto mediante secuencias de escape.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, generating templates from templates
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 9347e32a72e7f590f8f513c4b47a4b7aae699f27
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387182"
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>Cómo: Generar plantillas desde otras plantillas mediante secuencias de escape
Puede crear una plantilla de texto que cree otra plantilla de texto como salida de texto generada. Para ello, debe usar secuencias de escape para delinear las etiquetas de plantilla de texto. Si no usa secuencias de escape, la plantilla de texto generada tendrá un significado predefinido. Para obtener más información sobre el uso de secuencias de escape en plantillas de texto, vea [Usar secuencias de escape en plantillas de texto.](../modeling/using-escape-sequences-in-text-templates.md)

### <a name="to-generate-a-text-template-from-within-a-text-template"></a>Para generar una plantilla de texto desde una plantilla de texto

- Use la barra diagonal inversa ( ) como carácter de escape para generar las etiquetas de marcado necesarias dentro de la plantilla de texto para directivas, instrucciones, expresiones y características de clase en un archivo de plantilla de texto \\ independiente.

    ```
    \<#@ directive \#>
    \<# statement \#>
    \<#= expression \#>
    \<#+ classfeature \#>
    ```

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se usan caracteres de escape para generar una plantilla de texto a partir de una plantilla de texto. La directiva establece el tipo de archivo de destino en el tipo de archivo de `output` plantilla de texto (.tt).

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
