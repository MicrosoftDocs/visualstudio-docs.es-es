---
title: 'CA2111: Los punteros no deberían estar visibles | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- PointersShouldNotBeVisible
- CA2111
helpviewer_keywords:
- CA2111
- PointersShouldNotBeVisible
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0d96a71a27a235887fe1744bbee09027c2c6d434
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49888947"
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111: Los punteros no deberían estar visibles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PointersShouldNotBeVisible|
|Identificador de comprobación|CA2111|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un público o protegido <xref:System.IntPtr?displayProperty=fullName> o <xref:System.UIntPtr?displayProperty=fullName> campo no es de solo lectura.

## <a name="rule-description"></a>Descripción de la regla
 <xref:System.IntPtr> y <xref:System.UIntPtr> son tipos de puntero que se usan para tener acceso a memoria no administrada. Si un puntero no es privado, interno o de solo lectura, el código malintencionado puede cambiar el valor del puntero, potencialmente que permita el acceso a ubicaciones arbitrarias en memoria o provocando errores de aplicación o sistema.

 Si piensa proteger el acceso al tipo que contiene el campo de puntero, vea [CA2112: los tipos seguros no deberían exponer campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Proteja el puntero mediante la realización de solo lectura, interno o privado.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla si no confía en el valor del puntero.

## <a name="example"></a>Ejemplo
 El código siguiente muestra punteros que infringen y cumplen la regla. Tenga en cuenta que los punteros no privados también infringen la regla [CA1051: no declarar campos de instancia visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

 [!code-csharp[FxCop.Security.PointersArePrivate#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PointersArePrivate/cs/FxCop.Security.PointersArePrivate.cs#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2112: Los tipos seguros no deberían exponer campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA1051: No declarar campos de instancia visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Vea también
 <xref:System.IntPtr?displayProperty=fullName> <xref:System.UIntPtr?displayProperty=fullName>



