---
title: "La referencia de ensamblado de confianza &lt;reference&gt; no es v&#225;lida. Las declaraciones InternalsVisibleTo no pueden tener una versi&#243;n, un token de clave p&#250;blica, una referencia cultural o una arquitectura de procesador especificada. | Microsoft Docs"
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
  - "bc31534"
  - "vbc31534"
helpviewer_keywords: 
  - "BC31534"
ms.assetid: ae1e470e-3105-48f2-87b1-466e395a7d44
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La referencia de ensamblado de confianza &lt;reference&gt; no es v&#225;lida. Las declaraciones InternalsVisibleTo no pueden tener una versi&#243;n, un token de clave p&#250;blica, una referencia cultural o una arquitectura de procesador especificada.
El nombre del ensamblado que se pasa al constructor de atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> contiene un atributo `Version`, `Culture`, `PublicKeyToken` o `processorArchitecture`.  
  
 **Identificador de error:** BC31534  
  
### Para corregir este error  
  
1.  Quite el atributo `Version`, `Culture`, `PublicKeyToken` o `processorArchitecture` del nombre de ensamblado pasado al constructor de atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.  
  
## Vea también  
 <xref:System.Reflection.AssemblyName>   
 [NO ESTÁ EN LA COMPILACIÓN: Ensamblados de confianza \(Visual Basic\)](http://msdn.microsoft.com/es-es/80e7a33a-ca91-450b-a00e-c5a7986e228c)