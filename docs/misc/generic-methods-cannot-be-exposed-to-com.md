---
title: "Los m&#233;todos gen&#233;ricos no se pueden exponer a COM. | Microsoft Docs"
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
  - "vbc30943"
  - "bc30943"
helpviewer_keywords: 
  - "BC30943"
ms.assetid: 0e3bff62-f187-4864-8520-70f6be22e869
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los m&#233;todos gen&#233;ricos no se pueden exponer a COM.
Un componente [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que contiene uno o varios procedimientos genéricos se exporta a un componente COM.  
  
 El modelo de objetos componentes \(COM\) no admite tipos genéricos y no puede interoperar con ellos.  
  
 **Identificador de error:** BC30943  
  
### Para corregir este error  
  
-   Quite el procedimiento o los procedimientos genéricos desde el componente [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], o no lo use para la interoperabilidad COM.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Interoperabilidad COM](/dotnet/visual-basic/programming-guide/com-interop/index)