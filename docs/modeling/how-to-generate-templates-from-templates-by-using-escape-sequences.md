---
title: "Cómo: generar plantillas desde plantillas mediante secuencias de Escape | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: text templates, generating templates from templates
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7d8aeee2588d0f86708bf76f3630fa0d9ecd5bd1
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2018
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>Cómo: Generar plantillas desde otras plantillas mediante secuencias de escape
Puede crear una plantilla de texto que se crea otra plantilla de texto como salida de texto generada. Para ello, debe utilizar secuencias de escape para delinear las etiquetas de plantilla de texto. Si no utiliza secuencias de escape, la plantilla de texto generada tendrá un significado predefinido. Para obtener más información sobre el uso de secuencias de escape en las plantillas de texto, consulte [utilizando las secuencias de Escape en las plantillas de texto](../modeling/using-escape-sequences-in-text-templates.md).  
  
### <a name="to-generate-a-text-template-from-within-a-text-template"></a>Para generar una plantilla de texto desde una plantilla de texto  
  
-   Utilice la barra diagonal inversa (\\) como carácter de escape para generar las etiquetas de marcado necesarias dentro de la plantilla de texto para las directivas, instrucciones, expresiones y características en un archivo de plantilla de texto independiente de clase.  
  
    ```  
    \<#@ directive \#>  
    \<# statement \#>  
    \<#= expression \#>  
    \<#+ classfeature \#>  
    ```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se usa caracteres de escape para generar una plantilla de texto desde una plantilla de texto. El `output` Directiva establece el tipo de archivo de destino para el tipo de archivo de plantilla de texto (TT).  
  
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