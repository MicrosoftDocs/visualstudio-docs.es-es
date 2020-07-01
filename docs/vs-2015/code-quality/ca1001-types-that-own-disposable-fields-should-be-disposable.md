---
title: 'CA1001: los tipos que poseen campos descartables deben ser descartables | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
helpviewer_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: dab4532f082bd81eaa7b812eb038c5957636d453
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548322"
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001: Los tipos que poseen campos descartables deben ser descartables
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|
|Identificador de comprobación|CA1001|
|Category|Microsoft. Design|
|Cambio problemático|No problemático: Si el tipo no es visible fuera del ensamblado.<br /><br /> Interrumpir: Si el tipo es visible fuera del ensamblado.|

## <a name="cause"></a>Causa
 Una clase declara e implementa un campo de instancia que es un <xref:System.IDisposable?displayProperty=fullName> tipo y la clase no implementa <xref:System.IDisposable> .

## <a name="rule-description"></a>Descripción de la regla
 Una clase implementa la <xref:System.IDisposable> interfaz para desechar los recursos no administrados que posee. Un campo de instancia que es un <xref:System.IDisposable> tipo indica que el campo posee un recurso no administrado. Una clase que declara un <xref:System.IDisposable> campo posee indirectamente un recurso no administrado y debe implementar la <xref:System.IDisposable> interfaz. Si la clase no posee directamente ningún recurso no administrado, no debe implementar un finalizador.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, implemente <xref:System.IDisposable> y desde el <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> método, llame al <xref:System.IDisposable.Dispose%2A> método del campo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra una clase que infringe la regla y una clase que satisface la regla implementando <xref:System.IDisposable> . La clase no implementa un finalizador porque la clase no posee directamente ningún recurso no administrado.

 [!code-csharp[FxCop.Design.DisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.DisposableFields/cs/FxCop.Design.DisposableFields.cs#1)]
 [!code-vb[FxCop.Design.DisposableFields#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DisposableFields/vb/FxCop.Design.DisposableFields.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2213: Los campos descartables deben ser descartables](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

 [CA2216: Los tipos descartables deben declarar el finalizador](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA2215: Los métodos Dispose deben llamar al método Dispose de la clase base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA1049: Los tipos que poseen recursos nativos deben ser descartables](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)
