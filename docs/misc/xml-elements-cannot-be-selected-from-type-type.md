---
title: "No se pueden seleccionar elementos XML del tipo &#39;tipo&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36807"
  - "bc36807"
helpviewer_keywords: 
  - "BC36807"
ms.assetid: 01c19899-2b44-41e9-a99c-35edfa0deaf1
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se pueden seleccionar elementos XML del tipo &#39;tipo&#39;
Se ha hecho referencia a un elemento secundario XML para un objeto que no es de tipo <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XDocument> o `IEnumerable(Of XElement)`. Para obtener más información, consulte [Propiedades de eje secundario XML](/dotnet/visual-basic/language-reference/xml-axis/xml-child-axis-property).  
  
```vb#  
' Generates an error. Dim var = "sample text".<child>  
```  
  
 **Identificador de error:** BC36807  
  
### Para corregir este error  
  
-   Asegúrese de que el objeto del que hace referencia a un atributo está fuertemente tipado como <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XDocument> o `IEnumerable(Of XElement)`. A continuación se muestra un ejemplo:  
  
    ```vb#  
    Dim elem As XElement = <root> <child /> </root> Dim var = elem.<child>  
    ```  
  
## Vea también  
 [Propiedades de eje secundario XML](/dotnet/visual-basic/language-reference/xml-axis/xml-child-axis-property)   
 [Propiedades de eje XML](/dotnet/visual-basic/language-reference/xml-axis/xml-axis-properties)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)