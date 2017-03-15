---
title: "La primera instrucci&#243;n del cuerpo del m&#233;todo no puede estar en la misma l&#237;nea que la declaraci&#243;n del m&#233;todo. | Microsoft Docs"
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
  - "vbc30040"
  - "bc30040"
helpviewer_keywords: 
  - "BC30040"
ms.assetid: 27df3488-de77-499d-b9a6-08037d540cb0
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La primera instrucci&#243;n del cuerpo del m&#233;todo no puede estar en la misma l&#237;nea que la declaraci&#243;n del m&#233;todo.
Una instrucción `Function`, `Sub`, `Get`, `Set` o `Property` debe figurar aislada en una línea de código fuente.  
  
 **Identificador de error:** BC30040  
  
### Para corregir este error  
  
1.  Quite cualquier etiqueta de línea que preceda a la declaración de procedimiento.  
  
2.  Mueva cualquier instrucción que preceda a la declaración de procedimiento a una línea de código fuente anterior.  
  
3.  Mueva cualquier instrucción que siga a la declaración de procedimiento a una línea de código fuente posterior.  
  
## Vea también  
 [Procedimientos](/dotnet/visual-basic/programming-guide/language-features/procedures/index)   
 [Cómo: Aplicar etiquetas a las instrucciones](../Topic/How%20to:%20Label%20Statements%20\(Visual%20Basic\).md)