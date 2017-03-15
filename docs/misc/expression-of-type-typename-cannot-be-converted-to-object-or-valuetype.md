---
title: "No se puede convertir la expresi&#243;n de tipo &#39;&lt;nombreTipo&gt;&#39; a &#39;Object&#39; o &#39;ValueType&#39;. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31394"
  - "vbc31394"
helpviewer_keywords: 
  - "BC31394"
ms.assetid: e6f76257-65bb-4954-99f9-90f282648354
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede convertir la expresi&#243;n de tipo &#39;&lt;nombreTipo&gt;&#39; a &#39;Object&#39; o &#39;ValueType&#39;.
Una expresión se evalúa a un tipo al que Common Language Runtime \(CLR\) no puede aplicar la conversión boxing.  
  
 La *conversión boxing* hace referencia al procesamiento necesario para convertir un tipo a `Object` o, en ocasiones, a <xref:System.ValueType>. Common Language Runtime no puede aplicar la conversión boxing a determinados tipos, por ejemplo, <xref:System.ArgIterator> y <xref:System.TypedReference>.  
  
 Si no ha usado `CType` o `CObj` en la instrucción que contiene esta expresión, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ha intentado una conversión implícita que produce este error.  
  
 **Identificador de error:** BC31394  
  
### Para corregir este error  
  
1.  Localice la expresión que se evalúa en el tipo mencionado.  
  
2.  Busque la parte de la instrucción que intenta aplicar la conversión boxing al tipo mencionado.  
  
3.  Vuelva a escribir la instrucción para evitar la conversión boxing.  
  
## Vea también  
 [Conversiones implícitas y explícitas](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)