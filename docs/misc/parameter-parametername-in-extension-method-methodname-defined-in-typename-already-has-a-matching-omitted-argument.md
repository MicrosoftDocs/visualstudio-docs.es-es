---
title: "El par&#225;metro &#39;&lt;parametername&gt;&#39; del m&#233;todo de extensi&#243;n &#39;&lt;methodname&gt;&#39; definido en &#39;&lt;typename&gt;&#39; ya tiene un argumento omitido coincidente | Microsoft Docs"
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
  - "bc36583"
  - "vbc36583"
helpviewer_keywords: 
  - "BC36583"
ms.assetid: 662072fa-abb8-43c3-8ca2-aefb20f2e902
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El par&#225;metro &#39;&lt;parametername&gt;&#39; del m&#233;todo de extensi&#243;n &#39;&lt;methodname&gt;&#39; definido en &#39;&lt;typename&gt;&#39; ya tiene un argumento omitido coincidente
Una llamada a procedimiento a un método de extensión omite un argumento por posición y luego proporciona el argumento por nombre. Por ejemplo, la siguiente llamada al método de extensión `ABC` omite primero un argumento para el parámetro `Y` y después lo proporciona por nombre.  
  
```  
<Extension()> _ Public Sub ABC(ByVal X As Integer, Optional ByVal Y As Byte = 0, _ Optional ByVal Z As Byte = 0) End Sub ' . . . ' Calling extension method ABC. Dim number As Integer ' Not valid. ' number.ABC(, 4, Y:=5)  
```  
  
 **Id. de error:** BC36583  
  
### Para corregir este error  
  
-   Proporcione el argumento por posición o quite la coma que lo omite.  
  
## Vea también  
 [métodos de extensión.](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Pasar argumentos por posición o por nombre](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name)