---
title: "El argumento de tipo &#39;&lt;nombreDeArgumentoDeTipo&gt;&#39; no hereda del tipo de restricci&#243;n &#39;&lt;nombreDePar&#225;metroDeTipo&gt;&#39; ni lo implementa | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32044"
  - "vbc32044"
helpviewer_keywords: 
  - "BC32044"
ms.assetid: be91f648-c07d-4991-8ed1-28b1327619c4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El argumento de tipo &#39;&lt;nombreDeArgumentoDeTipo&gt;&#39; no hereda del tipo de restricci&#243;n &#39;&lt;nombreDePar&#225;metroDeTipo&gt;&#39; ni lo implementa
Un argumento de tipo proporcionado a un tipo genérico no satisface la restricción de herencia o implementación en su parámetro de tipo correspondiente.  
  
 Una lista de restricciones impone requisitos al argumento de tipo pasado al parámetro de tipo. Entre los posibles requisitos se incluyen:  
  
-   El argumento de tipo debe implementar una o varias interfaces  
  
-   El argumento de tipo debe heredar de al menos una clase  
  
 Puede combinar los requisitos anteriores para un parámetro de tipo único.[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] no puede construir el tipo a menos que el código proporcione argumentos de tipo que cumplan todas las restricciones de cada parámetro de tipo definido en el tipo genérico.  
  
 **Identificador de error:** BC32044  
  
### Para corregir este error  
  
-   Seleccione un argumento de tipo de un tipo que implemente cada interfaz especificada para el parámetro de tipo y que herede de la clase especificada, si existe alguna.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Cómo: Utilizar una clase genérica](../Topic/How%20to:%20Use%20a%20Generic%20Class%20\(Visual%20Basic\).md)