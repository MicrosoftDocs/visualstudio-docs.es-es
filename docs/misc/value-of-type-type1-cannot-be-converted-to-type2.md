---
title: "Un valor de tipo &#39;&lt;tipo1&gt;&#39; no se puede convertir a &#39;&lt;tipo2&gt;&#39;. | Microsoft Docs"
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
  - "bc30311"
  - "vbc30311"
helpviewer_keywords: 
  - "BC30311"
ms.assetid: e3a513d4-2a1e-46d6-b592-b2e756b89d7d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Un valor de tipo &#39;&lt;tipo1&gt;&#39; no se puede convertir a &#39;&lt;tipo2&gt;&#39;.
Una instrucción intenta convertir un tipo de datos a otro de manera que no está definida. Las causas posibles de este error son las siguientes:  
  
-   Una conversión especifica dos tipos de datos entre los que no existe ninguna conversión. Un ejemplo de esto es una conversión de un valor `Boolean` al tipo `Date`.  
  
-   Una inicialización de una matriz no incluye llaves \(`{}`\) después de una cláusula `New`. En este caso, \<tipo2\> tiene el formato 'matriz unidimensional de \<tipo\>'.  
  
 **Identificador de error:** BC30311  
  
### Para corregir este error  
  
-   Asegúrese de que la expresión se puede convertir al tipo de datos de destino.  
  
-   Si \<tipo2\> es una matriz, asegúrese de que la cláusula `New` contiene paréntesis y llaves después del nombre de tipo. El código siguiente ilustra una inicialización correcta de una matriz.  
  
    ```  
    Dim anIntArray As Integer() = New Integer() {}  
    ```  
  
## Vea también  
 [Conversiones de tipos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)   
 [Cómo: Inicializar una variable de matriz en Visual Basic](../Topic/How%20to:%20Initialize%20an%20Array%20Variable%20in%20Visual%20Basic.md)