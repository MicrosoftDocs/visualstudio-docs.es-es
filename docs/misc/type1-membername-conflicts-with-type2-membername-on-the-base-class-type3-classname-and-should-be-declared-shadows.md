---
title: "&lt;tipo1&gt; &#39;&lt;nombreMiembro&gt;&#39; est&#225; en conflicto con &lt;tipo2&gt; &#39;&lt;nombreMiembro&gt;&#39; en la clase base &lt;tipo3&gt; &#39;&lt;nombreClase&gt;&#39; y se debe declarar como &#39;Shadows&#39;. | Microsoft Docs"
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
  - "bc40004"
  - "vbc40004"
helpviewer_keywords: 
  - "BC40004"
ms.assetid: 24d10f31-3b3d-448c-b928-fc937e1f4a92
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;tipo1&gt; &#39;&lt;nombreMiembro&gt;&#39; est&#225; en conflicto con &lt;tipo2&gt; &#39;&lt;nombreMiembro&gt;&#39; en la clase base &lt;tipo3&gt; &#39;&lt;nombreClase&gt;&#39; y se debe declarar como &#39;Shadows&#39;.
Un elemento de programación se declara con el mismo nombre que un elemento definido en la clase base. En esta situación, el elemento de esta clase debe controlar remotamente el elemento de clase base.  
  
 Este mensaje es una advertencia. Se supone `Shadows` de forma predeterminada. Para más información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC40004  
  
### Para corregir este error  
  
-   Agregue la palabra clave `Shadows` a la declaración o cambie el nombre del elemento que se declara.  
  
## Vea también  
 [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)   
 [Sombrear en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/shadowing)