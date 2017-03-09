---
title: "La propiedad de atributo &#39;ReadOnly&#39; &#39;&lt;campoPropiedad&gt;&#39; no puede ser el destino de una asignaci&#243;n. | Microsoft Docs"
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
  - "bc31501"
  - "vbc31501"
helpviewer_keywords: 
  - "BC31501"
ms.assetid: 41c3f979-6b24-4595-9503-9c80a4d6d762
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La propiedad de atributo &#39;ReadOnly&#39; &#39;&lt;campoPropiedad&gt;&#39; no puede ser el destino de una asignaci&#243;n.
Se intentó asignar un valor a una propiedad `ReadOnly` en un atributo.  
  
 **Identificador de error:** BC31501  
  
### Para corregir este error  
  
1.  Elimine la instrucción de asignación de la propiedad.  
  
2.  Si usa propiedades que ha desarrollado, quite los modificadores `ReadOnly` o `Shared` de la propiedad del atributo.  
  
## Vea también  
 [Shared](/dotnet/visual-basic/language-reference/modifiers/shared)   
 [NO ESTÁ EN LA COMPILACIÓN: Atributos en Visual Basic](http://msdn.microsoft.com/es-es/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)