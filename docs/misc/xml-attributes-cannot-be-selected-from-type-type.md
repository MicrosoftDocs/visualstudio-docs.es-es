---
title: "No se pueden seleccionar atributos XML del tipo &#39;tipo&#39;. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36808"
  - "vbc36808"
helpviewer_keywords: 
  - "BC36808"
ms.assetid: 76b2605c-3d9b-4e56-ba3f-99c60c668290
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se pueden seleccionar atributos XML del tipo &#39;tipo&#39;.
Se ha hecho referencia a un atributo XML para un objeto que no es de tipo <xref:System.Xml.Linq.XElement> o `IEnumerable(Of XElement)`. Para obtener más información, consulta [Propiedad Axis para atributo XML](/dotnet/visual-basic/language-reference/xml-axis/xml-attribute-axis-property).  
  
```vb#  
' Generates an error. Dim var = "sample text".@attr  
```  
  
 **Identificador de error:** BC36808  
  
### Para corregir este error  
  
-   Asegúrese de que el objeto del que hace referencia a un atributo tiene un tipo seguro como <xref:System.Xml.Linq.XElement> o `IEnumerable(Of XElement)`. A continuación se muestra un ejemplo:  
  
    ```vb#  
    Dim elem As XElement = <root attr="value"/> Dim var = elem.@attr  
    ```  
  
## Vea también  
 [Propiedad Axis para atributo XML](/dotnet/visual-basic/language-reference/xml-axis/xml-attribute-axis-property)   
 [Propiedades de eje XML](/dotnet/visual-basic/language-reference/xml-axis/xml-axis-properties)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)