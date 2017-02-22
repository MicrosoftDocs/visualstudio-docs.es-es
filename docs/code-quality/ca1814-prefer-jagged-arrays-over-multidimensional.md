---
title: "CA1814: Preferir las matrices escalonadas antes que multidimensionales | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PreferJaggedArraysOverMultidimensional"
  - "CA1814"
helpviewer_keywords: 
  - "CA1814"
  - "PreferJaggedArraysOverMultidimensional"
ms.assetid: b1ccf563-2ec8-42e5-b89c-731a9de1ea1d
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1814: Preferir las matrices escalonadas antes que multidimensionales
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PreferJaggedArraysOverMultidimensional|  
|Identificador de comprobación|CA1814|  
|Categoría|Microsoft.Performance|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un miembro se declara como una matriz multidimensional.  
  
## Descripción de la regla  
 Una matriz escalonada es una matriz cuyos elementos son matrices.  Las matrices que constituyen los elementos pueden ser de tamaños diferentes, reduciendo el espacio desaprovechado para algunos conjuntos de datos.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie la matriz multidimensional a una matriz escalonada.  
  
## Cuándo suprimir advertencias  
 Suprima una advertencia de esta regla si la matriz multidimensional no desaprovecha el espacio.  
  
## Ejemplo  
 El ejemplo siguiente muestra las declaraciones para matrices multidimensionales y escalonadas.  
  
 [!code-vb[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/VisualBasic/ca1814-prefer-jagged-arrays-over-multidimensional_1.vb)]
 [!code-cs[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/CSharp/ca1814-prefer-jagged-arrays-over-multidimensional_1.cs)]