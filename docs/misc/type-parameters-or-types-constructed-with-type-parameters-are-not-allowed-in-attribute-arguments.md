---
title: "No se permiten los par&#225;metros de tipo o los tipos construidos con par&#225;metros de tipo en argumentos de atributo. | Microsoft Docs"
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
  - "BC32079"
  - "vbc32079"
helpviewer_keywords: 
  - "BC32079"
ms.assetid: 93eb59bd-e7db-4f73-a37f-405a83df48c1
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se permiten los par&#225;metros de tipo o los tipos construidos con par&#225;metros de tipo en argumentos de atributo.
Un atributo se aplica usando un argumento que es un parámetro de tipo o se construye usando un parámetro de tipo.  
  
 Visual Basic y .NET Framework no admiten actualmente ninguna combinación de atributos y tipos genéricos. Esto significa que se aplican las siguientes limitaciones:  
  
-   Un atributo no puede ser un tipo genérico ni declararse dentro de un tipo genérico.  
  
-   Un atributo no puede heredar de una clase genérica, ni una clase genérica puede heredar de un atributo.  
  
-   Cuando se aplica un atributo, no se puede proporcionar un argumento que sea cualquiera de los siguientes:  
  
    -   Un tipo genérico  
  
    -   Un tipo construido a partir de un tipo genérico  
  
    -   Un parámetro de tipo de un tipo de contenedor  
  
    -   Un tipo construido a partir de un parámetro de tipo de un tipo contenedor  
  
 **Identificador de error:** BC32079  
  
### Para corregir este error  
  
-   Reconstruya los argumentos proporcionados al atributo para que no incluyan parámetros de tipo ni ningún tipo construido a partir de un parámetro de tipo.  
  
## Vea también  
 <xref:System.Attribute>   
 [NO ESTÁ EN LA COMPILACIÓN: Información general de atributos en Visual Basic](http://msdn.microsoft.com/es-es/0d0cff64-892d-4f57-83bd-bef388553d4f)   
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)