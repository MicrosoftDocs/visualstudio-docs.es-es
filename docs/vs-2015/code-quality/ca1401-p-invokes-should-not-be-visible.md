---
title: 'CA1401: P-Invokes no debe estar visible | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PInvokesShouldNotBeVisible
- CA1401
helpviewer_keywords:
- CA1401
- PInvokesShouldNotBeVisible
ms.assetid: 0f4d96c1-f9de-414e-b223-4dc7f691bee3
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f3f867f14f7a2eca4482f1f8d5fb48149f02f43f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661359"
---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401: Los elementos P/Invoke no deben estar visibles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PInvokesShouldNotBeVisible|
|Identificador de comprobación|CA1401|
|Categoría|Microsoft. Interoperability|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método público o protegido en un tipo público tiene el <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> atributo (también implementado por la palabra clave `Declare` en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).

## <a name="rule-description"></a>Descripción de la regla
 Los métodos marcados con el atributo <xref:System.Runtime.InteropServices.DllImportAttribute> (o los métodos que se definen mediante la palabra clave `Declare` en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) utilizan los servicios de invocación de plataforma para tener acceso a código no administrado. No se deberían exponer estos métodos. Al mantener estos métodos en privado o interno, asegúrese de que la biblioteca no se puede usar para infringir la seguridad permitiendo que los llamadores tengan acceso a las API no administradas que no podían llamar de otra manera.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie el nivel de acceso del método.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se declara un método que infringe esta regla.

 [!code-csharp[FxCop.Interoperability.DllImports#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DllImports/cs/FxCop.Interoperability.DllImports.cs#1)]
 [!code-vb[FxCop.Interoperability.DllImports#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DllImports/vb/FxCop.Interoperability.DllImports.vb#1)]
