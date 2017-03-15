---
title: "Las variables locales dentro de los m&#233;todos gen&#233;ricos no se pueden declarar como &#39;Static&#39; | Microsoft Docs"
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
  - "vbc32068"
  - "bc32068"
helpviewer_keywords: 
  - "BC32068"
ms.assetid: cb5df484-76f9-4092-9d19-f26ddcf1c035
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Las variables locales dentro de los m&#233;todos gen&#233;ricos no se pueden declarar como &#39;Static&#39;
La declaración de una variable local dentro de un procedimiento genérico especifica `Static`.  
  
 Visual Basic y .NET Framework no admiten actualmente ninguna combinación de variables estáticas y procedimientos genéricos.  
  
 **Id. de error:** BC32068  
  
### Para corregir este error  
  
-   Quite la palabra clave `Static` de la declaración de variable.  
  
## Vea también  
 [Static](/dotnet/visual-basic/language-reference/modifiers/static)   
 [NO ESTÁ EN LA COMPILACIÓN Procedimiento: prolongar la duración de una variable](http://msdn.microsoft.com/es-es/04e7c56c-1db0-4fe5-a678-859a39ec654b)   
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Procedimientos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)