---
title: "&#39;&lt;nombreDeProcedimiento&gt;&#39; no puede reemplazar a &#39;&lt;nombreDeProcedimientoBase&gt;&#39; porque difieren en las restricciones de par&#225;metro de tipo | Microsoft Docs"
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
  - "BC32077"
  - "vbc32077"
helpviewer_keywords: 
  - "BC32077"
ms.assetid: 9be1a88d-c1a4-4f12-8e72-74abb2be565d
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nombreDeProcedimiento&gt;&#39; no puede reemplazar a &#39;&lt;nombreDeProcedimientoBase&gt;&#39; porque difieren en las restricciones de par&#225;metro de tipo
Un procedimiento genérico intenta reemplazar un procedimiento de clase base genérica, pero tienen distintas listas de restricciones en sus parámetros de tipo.  
  
 Para reemplazar un procedimiento de clase base, el procedimiento de reemplazo debe coincidir no solo con la signatura completa del procedimiento de clase base, sino también con el nivel de acceso del procedimiento y el mecanismo de paso de cada parámetro.  
  
 Para reemplazar un procedimiento de clase base genérica, el procedimiento de reemplazo debe coincidir además con el número de parámetros de tipo y la lista de restricciones de cada uno de ellos.  
  
 Para obtener más información sobre los requisitos de reemplazo, vea [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides).  
  
 **Identificador de error:** BC32077  
  
### Para corregir este error  
  
-   Si piensa reemplazar el procedimiento de clase base, revise las restricciones de parámetros de tipo para que coincidan exactamente con las del procedimiento de clase base.  
  
-   Si las restricciones de parámetros de tipo deben permanecer tal como están, no se puede reemplazar el procedimiento de clase base. Quite la palabra clave `Overrides` de la declaración.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)