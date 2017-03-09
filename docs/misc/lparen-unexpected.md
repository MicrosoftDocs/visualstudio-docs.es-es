---
title: "&#39;(&#39; inesperado | Microsoft Docs"
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
  - "vbc32095"
  - "bc32095"
helpviewer_keywords: 
  - "BC32095"
ms.assetid: a47ad15a-2cfc-4d17-9012-27ba85b7d783
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;(&#39; inesperado
'\(' inesperado. No se permiten matrices de tipos genéricos sin instancias.  
  
 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] no puede compilar una matriz a menos que sea un tipo de datos específico. No puede usar un parámetro de tipo de datos de un tipo genérico como el tipo de datos de una matriz.  
  
 **Identificador de error:** BC32095  
  
### Para corregir este error  
  
-   Si necesita usar una matriz, debe declararla para que sea un tipo de datos específico. No se puede usar un parámetro de tipo de datos.  
  
-   Si necesita un grupo de elementos del tipo de datos que se va a proporcionar para un parámetro de tipo de datos, debe usar una colección en lugar de una matriz.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [NO ESTÁ EN LA COMPILACIÓN Colecciones en Visual Basic](http://msdn.microsoft.com/es-es/8b2b7845-2251-4573-8dd3-c9f9c0a66a21)   
 [Administración de grupos de objetos en Visual Basic](http://msdn.microsoft.com/es-es/50be4910-4732-4d5f-a18a-055a162e9037)