---
title: "CA1043: Utilizar argumento integral o de cadena para los indizadores | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1043"
  - "UseIntegralOrStringArgumentForIndexers"
helpviewer_keywords: 
  - "CA1043"
  - "UseIntegralOrStringArgumentForIndexers"
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA1043: Utilizar argumento integral o de cadena para los indizadores
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseIntegralOrStringArgumentForIndexers|  
|Identificador de comprobación|CA1043|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un tipo público o protegido contiene un indizador público o protegido que utiliza un tipo de índice distinto de <xref:System.Int32?displayProperty=fullName>, <xref:System.Int64?displayProperty=fullName>, <xref:System.Object?displayProperty=fullName> o <xref:System.String?displayProperty=fullName>.  
  
## Descripción de la regla  
 Los indizadores, es decir, las propiedades indizadas, deben utilizar tipos enteros o de cadena para el índice.  Estos tipos se utilizan normalmente para indizar las estructuras de datos y aumentar la utilidad de la biblioteca.  El uso del tipo <xref:System.Object> debería limitarse a los casos en los que el tipo entero o de cadena no se puede especificar en tiempo de diseño.  Si el diseño requiere otros tipos para el índice, reconsidere si el tipo representa un almacén de datos lógico.  Si no representa un almacén de datos lógico, utilice un método.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie el índice a un tipo entero o de cadena, o utilice un método en lugar del indizador.  
  
## Cuándo suprimir advertencias  
 Sólo suprima con cuidado una advertencia de esta regla después de tener en cuenta la necesidad del indizador no estándar.  
  
## Ejemplo  
 El ejemplo siguiente muestra un indizador que utiliza un índice <xref:System.Int32>.  
  
 [!code-cs[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CSharp/ca1043-use-integral-or-string-argument-for-indexers_1.cs)]
 [!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CPP/ca1043-use-integral-or-string-argument-for-indexers_1.cpp)]
 [!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/VisualBasic/ca1043-use-integral-or-string-argument-for-indexers_1.vb)]  
  
## Reglas relacionadas  
 [CA1023: Los indizadores no deben ser multidimensionales](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)  
  
 [CA1024: Utilizar las propiedades donde corresponda](../code-quality/ca1024-use-properties-where-appropriate.md)