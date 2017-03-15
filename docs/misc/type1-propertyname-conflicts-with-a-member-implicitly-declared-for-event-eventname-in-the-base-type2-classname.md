---
title: "&lt;type1&gt; &#39;&lt;propertyname&gt;&#39; est&#225; en conflicto con un miembro declarado impl&#237;citamente para el evento &#39;&lt;eventname&gt;&#39; en la base &lt;type2&gt; &#39;&lt;classname&gt;&#39;. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40014"
  - "bc40014"
helpviewer_keywords: 
  - "BC40014"
ms.assetid: 100534b9-d533-4e94-a2a7-0ed26426965b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;type1&gt; &#39;&lt;propertyname&gt;&#39; est&#225; en conflicto con un miembro declarado impl&#237;citamente para el evento &#39;&lt;eventname&gt;&#39; en la base &lt;type2&gt; &#39;&lt;classname&gt;&#39;.
Se ha declarado una propiedad con el mismo nombre que un miembro implícito formado a partir de un evento en la clase base. Por ejemplo, si declara una propiedad denominada `Event1`, el compilador genera los procedimientos implícitos `add_Event1` y `remove_Event1`. Si la propiedad de esta clase tiene uno de estos nombres, debe controlar remotamente el miembro de clase base.  
  
 Este mensaje es una advertencia. Se supone `Shadows` de forma predeterminada. Para más información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC40014  
  
### Para corregir este error  
  
1.  Para ocultar el miembro de clase base, agregue la palabra clave `Shadows` a la declaración de propiedad.  
  
2.  Si no desea ocultar el miembro de clase base, cambie el nombre de la propiedad.  
  
## Vea también  
 [Property \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Event \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)   
 [Sombrear en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/shadowing)