---
title: 'CA1001: Los tipos que poseen campos descartables deben ser descartables'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
helpviewer_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: fae67f8c1ffa3b4e6d7cc2f0fbbaf670733f9ff4
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923310"
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001: Los tipos que poseen campos descartables deben ser descartables

|||
|-|-|
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|
|Identificador de comprobación|CA1001|
|Categoría|Microsoft.Design|
|Cambio problemático|No problemático: Si el tipo no es visible fuera del ensamblado.<br /><br /> Interrumpir: Si el tipo es visible fuera del ensamblado.|

## <a name="cause"></a>Causa
Una clase declara e implementa un campo de instancia que es un <xref:System.IDisposable?displayProperty=fullName> tipo y la clase no implementa. <xref:System.IDisposable>

## <a name="rule-description"></a>Descripción de la regla
Una clase implementa la <xref:System.IDisposable> interfaz para desechar los recursos no administrados que posee. Un campo de instancia que es <xref:System.IDisposable> un tipo indica que el campo posee un recurso no administrado. Una clase que declara un <xref:System.IDisposable> campo posee indirectamente un recurso no administrado y debe implementar la <xref:System.IDisposable> interfaz. Si la clase no posee directamente ningún recurso no administrado, no debe implementar un finalizador.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, <xref:System.IDisposable> implemente y <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> desde el método <xref:System.IDisposable.Dispose%2A> , llame al método del campo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra una clase que infringe la regla y una clase que satisface la regla implementando <xref:System.IDisposable>. La clase no implementa un finalizador porque la clase no posee directamente ningún recurso no administrado.

[!code-vb[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/VisualBasic/ca1001-types-that-own-disposable-fields-should-be-disposable_1.vb)]
[!code-csharp[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/CSharp/ca1001-types-that-own-disposable-fields-should-be-disposable_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas
[CA2213: los campos descartables deben ser descartables](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

[CA2216: Los tipos descartables deben declarar el finalizador](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

[CA2215 Los métodos Dispose deben llamar a Dispose de la clase base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

[CA1049: Los tipos que poseen recursos nativos deben ser descartables](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)