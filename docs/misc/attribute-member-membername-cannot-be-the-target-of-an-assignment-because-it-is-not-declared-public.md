---
title: "El miembro de atributo &#39;&lt;nombreDeMiembro&gt;&#39; no puede ser el destino de una asignaci&#243;n porque no est&#225; declarado &#39;Public&#39;. | Microsoft Docs"
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
  - "vbc31511"
  - "bc31511"
helpviewer_keywords: 
  - "BC31511"
ms.assetid: f8c958f6-58a4-4aff-b8c3-f2e9481e8132
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El miembro de atributo &#39;&lt;nombreDeMiembro&gt;&#39; no puede ser el destino de una asignaci&#243;n porque no est&#225; declarado &#39;Public&#39;.
Se intentó asignar un valor a un miembro privado de un atributo.  
  
 **Identificador de error:** BC31511  
  
### Para corregir este error  
  
1.  Quite la asignación.  
  
2.  Si usa atributos personalizados desarrollados por usted, cambie el modificador de acceso del miembro de atributo a `Public`.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Atributos en Visual Basic](http://msdn.microsoft.com/es-es/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)   
 [Public](/dotnet/visual-basic/language-reference/modifiers/public)