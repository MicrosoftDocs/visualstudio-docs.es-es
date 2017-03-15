---
title: "El miembro &#39;&lt;nombreMiembro1&gt;&#39; declara impl&#237;citamente &#39;&lt;nombreMiembroImpl&#237;cito&gt;&#39;, que entra en conflicto con un miembro declarado impl&#237;citamente para el miembro &#39;&lt;nombreMiembro2&gt;&#39; en la clase base &#39;&lt;nombreClaseBase&gt;&#39;. | Microsoft Docs"
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
  - "vbc40018"
  - "bc40018"
helpviewer_keywords: 
  - "BC40018"
ms.assetid: 43844e55-9ce1-4b88-9aa8-839b37f30e5a
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El miembro &#39;&lt;nombreMiembro1&gt;&#39; declara impl&#237;citamente &#39;&lt;nombreMiembroImpl&#237;cito&gt;&#39;, que entra en conflicto con un miembro declarado impl&#237;citamente para el miembro &#39;&lt;nombreMiembro2&gt;&#39; en la clase base &#39;&lt;nombreClaseBase&gt;&#39;.
El miembro '\<nombreMiembro1\>' declara implícitamente '\<nombreMiembroImplícito\>', que entra en conflicto con un miembro declarado implícitamente para el miembro '\<nombreMiembro2\>' en la clase base '\<nombreClaseBase\>'. Por lo que el miembro debe declararse como 'Shadows'.  
  
 Un miembro de una clase derivada genera un miembro implícito con el mismo nombre que un miembro implícito para la clase. Dado que los miembros implícitos no especifican [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads), el compilador supone que este miembro aplica [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows) en el miembro de clase base implícito. El código es más legible y menos propenso al error, si se especifica explícitamente la palabra clave `Shadows` para este miembro.  
  
 El compilador [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] crea miembros implícitos que corresponden a determinados elementos de programación que declara. En la tabla siguiente se resumen estos miembros implícitos o *sintéticos*.  
  
|Elemento declarado|Miembros creados implícitamente|  
|------------------------|-------------------------------------|  
|Enumeración|Miembro `value__`|  
|Evento|Procedimiento `add_<eventname>`<br /><br /> Procedimiento `remove_<eventname>`<br /><br /> Campo de `<eventname>Event`<br /><br /> Delegado `<eventname>EventHandler`|  
|Propiedad|Procedimiento `get_<propertyname>`<br /><br /> Procedimiento `set_<propertyname>`|  
|Miembro `My.Form`, miembro `My.WebService` o miembro de una clase marcada con el atributo <xref:Microsoft.VisualBasic.MyGroupCollectionAttribute>|Variable `m_<variablename>` `Static`<br /><br /> Propiedad `<variablename>`<br /><br /> Procedimiento `get_<variablename>`<br /><br /> Procedimiento `set_<variablename>`|  
|Variable `WithEvents`|Variable `_<variablename>`<br /><br /> Propiedad `<variablename>`<br /><br /> Procedimiento `get_<variablename>`<br /><br /> Procedimiento `set_<variablename>`|  
  
 Debido al riesgo de conflictos de nombres, debe evitar asignar un nombre a cualquier elemento de programación declarado con el mismo formato que uno de estos miembros implícitos. Por ejemplo, debe evitar los nombres de elementos que empiecen por `get_` o `set_`.  
  
 De forma predeterminada, este mensaje es una advertencia. Para más información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC40018  
  
### Para corregir este error  
  
-   Si quiere ocultar, o reemplazar, el miembro de clase base implícito, incluya la palabra clave [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows) en la declaración del miembro de clase derivada.  
  
-   Si no desea reemplazar el miembro de clase base implícito, cambie el nombre del miembro de clase derivada para evitar conflictos con nombres que aparecen en la tabla anterior.  
  
## Vea también  
 [Nombres de elementos declarados](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)