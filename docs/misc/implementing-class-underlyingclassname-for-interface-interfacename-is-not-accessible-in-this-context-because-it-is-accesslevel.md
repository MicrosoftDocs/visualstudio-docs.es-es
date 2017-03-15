---
title: "La implementaci&#243;n de la clase &#39;&lt;underlyingclassname&gt;&#39; para la interfaz &#39;&lt;interfacename&gt;&#39; no es accesible en este contexto porque es &#39;&lt;accesslevel&gt;&#39; | Microsoft Docs"
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
  - "BC31109"
  - "vbc31109"
helpviewer_keywords: 
  - "BC31109"
ms.assetid: ab2a3bc3-b875-476f-b601-3e736ad2677e
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La implementaci&#243;n de la clase &#39;&lt;underlyingclassname&gt;&#39; para la interfaz &#39;&lt;interfacename&gt;&#39; no es accesible en este contexto porque es &#39;&lt;accesslevel&gt;&#39;
Se declara una interfaz con el <xref:System.Runtime.InteropServices.CoClassAttribute> que especifica una clase subyacente, pero esa clase tiene un nivel de acceso que impide al código tener acceso a ella.  
  
 Al aplicar el <xref:System.Runtime.InteropServices.CoClassAttribute> a una interfaz, se asocia una clase subyacente a la interfaz. Esto permite que el código cree un objeto directamente desde la interfaz con una cláusula `New`.  
  
 Si el código que usa la cláusula `New` no tiene acceso a la clase subyacente, por ejemplo, si la clase es `Private`, el compilador genera este error.  
  
 **Identificador de error:** BC31109  
  
### Para corregir este error  
  
1.  Si tiene el control de código fuente sobre la clase subyacente, ajuste su nivel de acceso para que el código en uso pueda obtener acceso a esta.  
  
2.  Si por alguna razón no puede cambiar el nivel de acceso de la clase subyacente, quite la cláusula `New`. No se puede crear un objeto directamente desde esta interfaz.  
  
## Vea también  
 <xref:System.Runtime.InteropServices.CoClassAttribute>   
 [New \(Operador\)](/dotnet/visual-basic/language-reference/operators/new-operator)   
 [Niveles de acceso en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)