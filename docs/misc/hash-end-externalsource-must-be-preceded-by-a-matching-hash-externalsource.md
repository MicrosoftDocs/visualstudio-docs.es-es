---
title: "&#39;#End ExternalSource&#39; debe ir precedido del c&#243;digo &#39;#ExternalSource&#39; coincidente | Microsoft Docs"
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
  - "bc30578"
  - "vbc30578"
helpviewer_keywords: 
  - "BC30578"
ms.assetid: f011673d-eced-46a7-a08e-d54d86c8a76b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;#End ExternalSource&#39; debe ir precedido del c&#243;digo &#39;#ExternalSource&#39; coincidente
La directiva `#ExternalSource` hace referencia a código externo, lo que permite al compilador informar con exactitud de cuándo se producen excepciones dentro de ese código. Un bloque `#ExternalSource` debe empezar por `#ExternalSource` y terminar con `#End ExternalSource`.  
  
 **Identificador de error:** BC30578  
  
### Para corregir este error  
  
1.  Agregue `#ExternalSource` a la ubicación adecuada en el código.  
  
2.  Quite `#End ExternalSource` si no se necesita.  
  
## Vea también  
 [\#ExternalSource \(Directiva\)](/dotnet/visual-basic/language-reference/directives/externalsource-directive)   
 [NO ESTÁ EN LA COMPILACIÓN Compilación condicional \(Visual Basic\)](http://msdn.microsoft.com/es-es/ad1e35e0-935e-4a35-a2ae-738bcf2a9240)