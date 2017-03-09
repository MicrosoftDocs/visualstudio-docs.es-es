---
title: "El evento &#39;&lt;eventname1&gt;&#39; no puede implementar el evento &#39;&lt;eventname2&gt;&#39; porque su tipo delegado no coincide con el tipo delegado de otro evento implementado por &#39;&lt;eventname1&gt;&#39;. | Microsoft Docs"
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
  - "bc31407"
  - "vbc31407"
helpviewer_keywords: 
  - "BC31407"
ms.assetid: 0b9ffddb-4759-438b-b569-beac7062e986
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El evento &#39;&lt;eventname1&gt;&#39; no puede implementar el evento &#39;&lt;eventname2&gt;&#39; porque su tipo delegado no coincide con el tipo delegado de otro evento implementado por &#39;&lt;eventname1&gt;&#39;.
[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] no puede implementar un evento porque su tipo delegado no coincide con el tipo delegado de otro evento. Este error puede producirse cuando define varios eventos en una interfaz e intenta implementarlos juntos con el mismo evento. Un evento puede implementar dos o más eventos solo si todos los eventos implementados se declaran con la sintaxis `As` y si se especifica el mismo tipo delegado.  
  
 **Identificador de error:** BC31407  
  
### Para corregir este error  
  
-   Implemente los eventos por separado.  
  
## Vea también  
 [Eventos](/dotnet/visual-basic/programming-guide/language-features/events/events)