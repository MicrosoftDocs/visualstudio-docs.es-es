---
title: "Option Strict On no permite reducciones en conversiones de tipo impl&#237;cito entre el m&#233;todo de extensi&#243;n &#39;&lt;nombreM&#233;todoExtensi&#243;n&gt;&#39; definido en &#39;nombreM&#243;dulo&#39; y el delegado &#39;nombreDelegado&#39;. | Microsoft Docs"
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
  - "bc36709"
  - "vbc36709"
helpviewer_keywords: 
  - "BC36709"
ms.assetid: 95d8c833-3525-411b-98e8-b7d3f61f75c9
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On no permite reducciones en conversiones de tipo impl&#237;cito entre el m&#233;todo de extensi&#243;n &#39;&lt;nombreM&#233;todoExtensi&#243;n&gt;&#39; definido en &#39;nombreM&#243;dulo&#39; y el delegado &#39;nombreDelegado&#39;.
Cuando se activa `Option Strict`, no se puede realizar una conversión de restricción del tipo de datos de un parámetro en un delegado al parámetro correspondiente de un método de extensión asignado a una variable de ese tipo de delegado. El tipo de datos del parámetro de delegado debe ampliarse al tipo de datos del método de extensión.  
  
 **Identificador de error:** BC36709  
  
### Para corregir este error  
  
-   Cambie el tipo de datos del parámetro en el delegado o el método de extensión para que exista la relación de ampliación necesaria.  
  
## Vea también  
 [métodos de extensión.](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Conversión de delegado flexible](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)   
 [Delegados](/dotnet/visual-basic/programming-guide/language-features/delegates/delegates)   
 [Conversiones de ampliación y de restricción](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [NO ESTÁ EN LA COMPILACIÓN: Delegados y el operador AddressOf](http://msdn.microsoft.com/es-es/7b2ed932-8598-4355-b2f7-5cedb23ee86f)