---
title: "No se puede aplicar el atributo &#39;&lt;nombreDeAtributo&gt;&#39; a un m&#233;todo con par&#225;metros opcionales | Microsoft Docs"
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
  - "vbc30645"
  - "bc30645"
helpviewer_keywords: 
  - "BC30645"
ms.assetid: 4de3d2c9-5588-47c2-a6b2-e165d16106b8
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede aplicar el atributo &#39;&lt;nombreDeAtributo&gt;&#39; a un m&#233;todo con par&#225;metros opcionales
El atributo solo puede usarse con métodos que emplean argumentos necesarios o sin argumentos.  
  
 **Identificador de error:** BC30645  
  
### Para corregir este error  
  
1.  Defina el método sin parámetros opcionales.  
  
2.  Use un atributo que se pueda emplear con métodos que tienen parámetros opcionales.  
  
3.  Defina un atributo personalizado que se pueda usar en este contexto.  
  
## Vea también  
 <xref:System.AttributeUsageAttribute>   
 [NO ESTÁ EN LA COMPILACIÓN: Atributos en Visual Basic](http://msdn.microsoft.com/es-es/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)