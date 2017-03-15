---
title: "El m&#233;todo de extensi&#243;n &#39;&lt;nombreM&#233;todo&gt;&#39; definido en &#39;&lt;nombreM&#243;dulo&gt;&#39; no tiene una signatura compatible con el delegado &#39;&lt;nombreDelegado&gt;&#39;. | Microsoft Docs"
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
  - "bc36710"
  - "vbc36710"
helpviewer_keywords: 
  - "BC36710"
ms.assetid: e439d9e0-7821-451a-a7b7-68c1cf1a85a3
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El m&#233;todo de extensi&#243;n &#39;&lt;nombreM&#233;todo&gt;&#39; definido en &#39;&lt;nombreM&#243;dulo&gt;&#39; no tiene una signatura compatible con el delegado &#39;&lt;nombreDelegado&gt;&#39;.
Hay un error de coincidencia entre las signaturas del método de extensión y el delegado que está intentando usar. La instrucción `Delegate` define los tipos de parámetro y los tipos de valor devueltos de una clase de delegado. Cualquier procedimiento con parámetros compatibles, tipos de parámetros y tipo de valor devuelto puede usarse para crear una instancia de este tipo de delegado.  
  
 **Identificador de error:** BC36710  
  
## Vea también  
 [Conversión de delegado flexible](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)   
 [Delegate \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [NO ESTÁ EN LA COMPILACIÓN: Delegados y el operador AddressOf](http://msdn.microsoft.com/es-es/7b2ed932-8598-4355-b2f7-5cedb23ee86f)