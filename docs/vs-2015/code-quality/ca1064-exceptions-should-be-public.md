---
title: 'CA1064: Las excepciones deben ser públicas | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1064
- ExceptionsShouldBePublic
helpviewer_keywords:
- ExceptionsShouldBePublic
- CA1064
ms.assetid: 83eb224c-2456-4368-acf4-3b3378e67759
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 00d188188f722907c2bac20e84cb9291ef8bc0fe
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200426"
---
# <a name="ca1064-exceptions-should-be-public"></a>CA1064: Las excepciones deben ser públicas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ExceptionsShouldBePublic|
|Identificador de comprobación|CA1064|
|Categoría|Microsoft.Design|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa
 Una excepción no pública se deriva directamente de <xref:System.Exception>, <xref:System.SystemException>, o <xref:System.ApplicationException>.

## <a name="rule-description"></a>Descripción de la regla
 Una excepción interna solo está visible dentro de su propio ámbito interno. Cuando la excepción esté fuera del ámbito interno, sólo se podrá usar la excepción base para detectarla. Si la excepción interna se hereda de <xref:System.Exception>, <xref:System.SystemException>, o <xref:System.ApplicationException>, el código externo no tendrá información suficiente para saber qué hacer con la excepción.

 Pero, si el código tiene una excepción pública que más adelante se utiliza como base para una excepción interna, es razonable suponer que el código más out será capaz de hacer algo inteligente con la excepción base. La excepción pública tendrá más información que lo que proporciona Exception, SystemException y ApplicationException.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Hacer pública la excepción o derive la excepción interna de una excepción pública que no sea <xref:System.Exception>, <xref:System.SystemException>, o <xref:System.ApplicationException>.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprimir un mensaje de esta regla si está seguro de todos los casos que detectará la excepción privada dentro de su propio ámbito interno.

## <a name="example"></a>Ejemplo
 Esta regla se desencadena en el primer método de ejemplo, FirstCustomException porque la clase de excepción se deriva directamente de la excepción y es interna. La regla se desencadena en la clase SecondCustomException porque aunque la clase también se deriva directamente de excepción, la clase se ha declarado pública. La tercera clase también desencadena la regla porque no se deriva directamente de <xref:System.Exception?displayProperty=fullName>, <xref:System.SystemException?displayProperty=fullName>, o <xref:System.ApplicationException?displayProperty=fullName>.

 [!code-csharp[FxCop.Design.ExceptionsShouldBePublic.CA1064#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.design.exceptionsshouldbepublic.ca1064/cs/ca1064 - exceptionsshouldbepublic.cs#1)]
