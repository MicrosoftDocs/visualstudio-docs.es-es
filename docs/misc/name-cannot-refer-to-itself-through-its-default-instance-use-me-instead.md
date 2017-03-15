---
title: "&#39;&lt;nombre&gt;&#39; no puede hacerse referencia a s&#237; mismo a trav&#233;s de su instancia predeterminada, use &#39;Me&#39; en su lugar. | Microsoft Docs"
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
  - "vbc31139"
  - "bc31139"
helpviewer_keywords: 
  - "BC31139"
ms.assetid: 459e5d5a-d526-4cd0-934e-96e4e1eb51bb
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nombre&gt;&#39; no puede hacerse referencia a s&#237; mismo a trav&#233;s de su instancia predeterminada, use &#39;Me&#39; en su lugar.
Se ha intentado hacer referencia desde dentro de un formulario a ese formulario, como una instancia predeterminada. Esto puede provocar que el formulario se llame a sí mismo recursivamente.  
  
 En la mayoría de los casos, debe usar `Me` al hacer referencia a la instancia actual del formulario, en lugar de usar la instancia predeterminada.  
  
 **Identificador de error:** BC31139  
  
### Para corregir este error  
  
-   Use `Me` para hacer referencia al objeto.  
  
## Vea también  
 [Conceptos básicos del depurador](../debugger/debugger-basics.md)