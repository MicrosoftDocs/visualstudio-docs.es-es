---
title: "El constructor de atributos tiene un par&#225;metro de tipo &#39;&lt;type&gt;&#39;, que no es de tipo integral, punto flotante o enumeraci&#243;n, ni de tipo Char, String, Boolean o System.Type o una matriz unidimensional de estos tipos | Microsoft Docs"
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
  - "bc30045"
  - "vbc30045"
helpviewer_keywords: 
  - "BC30045"
ms.assetid: 16899755-7901-4c56-ae90-54c3532e8319
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El constructor de atributos tiene un par&#225;metro de tipo &#39;&lt;type&gt;&#39;, que no es de tipo integral, punto flotante o enumeraci&#243;n, ni de tipo Char, String, Boolean o System.Type o una matriz unidimensional de estos tipos
Una definición de atributo personalizada incluye un constructor que especifica un tipo de datos no válido para un parámetro. Los atributos pueden tomar solo determinados tipos de datos como parámetros, porque solo esos tipos se pueden serializar en los metadatos del ensamblado.  
  
 **Identificador de error:** BC30045  
  
### Para corregir este error  
  
1.  Cambie el tipo de datos del parámetro a `Byte`, `Short`, `Integer`, `Long`, `Single`, `Double`, `Char`, `String`, `Boolean`, `System.Type` o un tipo de enumeración.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Atributos personalizados en Visual Basic](http://msdn.microsoft.com/es-es/d72d8a5c-8f64-4614-b15b-cad66845d047)