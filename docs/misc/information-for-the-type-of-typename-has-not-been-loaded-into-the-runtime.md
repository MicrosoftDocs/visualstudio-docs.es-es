---
title: "No se carg&#243; la informaci&#243;n del tipo &#39;&lt;nombreTipo&gt;&#39; en el runtime. | Microsoft Docs"
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
  - "vbc30750"
  - "bc30750"
helpviewer_keywords: 
  - "BC30750"
ms.assetid: b0f074f9-571d-48f8-b334-4fd34b61cd89
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se carg&#243; la informaci&#243;n del tipo &#39;&lt;nombreTipo&gt;&#39; en el runtime.
Se hace referencia a un tipo que el runtime no ha cargado.  
  
 **Identificador de error:** BC30750  
  
### Para corregir este error  
  
1.  Reestructure el código para que el tipo esté definido en el ámbito actual.  
  
2.  Compruebe que el miembro está definido y que ha escrito correctamente el nombre del miembro.  
  
3.  Intente obtener acceso a uno de los miembros declarados en el módulo. En algunos casos, el entorno de depuración no encuentra los miembros porque los módulos donde se declaran no están cargados.  
  
## Vea también  
 [Depurar en Visual Studio](../debugger/debugging-in-visual-studio.md)