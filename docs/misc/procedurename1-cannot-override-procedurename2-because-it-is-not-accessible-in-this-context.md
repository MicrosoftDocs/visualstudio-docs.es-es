---
title: "&#39;&lt;nombreDeProcedimiento1&gt;&#39; no puede reemplazar &#39;&lt;nombreDeProcedimiento2&gt;&#39; porque no es accesible en este contexto. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31417"
  - "vbc31417"
helpviewer_keywords: 
  - "BC31417"
ms.assetid: 1a36acbf-cead-43a0-b12f-f52f94d09124
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nombreDeProcedimiento1&gt;&#39; no puede reemplazar &#39;&lt;nombreDeProcedimiento2&gt;&#39; porque no es accesible en este contexto.
Un procedimiento o una propiedad reemplaza un procedimiento o una propiedad con un nivel de acceso que impide el acceso del procedimiento o la propiedad de reemplazo.  
  
 Por ejemplo, si se declara un procedimiento como `Friend` en un ensamblado, este no será accesible fuera de ese ensamblado. Si un procedimiento de otro ensamblado del mismo proyecto intenta reemplazar el procedimiento `Friend`, no podrá acceder a este para reemplazarlo.  
  
 **Identificador de error:** BC31417  
  
### Para corregir este error  
  
-   Mueva el procedimiento o la propiedad de reemplazo al mismo ensamblado que el procedimiento o la propiedad que se debe reemplazar.  
  
     O bien  
  
-   Quite la palabra clave `Overrides`.  
  
## Vea también  
 [Niveles de acceso en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)   
 [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides)   
 [NO ESTÁ EN LA COMPILACIÓN: Reemplazar propiedades y métodos](http://msdn.microsoft.com/es-es/2167e8f5-1225-4b13-9ebd-02591ba90213)