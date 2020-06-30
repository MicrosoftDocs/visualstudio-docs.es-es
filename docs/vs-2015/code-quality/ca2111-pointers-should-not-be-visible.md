---
title: 'CA2111: los punteros no deben ser visibles | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PointersShouldNotBeVisible
- CA2111
helpviewer_keywords:
- CA2111
- PointersShouldNotBeVisible
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7429251a66ce2fe22a825a153cb90248faabb9fd
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544370"
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111: Los punteros no deben estar visibles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|PointersShouldNotBeVisible|
|Identificador de comprobación|CA2111|
|Category|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Un campo público o protegido <xref:System.IntPtr?displayProperty=fullName> o <xref:System.UIntPtr?displayProperty=fullName> no es de solo lectura.

## <a name="rule-description"></a>Descripción de la regla
 <xref:System.IntPtr>y <xref:System.UIntPtr> son tipos de puntero que se usan para tener acceso a la memoria no administrada. Si un puntero no es privado, interno o de solo lectura, el código malintencionado puede cambiar el valor del puntero, permitiendo potencialmente el acceso a ubicaciones arbitrarias en memoria o provocando errores del sistema o de la aplicación.

 Si desea proteger el acceso al tipo que contiene el campo de puntero, vea [CA2112: los tipos seguros no deben exponer los campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Proteja el puntero haciéndolo de solo lectura, interno o privado.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla si no se basa en el valor del puntero.

## <a name="example"></a>Ejemplo
 En el código siguiente se muestran punteros que infringen y satisfacen la regla. Observe que los punteros no privados también infringen la regla [CA1051: no declarar campos de instancia visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

 [!code-csharp[FxCop.Security.PointersArePrivate#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PointersArePrivate/cs/FxCop.Security.PointersArePrivate.cs#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2112: Los tipos seguros no deben exponer campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA1051: No declarar campos de instancia visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Consulte también
 <xref:System.IntPtr?displayProperty=fullName> <xref:System.UIntPtr?displayProperty=fullName>
