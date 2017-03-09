---
title: "Una variable no se puede inicializar con un tipo &#39;&lt;nombreElemento&gt;&#39; que no sea de matriz. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36536"
  - "bc36536"
helpviewer_keywords: 
  - "BC36536"
ms.assetid: 959415de-164e-4971-aab0-faad315753e9
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Una variable no se puede inicializar con un tipo &#39;&lt;nombreElemento&gt;&#39; que no sea de matriz.
Una variable que se declara como una matriz se debe inicializar con un valor de matriz.  
  
```  
' Not valid. ' The following line causes this error when executed with Option Strict off. ' Dim arrayVar1() = 10  
```  
  
 **Identificador de error:** BC36536  
  
### Para corregir este error  
  
-   Inicialice la variable de matriz con un valor de matriz:  
  
    ```  
    ' With Option Strict off. Dim arrayVar2() = {1, 2, 3} ' With Option Strict on. Dim arrayVar3() As Integer = {1, 2, 3}  
    ```  
  
## Vea también  
 [NOTINBUILD Una variable de matriz](http://msdn.microsoft.com/es-es/c2da78bd-6928-46ba-805f-44f819dfaf93)