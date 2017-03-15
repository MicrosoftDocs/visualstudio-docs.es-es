---
title: "&#39;System.Nullable&#39; no satisface la restricci&#243;n &#39;Structure&#39; para el par&#225;metro de tipo &#39;&lt;nombreDePar&#225;metroDeTipo&gt;&#39; | Microsoft Docs"
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
  - "bc32115"
  - "vbc32115"
helpviewer_keywords: 
  - "BC32115"
ms.assetid: 98053645-fa76-4826-a7c1-f1bdf3511863
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System.Nullable&#39; no satisface la restricci&#243;n &#39;Structure&#39; para el par&#225;metro de tipo &#39;&lt;nombreDePar&#225;metroDeTipo&gt;&#39;
Se invoca un tipo genérico pasando un argumento de tipo <xref:System.Nullable%601> a un parámetro de tipo con una restricción `Structure`.  
  
 Common Language Runtime \(CLR\) deniega específicamente la estructura <xref:System.Nullable%601> como un argumento de tipo para sí mismo. Aunque es una estructura y satisfaría una restricción `Structure`, su uso de forma recursiva podría generar construcciones extrañas como `Nullable(Of Nullable(Of Nullable))`.  
  
 **Identificador de error:** BC32115  
  
### Para corregir este error  
  
-   Quite la restricción `Structure` del parámetro de tipo o cambie el argumento de tipo a algún tipo de valor que no sea <xref:System.Nullable%601>.  
  
## Vea también  
 <xref:System.Nullable%601>   
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Structure \(Visual Basic\)](http://msdn.microsoft.com/es-es/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)