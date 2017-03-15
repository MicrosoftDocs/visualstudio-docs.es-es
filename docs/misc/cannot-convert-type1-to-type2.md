---
title: "No se puede convertir &#39;type1&#39; en &#39;type2&#39; | Microsoft Docs"
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
  - "bc31193"
  - "vbc31193"
helpviewer_keywords: 
  - "BC31193"
ms.assetid: f25a9f5b-7741-4cd6-b85a-b19037ed8e49
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede convertir &#39;type1&#39; en &#39;type2&#39;
No se puede convertir 'type1' en 'type2'. Puede usar la propiedad 'Value' para obtener el valor de cadena del primer elemento de '\<elementoPrimario\>'.  
  
 Se intentó convertir implícitamente un literal XML a un tipo específico. El literal XML no se puede convertir implícitamente al tipo especificado.  
  
 **Identificador de error:** BC31193  
  
### Para corregir este error  
  
-   Use la propiedad `Value` del literal XML para hacer referencia a su valor como `String`. Use la función `CType`, otra función de conversión de tipo o la clase <xref:System.Convert> para convertir el valor como el tipo especificado.  
  
## Vea también  
 <xref:System.Convert>   
 [Obtener acceso a XML en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/xml/accessing-xml)   
 [Funciones de conversión de tipos](/dotnet/visual-basic/language-reference/functions/type-conversion-functions)   
 [Literales XML](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)