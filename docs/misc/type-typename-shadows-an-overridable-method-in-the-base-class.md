---
title: "&lt;tipo&gt; &#39;&lt;nombreDeTipo&gt;&#39; ensombrece un m&#233;todo reemplazable en la clase base | Microsoft Docs"
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
  - "vbc40005"
  - "bc40005"
helpviewer_keywords: 
  - "BC40005"
ms.assetid: 1dadda7f-1d26-4ae8-a668-9f69d55ceb50
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;tipo&gt; &#39;&lt;nombreDeTipo&gt;&#39; ensombrece un m&#233;todo reemplazable en la clase base
\<tipo\> '\<nombreDeTipo\>' ensombrece un método reemplazable en la clase base. Si quiere sobrecargar el método base, este método se debe declarar 'Overrides'.  
  
 Un elemento de programación se declara con el mismo nombre que un procedimiento o una propiedad definido en la clase base. En esta situación, el elemento de esta clase debe ensombrecer el elemento de clase base.  
  
 De forma predeterminada, este mensaje es una advertencia. Para más información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC40005  
  
### Para corregir este error  
  
-   Si tiene previsto reemplazar el procedimiento base, agregue la palabra clave `Overrides` a la declaración.  
  
-   Si tiene previsto ensombrecer el procedimiento base, agregue la palabra clave `Shadows` a la declaración.  
  
-   Si no desea realizar un reemplazo ni un sombreado, cambie el nombre del elemento que se está declarando.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Reemplazar propiedades y métodos](http://msdn.microsoft.com/es-es/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [Sombrear en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/shadowing)   
 [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides)   
 [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)