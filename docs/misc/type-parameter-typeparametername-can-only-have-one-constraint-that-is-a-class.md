---
title: "El par&#225;metro de tipo &#39;&lt;typeparametername&gt;&#39; &#250;nicamente puede tener una restricci&#243;n que sea una clase. | Microsoft Docs"
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
  - "bc32047"
  - "vbc32047"
helpviewer_keywords: 
  - "BC32047"
ms.assetid: ac7ab76b-5300-4c79-b519-5a1287ed5fa9
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El par&#225;metro de tipo &#39;&lt;typeparametername&gt;&#39; &#250;nicamente puede tener una restricci&#243;n que sea una clase.
Una lista de restricciones incluye más de una clase.  
  
 Una lista de restricciones en un parámetro de tipo puede aceptar cualquier número de interfaces pero a lo sumo una clase. Un argumento de tipo proporcionado para ese parámetro de tipo debe heredar de esa clase, y [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] no admite la herencia múltiple.  
  
 **Identificador de error:** BC32047  
  
### Para corregir este error  
  
-   Seleccione una clase e incluya solo esta clase en la lista de restricciones.  
  
-   Puede definir parámetros de tipo adicionales para alojar la clase o clases que no se incluyen en esta lista de restricciones.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)