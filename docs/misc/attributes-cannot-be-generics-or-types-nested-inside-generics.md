---
title: "Los atributos no pueden ser gen&#233;ricos ni tipos anidados dentro de gen&#233;ricos. | Microsoft Docs"
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
  - "bc32067"
  - "vbc32067"
helpviewer_keywords: 
  - "BC32067"
ms.assetid: 93ae2848-0a72-4ae5-82a3-32e0a49bb7cd
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los atributos no pueden ser gen&#233;ricos ni tipos anidados dentro de gen&#233;ricos.
Un atributo se declara como tipo genérico o dentro de un tipo genérico.  
  
 Visual Basic y .NET Framework no admiten actualmente ninguna combinación de atributos y tipos genéricos. Esto significa que se aplican las siguientes limitaciones:  
  
-   Un atributo no puede ser un tipo genérico ni declararse dentro de un tipo genérico.  
  
-   Un atributo no puede heredar de una clase genérica, ni una clase genérica puede heredar de un atributo.  
  
-   Cuando se aplica un atributo, no se puede proporcionar un argumento que sea cualquiera de los siguientes:  
  
    -   Un tipo genérico  
  
    -   Un tipo construido a partir de un tipo genérico  
  
    -   Un parámetro de tipo de un tipo de contenedor  
  
    -   Un tipo construido a partir de un parámetro de tipo de un tipo contenedor  
  
 **Identificador de error:** BC32067  
  
### Para corregir este error  
  
-   Si la declaración del atributo incluye la palabra clave `Of` y una lista de parámetros de tipo, elimínelas.  
  
-   Si la declaración del atributo aparece dentro de un tipo genérico, muévala fuera de cualquier tipo genérico.  
  
## Vea también  
 <xref:System.Attribute>   
 [NO ESTÁ EN LA COMPILACIÓN: Información general de atributos en Visual Basic](http://msdn.microsoft.com/es-es/0d0cff64-892d-4f57-83bd-bef388553d4f)   
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)