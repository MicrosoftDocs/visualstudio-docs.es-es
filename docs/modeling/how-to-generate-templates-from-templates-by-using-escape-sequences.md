---
title: "How to: Generate Templates from Templates By Using Escape Sequences | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, generating templates from templates"
ms.assetid: 4126156a-7cea-48b8-925e-7790806cfe6c
caps.latest.revision: 35
caps.handback.revision: 35
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# How to: Generate Templates from Templates By Using Escape Sequences
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede crear una plantilla de texto que cree otra plantilla de texto como salida de texto generada.  Con este fin, debe utilizar secuencias de escape para delinear las etiquetas de plantilla de texto.  Si no utiliza secuencias de escape, la plantilla de texto generada tendrá un significado predefinido.  Para obtener más información sobre cómo utilizar secuencias de escape en las plantillas de texto, vea [Using Escape Sequences in Text Templates](../modeling/using-escape-sequences-in-text-templates.md).  
  
### Para generar una plantilla de texto desde otra plantilla de texto  
  
-   Utilice la barra diagonal inversa \(\\\) como carácter de escape para producir las etiquetas de marcado necesarias dentro de la plantilla de texto para las directivas, instrucciones, expresiones y características de clase en un archivo de plantilla de texto independiente.  
  
    ```  
    \<#@ directive \#>  
    \<# statement \#>  
    \<#= expression \#>  
    \<#+ classfeature \#>  
    ```  
  
## Ejemplo  
 En el siguiente ejemplo se utilizan caracteres de escape para producir una plantilla de texto a partir de otra plantilla de texto.  La directiva `output` establece el tipo de archivo de destino en el tipo de archivo de plantilla de texto \(.tt\).  
  
```c#  
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