---
title: "La expresi&#243;n de tipo &#39;&lt;nombreDeTipo1&gt;&#39; nunca puede ser del tipo &#39;&lt;nombreDeTipo2&gt;&#39; | Microsoft Docs"
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
  - "vbc31430"
  - "bc31430"
helpviewer_keywords: 
  - "BC31430"
ms.assetid: 1d527033-3f6f-4945-b1d3-5ef59a1e1b53
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La expresi&#243;n de tipo &#39;&lt;nombreDeTipo1&gt;&#39; nunca puede ser del tipo &#39;&lt;nombreDeTipo2&gt;&#39;
Una expresión `TypeOf`...`Is` prueba una variable de referencia de objeto a un tipo de datos que no puede contener.  
  
 En algunos casos el compilador puede determinar que una prueba `TypeOf`...`Is` solo puede fallar, por ejemplo, si no hay ninguna relación de herencia entre dos clases.  
  
 El código siguiente puede generar este error.  
  
 `Dim refVar as System.Windows.Forms.Form`  
  
 `If TypeOf refVar Is System.Array`  
  
 `End If`  
  
 Dado que <xref:System.Windows.Forms.Form> y <xref:System.Array> son tipos que no tienen ninguna relación, el compilador puede determinar que la expresión `TypeOf`...`Is` devuelva `False` para cualquier valor de `refVar`.  
  
 **Identificador de error:** BC31430  
  
### Para corregir este error  
  
-   Pruebe la variable para un tipo de datos realista o quite la prueba `TypeOf`...`Is` por completo.  
  
## Vea también  
 [TypeOf \(Operador\)](/dotnet/visual-basic/language-reference/operators/typeof-operator)   
 [Cómo: Determinar el tipo al que hace referencia una variable de objeto](../Topic/How%20to:%20Determine%20What%20Type%20an%20Object%20Variable%20Refers%20To%20\(Visual%20Basic\).md)