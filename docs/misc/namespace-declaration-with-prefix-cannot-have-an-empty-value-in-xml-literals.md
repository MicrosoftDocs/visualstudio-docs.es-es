---
title: "Una declaraci&#243;n de espacio de nombres con prefijo no puede tener un valor vac&#237;o en literales XML | Microsoft Docs"
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
  - "bc31184"
  - "vbc31184"
helpviewer_keywords: 
  - "BC31184"
ms.assetid: dde656b4-df3b-4a2e-8871-4e14832ca778
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Una declaraci&#243;n de espacio de nombres con prefijo no puede tener un valor vac&#237;o en literales XML
Una declaración de espacio de nombres XML en un literal XML no incluye un valor de espacio de nombres. Por ejemplo, el código siguiente provocará este error:  
  
```vb#  
Dim book = <book xmlns:ns=""/>  
```  
  
 **Identificador de error:** BC31184  
  
### Para corregir este error  
  
-   Incluya un espacio de nombres válido en la declaración de espacio de nombres XML, o bien quite la declaración de espacio de nombres XML del literal XML.  
  
     Como alternativa, puede usar la instrucción `Imports` para identificar un prefijo de espacio de nombres para el espacio de nombres vacío. Por ejemplo:  
  
    ```vb#  
    Imports <xmlns:ns="">  
    ```  
  
## Vea también  
 [Literales XML](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)   
 [Imports \(Instrucción, Espacio de nombres XML\)](/dotnet/visual-basic/language-reference/statements/imports-statement-xml-namespace)