---
title: "El evento &#39;&lt;nombreDeEvento&gt;&#39; declara impl&#237;citamente &#39;&lt;nombreDeMiembro&gt;&#39;, que entra en conflicto con un miembro de la base de &lt;tipo&gt; &#39;&lt;nombreDeClase&gt;&#39; y, por lo tanto, el evento se debe declarar como &#39;Shadows&#39; | Microsoft Docs"
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
  - "bc40012"
  - "vbc40012"
helpviewer_keywords: 
  - "BC40012"
ms.assetid: 5f14e8bd-a227-4115-af99-cd2b6fe4dc0e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El evento &#39;&lt;nombreDeEvento&gt;&#39; declara impl&#237;citamente &#39;&lt;nombreDeMiembro&gt;&#39;, que entra en conflicto con un miembro de la base de &lt;tipo&gt; &#39;&lt;nombreDeClase&gt;&#39; y, por lo tanto, el evento se debe declarar como &#39;Shadows&#39;
Un evento está declarado con un nombre que se combina para formar un miembro implícito con el mismo nombre que un miembro de la clase base. Por ejemplo, si se declara un evento denominado `Event1`, el compilador genera los procedimientos implícitos `add_Event1` y `remove_Event1`. Si la clase base tiene un miembro con uno de estos nombres, el evento de esta clase debe ocultar el miembro de la clase base.  
  
 Este mensaje es una advertencia. De forma predeterminada, se da por supuesto que es `Shadows`. Para más información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC40012  
  
### Para corregir este error  
  
1.  Para ocultar el miembro de la clase base, agregue la palabra clave `Shadows` a la declaración de evento.  
  
2.  Si no quiere ocultar el miembro de la clase base, cambie el nombre del evento.  
  
## Vea también  
 [Event \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)   
 [Sombrear en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/shadowing)