---
title: 'CA1064: Las excepciones deben ser públicas | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1064
- ExceptionsShouldBePublic
helpviewer_keywords:
- ExceptionsShouldBePublic
- CA1064
ms.assetid: 83eb224c-2456-4368-acf4-3b3378e67759
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5d110c03cc09124f672cb6be7421b60d2014bd58
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca1064-exceptions-should-be-public"></a>CA1064: Las excepciones deben ser públicas
|||  
|-|-|  
|TypeName|ExceptionsShouldBePublic|  
|Identificador de comprobación|CA1064|  
|Categoría|Microsoft.Design|  
|Cambio problemático|No trascendental|  
  
## <a name="cause"></a>Motivo  
 Una excepción no pública deriva directamente de <xref:System.Exception>, <xref:System.SystemException>, o <xref:System.ApplicationException>.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Una excepción interna solo está visible dentro de su propio ámbito interno. Cuando la excepción esté fuera del ámbito interno, sólo se podrá usar la excepción base para detectarla. Si la excepción interna se hereda de <xref:System.Exception>, <xref:System.SystemException>, o <xref:System.ApplicationException>, el código externo no tendrá información suficiente para saber qué hacer con la excepción.  
  
 Sin embargo, si el código tiene una excepción pública que más adelante se utiliza como base para una excepción interna, es razonable suponer que más el código espera será capaz de hacer algo inteligente con la excepción base. La excepción pública tendrá más información que el que se proporciona por <xref:System.Exception>, <xref:System.SystemException>, o <xref:System.ApplicationException>.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Hacer que la excepción pública o derive la excepción interna de una excepción pública que no sea <xref:System.Exception>, <xref:System.SystemException>, o <xref:System.ApplicationException>.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Suprimir un mensaje de esta regla si está seguro de que la excepción privada será detectada dentro de su propio ámbito interno de todos los casos.  
  
## <a name="example"></a>Ejemplo  
 Esta regla se desencadena en el primer método de ejemplo, FirstCustomException porque la clase de excepción deriva directamente de Exception y es para uso interna. La regla se desencadena en la clase SecondCustomException porque aunque la clase también deriva directamente de Exception, la clase se ha declarado pública. La tercera clase tampoco desencadena la regla porque no se deriva directamente de <xref:System.Exception?displayProperty=fullName>, <xref:System.SystemException?displayProperty=fullName>, o <xref:System.ApplicationException?displayProperty=fullName>.  
  
 [!code-csharp[FxCop.Design.ExceptionsShouldBePublic.CA1064#1](../code-quality/codesnippet/CSharp/ca1064-exceptions-should-be-public_1.cs)]
