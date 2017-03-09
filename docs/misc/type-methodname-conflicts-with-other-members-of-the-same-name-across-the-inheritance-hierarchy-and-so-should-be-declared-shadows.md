---
title: "El tipo &#39;&lt;nombreDeM&#233;todo&gt;&#39; est&#225; en conflicto con otros miembros del mismo nombre en la jerarqu&#237;a de herencia y, por lo tanto, se debe declarar como &#39;Shadows&#39; | Microsoft Docs"
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
  - "vbc42000"
  - "bc42000"
helpviewer_keywords: 
  - "BC42000"
ms.assetid: 3081635f-99a9-4e90-997f-82251144d80f
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El tipo &#39;&lt;nombreDeM&#233;todo&gt;&#39; est&#225; en conflicto con otros miembros del mismo nombre en la jerarqu&#237;a de herencia y, por lo tanto, se debe declarar como &#39;Shadows&#39;
Una interfaz que hereda de dos o más interfaces define un procedimiento con el mismo nombre que otro procedimiento ya definido en más de una de las interfaces base. El procedimiento de esta interfaz debe ocultar uno de los procedimientos de la interfaz base.  
  
 Este mensaje es una advertencia. De forma predeterminada, se da por supuesto que es `Shadows`. Para obtener más información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC42000  
  
### Para corregir este error  
  
-   Si quiere ocultar uno de los procedimientos de la interfaz base, agregue la palabra clave `Shadows` a la declaración del nuevo procedimiento.  
  
-   Si no quiere ocultar los procedimientos de la interfaz base, cambie el nombre del nuevo procedimiento.  
  
## Vea también  
 [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)   
 [Sombrear en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/shadowing)