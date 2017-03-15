---
title: "Las directivas &#39;#ExternalSource&#39; no se pueden anidar. | Microsoft Docs"
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
  - "bc30580"
  - "vbc30580"
helpviewer_keywords: 
  - "BC30580"
ms.assetid: 56c6ef4b-28b1-4a62-8afa-d83a7742b507
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Las directivas &#39;#ExternalSource&#39; no se pueden anidar.
Se intentó colocar una directiva `#ExternalSource` dentro de un bloque de otra `#ExternalSource`. La directiva `#ExternalSource` hace referencia a código externo, lo que permite al compilador informar con exactitud de cuándo se producen excepciones dentro de ese código.  
  
 Los bloques de `#ExternalSource` no se pueden anidar dentro de otros bloques de `#ExternalSource`.  
  
 **Identificador de error:** BC30580  
  
### Para corregir este error  
  
-   Mueva la directiva `#ExternalSource` interna fuera del bloque de `#ExternalSource` que la contiene.  
  
## Vea también  
 [\#ExternalSource \(Directiva\)](/dotnet/visual-basic/language-reference/directives/externalsource-directive)   
 [NOTINBUILD Compilación condicional \(Visual Basic\)](http://msdn.microsoft.com/es-es/ad1e35e0-935e-4a35-a2ae-738bcf2a9240)