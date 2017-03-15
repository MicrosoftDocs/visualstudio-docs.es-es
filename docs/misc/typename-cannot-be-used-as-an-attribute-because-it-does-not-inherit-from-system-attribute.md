---
title: "&#39;&lt;typename&gt;&#39; no se puede utilizar como atributo porque no se hereda de &#39;System.Attribute&#39; | Microsoft Docs"
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
  - "vbc31504"
  - "bc31504"
helpviewer_keywords: 
  - "BC31504"
ms.assetid: 37517623-5099-4db9-a461-f2f5daa4957b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;typename&gt;&#39; no se puede utilizar como atributo porque no se hereda de &#39;System.Attribute&#39;
Se intentó utilizar una clase que no se deriva de `System.Attribute`.  
  
 **Id. de error:** BC31504  
  
### Para corregir este error  
  
1.  Defina atributos personalizados como clases que derivan de `System.Attribute` agregando una instrucción `Imports` a la primera línea de código de la clase.  
  
## Vea también  
 <xref:System.AttributeUsageAttribute>   
 [NO ESTÁ EN LA COMPILACIÓN: Atributos personalizados en Visual Basic](http://msdn.microsoft.com/es-es/d72d8a5c-8f64-4614-b15b-cad66845d047)