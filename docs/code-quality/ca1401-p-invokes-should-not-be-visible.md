---
title: 'CA1401: Los elementos P-Invoke no deben estar visibles'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PInvokesShouldNotBeVisible
- CA1401
helpviewer_keywords:
- CA1401
- PInvokesShouldNotBeVisible
ms.assetid: 0f4d96c1-f9de-414e-b223-4dc7f691bee3
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e26daf68e0031358605427b310bb7284d43baf1b
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922134"
---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401: Los elementos P/Invoke no deben estar visibles

|||
|-|-|
|TypeName|PInvokesShouldNotBeVisible|
|Identificador de comprobación|CA1401|
|Categoría|Microsoft.Interoperability|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
Un método público o protegido en un tipo público tiene el <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> atributo (también implementado por `Declare` la palabra [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]clave en).

## <a name="rule-description"></a>Descripción de la regla
Los métodos marcados con el <xref:System.Runtime.InteropServices.DllImportAttribute> atributo (o métodos que se definen mediante la `Declare` palabra clave en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) usan servicios de invocación de plataforma para tener acceso a código no administrado. No se deberían exponer estos métodos. Al mantener estos métodos en privado o interno, asegúrese de que la biblioteca no se puede usar para infringir la seguridad permitiendo que los llamadores tengan acceso a las API no administradas que no podían llamar de otra manera.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, cambie el nivel de acceso del método.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se declara un método que infringe esta regla.

[!code-vb[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/VisualBasic/ca1401-p-invokes-should-not-be-visible_1.vb)]
[!code-csharp[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/CSharp/ca1401-p-invokes-should-not-be-visible_1.cs)]