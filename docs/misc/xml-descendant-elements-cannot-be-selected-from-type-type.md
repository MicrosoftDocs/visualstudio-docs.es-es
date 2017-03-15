---
title: "No se pueden seleccionar elementos descendientes XML del tipo &#39;tipo&#39;. | Microsoft Docs"
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
  - "vbc36809"
  - "bc36809"
helpviewer_keywords: 
  - "BC36809"
ms.assetid: 560a3370-f24d-4ca3-93b1-39aabe13c238
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se pueden seleccionar elementos descendientes XML del tipo &#39;tipo&#39;.
Se ha hecho referencia a un descendiente XML para un objeto que no es de tipo <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XDocument> o `IEnumerable(Of XElement)`. Para obtener más información, consulta [Propiedad de eje descendiente XML](/dotnet/visual-basic/language-reference/xml-axis/xml-descendant-axis-property).  
  
```vb#  
' Generates an error. Dim var = "sample text"...<childElement>  
```  
  
 **Identificador de error:** BC36809  
  
### Para corregir este error  
  
-   Asegúrese de que el objeto del que hace referencia a un elemento descendiente tiene un tipo seguro como <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XDocument> o `IEnumerable(Of XElement)`. A continuación se muestra un ejemplo:  
  
    ```vb#  
    Dim elem As XElement = <root> <child /> </root> Dim var = elem...<child>  
    ```  
  
## Vea también  
 [Propiedad de eje descendiente XML](/dotnet/visual-basic/language-reference/xml-axis/xml-descendant-axis-property)   
 [Propiedades de eje XML](/dotnet/visual-basic/language-reference/xml-axis/xml-axis-properties)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)