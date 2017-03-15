---
title: "El miembro &#39;&lt;membername&gt;&#39; define impl&#237;citamente un miembro &#39;&lt;implicitmembername&gt;&#39; que tiene el mismo nombre que un par&#225;metro de tipo | Microsoft Docs"
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
  - "BC32070"
  - "vbc32070"
helpviewer_keywords: 
  - "BC32070"
ms.assetid: cc0b3fcf-c141-47e2-9b33-d2b91c8bf2d6
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El miembro &#39;&lt;membername&gt;&#39; define impl&#237;citamente un miembro &#39;&lt;implicitmembername&gt;&#39; que tiene el mismo nombre que un par&#225;metro de tipo
Un miembro de una clase genérica genera un miembro implícito con el mismo nombre que un parámetro de tipo para la clase.  
  
 El compilador [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] crea miembros implícitos que corresponden a determinados elementos de programación que declara. En la tabla siguiente se resumen estos miembros implícitos o *sintéticos*.  
  
|Elemento declarado|Miembros creados implícitamente|  
|------------------------|-------------------------------------|  
|Enumeración|Miembro `value__`|  
|Evento|Procedimiento `add_<eventname>`<br /><br /> Procedimiento `remove_<eventname>`<br /><br /> Campo de `<eventname>Event`<br /><br /> Delegado `<eventname>EventHandler`|  
|Propiedad|Procedimiento `get_<propertyname>`<br /><br /> Procedimiento `set_<propertyname>`|  
|Variable de colección `My.`|Variable `m_<variablename>` `Static`<br /><br /> Propiedad `<variablename>`<br /><br /> Procedimiento `get_<variablename>`<br /><br /> Procedimiento `set_<variablename>`|  
|Variable `WithEvents`|Variable `_<variablename>`<br /><br /> Propiedad `<variablename>`<br /><br /> Procedimiento `get_<variablename>`<br /><br /> Procedimiento `set_<variablename>`|  
  
 Debido a la posibilidad de conflictos de nombres, debe evitar asignar un nombre de cualquier elemento de programación declarado con el mismo formato que cualquiera de estos miembros implícitos. Por ejemplo, debe evitar los nombres de elementos que comiencen por `get_` o `set_`.  
  
 **Id. de error:** BC32070  
  
### Para corregir este error  
  
-   Si el nombre del parámetro de tipo es flexible, cámbielo para evitar conflictos con los nombres que aparecen en la tabla anterior.  
  
-   Si el parámetro de tipo debe retener su nombre, cambie el nombre del miembro de clase para evitar conflictos con los nombres que aparecen en la tabla anterior.  
  
## Vea también  
 [Nombres de elementos declarados](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)   
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)