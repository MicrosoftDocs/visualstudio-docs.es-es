---
title: "Aqu&#237; no puede aparecer un literal XML a menos que se incluya entre par&#233;ntesis | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31198"
  - "vbc31198"
helpviewer_keywords: 
  - "BC31198"
ms.assetid: 97b16076-39ff-430a-9c65-073d01bcb08e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Aqu&#237; no puede aparecer un literal XML a menos que se incluya entre par&#233;ntesis
Una declaración de literal de XML se usa en una expresión de una ubicación que es ambigua para el compilador de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Es decir, el compilador de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] no puede determinar si el carácter menor que \(\<\) se usa como operador comparativo o para iniciar un literal XML. El siguiente fragmento de código muestra un ejemplo:  
  
 \[Visual Basic\]  
  
```  
' Generates an error. Dim queryResult = From element In elements _ Where <sample>Value</sample> = "Value" _ Select element  
```  
  
 **Identificador de error:** BC31198  
  
### Para corregir este error  
  
-   Incluya la declaración de literal XML entre paréntesis, tal como se muestra en el ejemplo siguiente:  
  
    ```vb#  
    Dim queryResult = From element In elements _ Where (<sample> Value</sample>) = "Value" _ Select element  
    ```  
  
-   Modifique el código para hacer referencia a un literal XML existente, tal como se muestra en el ejemplo siguiente:  
  
    ```vb#  
    Dim queryResult = From element In elements _ Where e.<sample>.Value = "Value" _ Select element  
    ```  
  
## Vea también  
 [Literales XML](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [Propiedades de eje XML](/dotnet/visual-basic/language-reference/xml-axis/xml-axis-properties)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)