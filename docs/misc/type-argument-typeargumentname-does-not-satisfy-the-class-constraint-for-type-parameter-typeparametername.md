---
title: "El argumento de tipo &#39;&lt;nombreDeArgumentoDeTipo&gt;&#39; no satisface la restricci&#243;n &#39;Class&#39; para el par&#225;metro de tipo &#39;&lt;nombreDePar&#225;metroDeTipo&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32106"
  - "bc32106"
helpviewer_keywords: 
  - "BC32106"
ms.assetid: 1bac1dd6-f86b-4e98-ba2d-57d1936e3658
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El argumento de tipo &#39;&lt;nombreDeArgumentoDeTipo&gt;&#39; no satisface la restricci&#243;n &#39;Class&#39; para el par&#225;metro de tipo &#39;&lt;nombreDePar&#225;metroDeTipo&gt;&#39;
Un argumento de tipo proporcionado a un tipo genérico no satisface la restricción de tipo de referencia en su parámetro de tipo correspondiente.  
  
 Una lista de restricciones impone requisitos al argumento de tipo pasado al parámetro de tipo. Si no incluye ninguna clase o interfaz específica en la lista de restricciones, puede imponer un requisito general especificando uno de los elementos siguientes:  
  
-   El argumento de tipo debe ser un tipo de valor \[incluya la restricción [Structure \(Visual Basic\)](http://msdn.microsoft.com/es-es/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)\]  
  
-   El argumento de tipo debe ser un tipo de referencia \[incluya la restricción [Class \(Visual Basic\)](http://msdn.microsoft.com/es-es/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)\]  
  
 No es posible especificar `Structure` y `Class` para el mismo parámetro de tipo ni se pueden especificar estas restricciones más de una vez.  
  
 **Identificador de error:** BC32106  
  
### Para corregir este error  
  
-   Seleccione un argumento de tipo de cualquier tipo de referencia.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Tipos de valor y tipos de referencia](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)   
 [Cómo: Utilizar una clase genérica](../Topic/How%20to:%20Use%20a%20Generic%20Class%20\(Visual%20Basic\).md)