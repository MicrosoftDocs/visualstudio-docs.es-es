---
title: "Una declaraci&#243;n de espacio de nombres debe comenzar por &#39;xmlns&#39; | Microsoft Docs"
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
  - "bc31187"
  - "vbc31187"
helpviewer_keywords: 
  - "BC31187"
ms.assetid: 64c6a033-7cdc-48a0-bff0-bdd045cb13ad
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Una declaraci&#243;n de espacio de nombres debe comenzar por &#39;xmlns&#39;
Se ha especificado un espacio de nombres XML sin el identificador `xmlns` necesario. El identificador `xmlns` debe contener únicamente caracteres en minúsculas.  
  
 **Id. de error:** BC31187  
  
### Para corregir este error  
  
-   Utilice el identificador `xmlns` cuando declare un espacio de nombres XML. A continuación se muestra un ejemplo:  
  
    ```vb#  
    Imports <xmlns:ns="http://SampleNamespace">  
    ```  
  
## Vea también  
 [Imports \(Instrucción, Espacio de nombres XML\)](/dotnet/visual-basic/language-reference/statements/imports-statement-xml-namespace)   
 [Literales XML](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)