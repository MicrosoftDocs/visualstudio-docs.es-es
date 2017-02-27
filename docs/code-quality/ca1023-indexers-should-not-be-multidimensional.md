---
title: "CA1023: Los indizadores no deben ser multidimensionales | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IndexersShouldNotBeMultidimensional"
  - "CA1023"
helpviewer_keywords: 
  - "CA1023"
  - "IndexersShouldNotBeMultidimensional"
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA1023: Los indizadores no deben ser multidimensionales
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IndexersShouldNotBeMultidimensional|  
|Identificador de comprobación|CA1023|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un tipo público o protegido contiene un indizador público o protegido que utiliza más de un índice.  
  
## Descripción de la regla  
 Los indizadores, es decir, las propiedades indizadas, deben utilizar un índice único.  Los indizadores multidimensionales pueden reducir de forma significativa la utilidad de la biblioteca.  Si el diseño requiere varios índices, reconsidere si un tipo representa un almacén de datos lógico.  Si no es así, use un método.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie el diseño para utilizar un solo entero o un índice de cadena o utilice un método en lugar del indizador.  
  
## Cuándo suprimir advertencias  
 Sólo suprima con cuidado una advertencia de esta regla después de tener en cuenta la necesidad del indizador no estándar.  
  
## Ejemplo  
 El ejemplo siguiente muestra un tipo, `DayOfWeek03`, con un indizador multidimensional que infringe la regla.  El indizador se puede considerar un tipo de conversión y, por tanto, es más apropiado exponerlo como un método.  El tipo se vuelve a diseñar en `RedesignedDayOfWeek03` para cumplir la regla.  
  
 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/VisualBasic/ca1023-indexers-should-not-be-multidimensional_1.vb)]
 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CPP/ca1023-indexers-should-not-be-multidimensional_1.cpp)]
 [!code-cs[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CSharp/ca1023-indexers-should-not-be-multidimensional_1.cs)]  
  
## Reglas relacionadas  
 [CA1043: Utilizar argumento integral o de cadena para los indizadores](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)  
  
 [CA1024: Utilizar las propiedades donde corresponda](../code-quality/ca1024-use-properties-where-appropriate.md)