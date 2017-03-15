---
title: "La instrucci&#243;n &#39;#ExternalSource&#39; debe terminar con la instrucci&#243;n &#39;#End ExternalSource&#39; correspondiente. | Microsoft Docs"
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
  - "vbc30579"
  - "bc30579"
helpviewer_keywords: 
  - "BC30579"
ms.assetid: 8d658008-eddc-4b7d-a8d4-036da42957bf
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La instrucci&#243;n &#39;#ExternalSource&#39; debe terminar con la instrucci&#243;n &#39;#End ExternalSource&#39; correspondiente.
La directiva `#ExternalSource` hace referencia a código externo, lo que permite al compilador informar con exactitud de cuándo se producen excepciones dentro de ese código. Un bloque de `#ExternalSource` debe empezar por `#ExternalSource` y finalizar con `#End ExternalSource`.  
  
 **Identificador de error:** BC30579  
  
### Para corregir este error  
  
1.  Agregue `#End ExternalSource` a la ubicación adecuada en el código.  
  
2.  Quite la instrucción `#ExternalSource` inicial si no es necesaria.  
  
## Vea también  
 [\#ExternalSource \(Directiva\)](/dotnet/visual-basic/language-reference/directives/externalsource-directive)   
 [NOTINBUILD Compilación condicional \(Visual Basic\)](http://msdn.microsoft.com/es-es/ad1e35e0-935e-4a35-a2ae-738bcf2a9240)