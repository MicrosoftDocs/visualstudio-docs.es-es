---
title: "&#39;&lt;miembro&gt;&#39; entra en conflicto con el miembro reservado por este nombre que est&#225; declarado impl&#237;citamente en todas las enumeraciones | Microsoft Docs"
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
  - "bc31420"
  - "vbc31420"
helpviewer_keywords: 
  - "BC31420"
ms.assetid: f2ea5a8b-f63c-4c93-bfac-418ae5a150a5
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;miembro&gt;&#39; entra en conflicto con el miembro reservado por este nombre que est&#225; declarado impl&#237;citamente en todas las enumeraciones
El nombre de un miembro de tipo está en conflicto con el nombre de un miembro declarado implícitamente en todas las enumeraciones.  
  
 El compilador de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] crea miembros implícitos que corresponden a determinados elementos de programación que el usuario declara. Las enumeraciones declaran implícitamente el miembro `value__member`.  
  
 **Identificador de error:** BC31420  
  
### Para corregir este error  
  
-   Modifique el nombre del miembro.  
  
## Vea también  
 [No está en la compilación: Instrucciones de declaración en Visual Basic](http://msdn.microsoft.com/es-es/81f3c398-f45c-4d95-80bf-aa39d1a0fb30)   
 [Información general sobre las enumeraciones](/dotnet/visual-basic/programming-guide/language-features/constants-enums/enumerations-overview)   
 [Nombres de elementos declarados](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)