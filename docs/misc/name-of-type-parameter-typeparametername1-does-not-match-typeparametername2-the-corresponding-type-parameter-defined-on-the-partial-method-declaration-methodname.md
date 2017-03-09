---
title: "El nombre del par&#225;metro de tipo &#39;&lt;nombreDePar&#225;metroDeTipo1&gt;&#39; no coincide con &#39;&lt;nombreDePar&#225;metroDeTipo2&gt;, que es el tipo de par&#225;metro correspondiente definido en la declaraci&#243;n del m&#233;todo parcial &#39;&lt;nombreDeM&#233;todo&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31443"
  - "bc31443"
helpviewer_keywords: 
  - "BC31443"
ms.assetid: 27c81cc1-325e-4e86-9d00-34f81e928076
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El nombre del par&#225;metro de tipo &#39;&lt;nombreDePar&#225;metroDeTipo1&gt;&#39; no coincide con &#39;&lt;nombreDePar&#225;metroDeTipo2&gt;, que es el tipo de par&#225;metro correspondiente definido en la declaraci&#243;n del m&#233;todo parcial &#39;&lt;nombreDeM&#233;todo&gt;&#39;
En un método parcial que incluye uno o varios parámetros de tipo, los nombres de los parámetros de tipo deben ser iguales en la declaración del método y en la implementación del método.  
  
 Por ejemplo, la declaración e implementación siguientes provocan este error.  
  
```vb#  
' Definition of the partial method signature with type parameter T. Partial Private Sub OnNameChanged(Of T)() End Sub  
```  
  
```vb#  
'' Implementation of the partial method with type parameter N. 'Private Sub OnNameChanged(Of N)() '    Console.WriteLine("Name was changed to " & Me.Name) 'End Sub  
```  
  
 **Identificador de error:** BC31443  
  
### Para corregir este error  
  
-   Examine los parámetros de tipo para determinar dónde no coinciden. Cambiar los nombres según sea necesario para que sean iguales.  
  
## Vea también  
 [Métodos Partial](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)   
 [Procedimientos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)