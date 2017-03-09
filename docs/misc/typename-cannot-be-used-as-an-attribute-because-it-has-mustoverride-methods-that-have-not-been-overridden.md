---
title: "&#39;&lt;nombreDeTipo&gt;&#39; no se puede usar como atributo porque tiene m&#233;todos &#39;MustOverride&#39; no reemplazados | Microsoft Docs"
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
  - "bc31507"
  - "vbc31507"
helpviewer_keywords: 
  - "BC31507"
ms.assetid: 843643d3-3e81-4ce3-b4df-278882f3954d
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nombreDeTipo&gt;&#39; no se puede usar como atributo porque tiene m&#233;todos &#39;MustOverride&#39; no reemplazados
Las clases con métodos `MustOverride` no se pueden usar como atributos.  
  
 Los miembros `MustOverride` de clases de atributos solo pueden usarse de clases derivadas que reemplazan estos miembros.  
  
 **Identificador de error:** BC31507  
  
### Para corregir este error  
  
1.  Quite el modificador `MustOverride` de los miembros de clase de atributo.  
  
2.  Implemente los miembros `MustOverride` de una clase derivada y use esa clase como un atributo.  
  
## Vea también  
 <xref:System.AttributeUsageAttribute>   
 [NO ESTÁ EN LA COMPILACIÓN: Atributos personalizados en Visual Basic](http://msdn.microsoft.com/es-es/d72d8a5c-8f64-4614-b15b-cad66845d047)