---
title: "La clase &#39;&lt;nombreDeClase&gt;&#39; debe declararse como &#39;MustInherit&#39; o reemplazar los siguientes miembros &#39;MustOverride&#39; heredados: &lt;nombresDeMiembros&gt;. | Microsoft Docs"
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
  - "bc30610"
  - "vbc30610"
helpviewer_keywords: 
  - "BC30610"
ms.assetid: 7fba7a3b-c918-44ba-ae85-20312615c1ce
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La clase &#39;&lt;nombreDeClase&gt;&#39; debe declararse como &#39;MustInherit&#39; o reemplazar los siguientes miembros &#39;MustOverride&#39; heredados: &lt;nombresDeMiembros&gt;.
Las clases derivadas de las clases base que contienen miembros `MustOverride` deben reemplazar dichos miembros o usar el modificador `MustInherit`.  
  
 **Identificador de error:** BC30610  
  
### Para corregir este error  
  
-   Agregue el modificador `MustInherit` a la definición de clase.  
  
-   Declare un reemplazo mediante la palabra clave `Overrides`.  
  
## Vea también  
 [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides)   
 [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)   
 [NO ESTÁ EN LA COMPILACIÓN: Herencia en Visual Basic](http://msdn.microsoft.com/es-es/e5e6e240-ed31-4657-820c-079b7c79313c)