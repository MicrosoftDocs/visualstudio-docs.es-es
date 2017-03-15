---
title: "Argumentos de tipo no esperados porque los atributos no pueden ser gen&#233;ricos | Microsoft Docs"
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
  - "bc32066"
  - "vbc32066"
helpviewer_keywords: 
  - "BC32066"
ms.assetid: cd43a92c-33fb-4def-bbf7-527d21bff93c
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Argumentos de tipo no esperados porque los atributos no pueden ser gen&#233;ricos
Un atributo se aplica con una lista de argumentos de tipo.  
  
 Visual Basic y .NET Framework no admiten actualmente ninguna combinación de atributos y tipos genéricos. Esto significa que se aplican las siguientes limitaciones:  
  
-   Un atributo no puede ser un tipo genérico ni declararse dentro de un tipo genérico.  
  
-   Un atributo no puede heredar de una clase genérica, ni una clase genérica puede heredar de un atributo.  
  
-   Cuando se aplica un atributo, no se puede proporcionar un argumento que sea cualquiera de los siguientes:  
  
    -   Un tipo genérico  
  
    -   Un tipo construido a partir de un tipo genérico  
  
    -   Un parámetro de tipo de un tipo de contenedor  
  
    -   Un tipo construido a partir de un parámetro de tipo de un tipo contenedor  
  
 **Id. de error:** BC32066  
  
### Para corregir este error  
  
-   Si los argumentos de tipo están pensados para ser argumentos normales, quite la palabra clave `Of`. Al hacerlo, la lista de argumentos de tipo se convierte en una lista de argumentos normal.  
  
-   Si los argumentos de tipo están diseñados para se faciliten a parámetros de tipo, quite la palabra clave `Of` y los argumentos de tipo. Un atributo no puede aceptar argumentos de tipo.  
  
## Vea también  
 <xref:System.Attribute>   
 [NO ESTÁ EN LA COMPILACIÓN: Información general de atributos en Visual Basic](http://msdn.microsoft.com/es-es/0d0cff64-892d-4f57-83bd-bef388553d4f)   
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)