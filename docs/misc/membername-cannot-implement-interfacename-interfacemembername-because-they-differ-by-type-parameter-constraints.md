---
title: "&#39;&lt;nombreDeMiembro&gt;&#39; no puede implementar &#39;&lt;nombreDeInterfaz&gt;.&lt;nombreDeMiembroDeInterfaz&gt;&#39; porque difieren en las restricciones de par&#225;metro de tipo | Microsoft Docs"
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
  - "vbc32078"
  - "BC32078"
helpviewer_keywords: 
  - "BC32078"
ms.assetid: 2c971345-edb4-491e-9202-8eb8286b66f8
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nombreDeMiembro&gt;&#39; no puede implementar &#39;&lt;nombreDeInterfaz&gt;.&lt;nombreDeMiembroDeInterfaz&gt;&#39; porque difieren en las restricciones de par&#225;metro de tipo
Un evento, una propiedad o un procedimiento genérico intenta implementar un miembro similar definido en una interfaz, pero dichos miembros tienen distintas listas de restricciones en sus parámetros de tipo.  
  
 Para implementar un miembro de interfaz, el miembro que implementa debe coincidir no solo con la signatura completa del miembro de interfaz, sino también con el mecanismo de paso de cada parámetro.  
  
 Para implementar un miembro de interfaz genérica, el miembro que implementa debe coincidir además con el número de parámetros de tipo y la lista de restricciones de cada uno de ellos.  
  
 Para obtener información detallada sobre la implementación de interfaz, vea [NO ESTÁ EN LA COMPILACIÓN: Palabra clave Implements e instrucción Implements](http://msdn.microsoft.com/es-es/b96560f7-6413-480f-a1e2-f80253bab5be).  
  
 **Identificador de error:** BC32078  
  
### Para corregir este error  
  
-   Si tiene intención de implementar el miembro de interfaz, revise las restricciones de parámetro de tipo para comprobar que coinciden exactamente con los del miembro de interfaz.  
  
-   Si las restricciones de parámetro de tipo deben permanecer tal y como las tiene, no puede implementar el miembro de interfaz en esta declaración. Quite la palabra clave [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause) de la declaración.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [NO ESTÁ EN LA COMPILACIÓN: Ejemplos de implementación de interfaz en Visual Basic](http://msdn.microsoft.com/es-es/50bf2a30-73b6-4126-a921-075fd6eec278)