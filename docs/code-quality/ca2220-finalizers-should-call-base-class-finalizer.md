---
title: 'CA2220: Los finalizadores deben llamar al finalizador de la clase base'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e5af6b7872f0fa05183334e6acd2bc4922f84990
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231162"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: Los finalizadores deben llamar al finalizador de la clase base

|||
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|Identificador de comprobación|CA2220|
|Categoría|Microsoft.Usage|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

Un tipo que invalida <xref:System.Object.Finalize%2A?displayProperty=fullName> no llama al <xref:System.Object.Finalize%2A> método en su clase base.

## <a name="rule-description"></a>Descripción de la regla

La finalización se debe difundir a través de la jerarquía de herencia. Para garantizar esto, los tipos deben llamar a su <xref:System.Object.Finalize%2A> método de clase base desde <xref:System.Object.Finalize%2A> dentro de su propio método. El C# compilador agrega la llamada al finalizador de la clase base automáticamente.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, llame al método del <xref:System.Object.Finalize%2A> tipo base desde <xref:System.Object.Finalize%2A> su método.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

No suprima las advertencias de esta regla. Algunos compiladores que tienen como destino el Common Language Runtime insertar una llamada al finalizador del tipo base en el lenguaje intermedio de Microsoft (MSIL). Si se indica una advertencia de esta regla, el compilador no inserta la llamada y debe agregarla al código.

## <a name="example"></a>Ejemplo

En el siguiente ejemplo de Visual Basic se `TypeB` muestra un tipo que <xref:System.Object.Finalize%2A> llama correctamente al método en su clase base.

[!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]

## <a name="see-also"></a>Vea también

- [Patrón de Dispose](/dotnet/standard/design-guidelines/dispose-pattern)