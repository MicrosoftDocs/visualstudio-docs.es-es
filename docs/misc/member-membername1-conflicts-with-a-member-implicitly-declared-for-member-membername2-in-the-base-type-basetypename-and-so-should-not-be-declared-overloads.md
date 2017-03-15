---
title: "El miembro &#39;&lt;nombreDeMiembro1&gt;&#39; entra en conflicto con un miembro declarado impl&#237;citamente para el miembro &#39;&lt;nombreDeMiembro2&gt;&#39; en el tipo base &#39;&lt;nombreDeTipoBase&gt;&#39; y, por lo tanto, no debe declararse &#39;Overloads&#39; | Microsoft Docs"
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
  - "vbc40023"
  - "bc40023"
helpviewer_keywords: 
  - "BC40023"
ms.assetid: 82bb29a6-8d49-47a4-8c19-b21e97dfc7de
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El miembro &#39;&lt;nombreDeMiembro1&gt;&#39; entra en conflicto con un miembro declarado impl&#237;citamente para el miembro &#39;&lt;nombreDeMiembro2&gt;&#39; en el tipo base &#39;&lt;nombreDeTipoBase&gt;&#39; y, por lo tanto, no debe declararse &#39;Overloads&#39;
Una propiedad o un procedimiento en una clase derivada usa el mismo nombre que un miembro implícito de la clase base y especifica la palabra clave [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads).  
  
 La sobrecarga se usa para definir varias versiones de una propiedad o un procedimiento en la misma clase. No se puede definir una versión adicional de un miembro de clase base a menos que ese miembro de clase base ya especifique `Overloads`. Dado que los miembros implícitos no especifican `Overloads`, el compilador supone que esta propiedad o este procedimiento [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows) es el miembro de clase base implícito.  
  
 El compilador de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] crea miembros implícitos que corresponden a determinados elementos de programación que el usuario declara. En la tabla siguiente se resumen estos miembros implícitos o *sintéticos*.  
  
|Elemento declarado|Miembros creados implícitamente|  
|------------------------|-------------------------------------|  
|Enumeración|Miembro `value__`|  
|Evento|Procedimiento `add_<eventname>`<br /><br /> Procedimiento `remove_<eventname>`<br /><br /> Campo de `<eventname>Event`<br /><br /> Delegado `<eventname>EventHandler`|  
|Propiedad|Procedimiento `get_<propertyname>`<br /><br /> Procedimiento `set_<propertyname>`|  
|Miembro `My.Form`, miembro `My.WebService` o miembro de una clase marcada con el atributo <xref:Microsoft.VisualBasic.MyGroupCollectionAttribute>|Variable `m_<variablename>` `Static`<br /><br /> Propiedad `<variablename>`<br /><br /> Procedimiento `get_<variablename>`<br /><br /> Procedimiento `set_<variablename>`|  
|Variable `WithEvents`|Variable `_<variablename>`<br /><br /> Propiedad `<variablename>`<br /><br /> Procedimiento `get_<variablename>`<br /><br /> Procedimiento `set_<variablename>`|  
  
 Debido al riesgo de conflictos de nombres, debe evitar asignar un nombre a cualquier elemento de programación declarado con el mismo formato que cualquiera de estos miembros implícitos. Por ejemplo, debe evitar los nombres de elementos que empiecen por `get_` o `set_`.  
  
 De forma predeterminada, este mensaje es una advertencia. Para más información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC40023  
  
### Para corregir este error  
  
-   Cambie el nombre de la propiedad o el procedimiento para evitar conflictos con los nombres que aparecen en la tabla anterior.  
  
## Vea también  
 [Nombres de elementos declarados](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)