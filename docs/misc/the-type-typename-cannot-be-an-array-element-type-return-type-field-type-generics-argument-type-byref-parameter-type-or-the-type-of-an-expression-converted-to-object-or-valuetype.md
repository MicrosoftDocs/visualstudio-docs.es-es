---
title: "El tipo &#39;&lt;nombreTipo&gt;&#39; no puede ser un tipo de elemento de matriz, un tipo de valor devuelto, un tipo de campo, un tipo de argumento gen&#233;rico, un tipo de par&#225;metro &#39;ByRef&#39; ni un tipo de una expresi&#243;n convertida a &#39;Object&#39; o &#39;ValueType&#39;. | Microsoft Docs"
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
  - "vbc31396"
  - "BC31396"
helpviewer_keywords: 
  - "BC31396"
ms.assetid: 56998a2c-a705-482e-87ee-5eff707f8a48
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El tipo &#39;&lt;nombreTipo&gt;&#39; no puede ser un tipo de elemento de matriz, un tipo de valor devuelto, un tipo de campo, un tipo de argumento gen&#233;rico, un tipo de par&#225;metro &#39;ByRef&#39; ni un tipo de una expresi&#243;n convertida a &#39;Object&#39; o &#39;ValueType&#39;.
Una expresión declara que una variable, un parámetro de procedimiento, un parámetro de tipo, un valor devuelto de función o una matriz es de un tipo restringido.  
  
 Common Language Runtime \(CLR\) expone determinados tipos únicamente para la compatibilidad de lenguaje especial y no deben usarse como tipos de datos en la aplicación. Estos tipos incluyen las estructuras <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle> y <xref:System.TypedReference>.  
  
 **Identificador de error:** BC31396  
  
### Para corregir este error  
  
-   No use la estructura restringida como un tipo de datos declarado.  
  
## Vea también  
 <xref:System.ArgIterator>   
 <xref:System.RuntimeArgumentHandle>   
 <xref:System.TypedReference>