---
title: "El miembro &#39;&lt;nombreDeMiembro1&gt;&#39; declara impl&#237;citamente &#39;&lt;nombreDeMiembroImpl&#237;cito&gt;&#39;, que entra en conflicto con un miembro de la clase base &#39;&lt;nombreDeClaseBase&gt;&#39; | Microsoft Docs"
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
  - "vbc40022"
  - "bc40022"
helpviewer_keywords: 
  - "BC40022"
ms.assetid: be5bb2ee-2274-42b2-b843-179b14127b34
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El miembro &#39;&lt;nombreDeMiembro1&gt;&#39; declara impl&#237;citamente &#39;&lt;nombreDeMiembroImpl&#237;cito&gt;&#39;, que entra en conflicto con un miembro de la clase base &#39;&lt;nombreDeClaseBase&gt;&#39;
El miembro '\<nombreDeMiembro1\>' declara implícitamente '\<nombreDeMiembroImplícito\>', que entra en conflicto con un miembro de la clase base '\<nombreDeClaseBase\>', por lo que el miembro no debe declararse 'Overloads'.  
  
 Un miembro de una clase derivada genera un miembro implícito con el mismo nombre que un miembro implícito de la clase y especifica la palabra clave [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads).  
  
 La sobrecarga se usa para definir varias versiones de una propiedad o un procedimiento en la misma clase. No se puede definir una versión adicional de un miembro de clase base a menos que ese miembro de clase base ya especifique `Overloads`. Dado que el miembro de la clase base en conflicto no especifica `Overloads`, el compilador supone que esta propiedad [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows) es el miembro de clase base implícito.  
  
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
  
 **Identificador de error:** BC40022  
  
### Para corregir este error  
  
-   Si quiere ocultar, o ensombrecer, el miembro de clase base, reemplace la palabra clave [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads) por la palabra clave [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows) en la declaración de la propiedad.  
  
-   Si no tiene previsto ensombrecer el miembro de clase base, cambie el nombre de la propiedad para evitar los conflictos de nombres que se describen en la tabla anterior.  
  
## Vea también  
 [Nombres de elementos declarados](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)