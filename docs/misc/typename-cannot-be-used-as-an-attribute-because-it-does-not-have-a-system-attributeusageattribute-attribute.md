---
title: "&#39;&lt;nombreDeTipo&gt;&#39; no se puede usar como atributo porque no tiene un atributo &#39;System.AttributeUsageAttribute&#39; | Microsoft Docs"
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
  - "vbc31505"
  - "bc31505"
helpviewer_keywords: 
  - "BC31505"
ms.assetid: 7dd84c9d-6711-4dab-afc6-1fe4dee78051
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nombreDeTipo&gt;&#39; no se puede usar como atributo porque no tiene un atributo &#39;System.AttributeUsageAttribute&#39;
Se intentó usar un atributo declarado sin el `System.AttributeUsageAttribute` para definir su uso.  
  
 **Identificador de error:** BC31505  
  
### Para corregir este error  
  
1.  Los atributos personalizados deben ser clases derivadas de`System.Attribute` que tengan el atributo `AttributeUsageAttribute` aplicado.  
  
## Vea también  
 <xref:System.AttributeUsageAttribute>   
 [NO ESTÁ EN LA COMPILACIÓN: Atributos personalizados en Visual Basic](http://msdn.microsoft.com/es-es/d72d8a5c-8f64-4614-b15b-cad66845d047)