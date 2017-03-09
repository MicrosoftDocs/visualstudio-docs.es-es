---
title: "No se puede aplicar el atributo &#39;&lt;nombreDeAtributo&gt;&#39; a &#39;&lt;nombreDeMiembro&gt;&#39; porque el atributo no es v&#225;lido en este tipo de declaraci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30662"
  - "bc30662"
helpviewer_keywords: 
  - "BC30662"
ms.assetid: 5cd07950-37d0-45e9-8770-3eaac54ff7d9
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede aplicar el atributo &#39;&lt;nombreDeAtributo&gt;&#39; a &#39;&lt;nombreDeMiembro&gt;&#39; porque el atributo no es v&#225;lido en este tipo de declaraci&#243;n
El atributo que está usando no es adecuado para el elemento que está usando.  
  
 **Identificador de error:** BC30662  
  
### Para corregir este error  
  
1.  Seleccione un atributo que sirva para el elemento que está usando. Por ejemplo, si usa un método, seleccione un atributo diseñado para usarse con métodos.  
  
2.  Si usa atributos personalizados desarrollados por usted, cambie el atributo `AttributeUsage` para que coincida con el tipo de elemento que está usando.  
  
## Vea también  
 <xref:System.AttributeUsageAttribute>   
 [NO ESTÁ EN LA COMPILACIÓN: Atributos en Visual Basic](http://msdn.microsoft.com/es-es/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)   
 [NO ESTÁ EN LA COMPILACIÓN: Atributos personalizados en Visual Basic](http://msdn.microsoft.com/es-es/d72d8a5c-8f64-4614-b15b-cad66845d047)