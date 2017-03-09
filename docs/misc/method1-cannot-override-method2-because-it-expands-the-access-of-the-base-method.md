---
title: "&#39;&lt;m&#233;todo1&gt;&#39; no puede reemplazar a &#39;&lt;m&#233;todo2&gt;&#39; porque expande el acceso del m&#233;todo base | Microsoft Docs"
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
  - "vbc32203"
  - "bc32203"
helpviewer_keywords: 
  - "BC32203"
ms.assetid: ef7816a4-5f57-4346-80fc-9311bc150b6b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;m&#233;todo1&gt;&#39; no puede reemplazar a &#39;&lt;m&#233;todo2&gt;&#39; porque expande el acceso del m&#233;todo base
Un procedimiento especifica `Overrides`, pero declara una accesibilidad menos restrictiva que la del método que se va a reemplazar. No se puede expandir la accesibilidad, lo que significa que el método de reemplazo no puede ser más accesible que el método al que reemplaza. Por ejemplo, si el método de la clase base es `Protected`, no se puede reemplazar por un método `Public`.  
  
 **Identificador de error:** BC32203  
  
### Para corregir este error  
  
-   Quite la palabra clave `Overrides`, o cambie la accesibilidad para que sea al menos tan restrictiva como la del método de la clase base.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Reemplazar propiedades y métodos](http://msdn.microsoft.com/es-es/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [Niveles de acceso en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)   
 [Sombrear en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/shadowing)