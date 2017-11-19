---
title: 'CA1043: Utilizar argumento integral o de cadena para los indizadores | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
helpviewer_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: aeaaf07dd3590e4dd703cfa239c48cb7e86b7f43
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ca1043-use-integral-or-string-argument-for-indexers"></a>CA1043: Utilizar argumento integral o de cadena para los indizadores
|||  
|-|-|  
|TypeName|UseIntegralOrStringArgumentForIndexers|  
|Identificador de comprobación|CA1043|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un tipo público o protegido contiene un indizador público o protegido que utiliza un tipo de índice distinto de <xref:System.Int32?displayProperty=fullName>, <xref:System.Int64?displayProperty=fullName>, <xref:System.Object?displayProperty=fullName>, o <xref:System.String?displayProperty=fullName>.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Los indizadores, es decir, las propiedades indizadas, deben utilizar tipos enteros o de cadena para el índice. Estos tipos se utilizan normalmente para indizar las estructuras de datos y aumentan la facilidad de uso de la biblioteca. El uso de la <xref:System.Object> tipo debería limitarse a los casos donde no se puede especificar el tipo de entero o una cadena específico en tiempo de diseño. Si el diseño requiere otros tipos para el índice, reconsidere si el tipo representa un almacén de datos lógico. Si no representa un almacén de datos lógico, utilice un método.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie el índice a un tipo entero o cadena, o utilice un método en lugar del indizador.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Suprima una advertencia de esta regla después de considerar cuidadosamente la necesidad del indizador no estándar.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra un indizador que se usa un <xref:System.Int32> índice.  
  
 [!code-csharp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CSharp/ca1043-use-integral-or-string-argument-for-indexers_1.cs)]
 [!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CPP/ca1043-use-integral-or-string-argument-for-indexers_1.cpp)]
 [!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/VisualBasic/ca1043-use-integral-or-string-argument-for-indexers_1.vb)]  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1023: Los indizadores no deben ser multidimensionales](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)  
  
 [CA1024: Utilizar las propiedades donde corresponda](../code-quality/ca1024-use-properties-where-appropriate.md)