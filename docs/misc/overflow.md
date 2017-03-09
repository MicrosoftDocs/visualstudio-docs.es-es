---
title: "Overflow. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VB_E_OVERFLOW"
  - "vs.message.0x800A0097"
ms.assetid: 632387b9-be9c-4744-bcc5-842c45582347
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Overflow.
Una asignación de memoria superó las limitaciones del destino de la asignación.  Este error se debe normalmente a una de las siguientes causas:  
  
-   El resultado de una asignación, cálculo o conversión de tipo de datos es demasiado grande para representarlo dentro del intervalo de valores permitido para ese tipo de variable.  
  
-   Una asignación de una propiedad supera el valor máximo que la propiedad puede aceptar.  
  
-   Ha intentado usar un número en un cálculo y se ha forzado la conversión de este número en un entero, pero el resultado es mayor que un entero.  
  
### Para corregir este error  
  
1.  Asigne el valor a un tipo de variable que admita un intervalo de valores mayor.  
  
     \-O bien\-  
  
     Asegúrese de que la asignación se ajusta al intervalo de la propiedad para la que se ha creado.