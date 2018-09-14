---
title: 'CA1401: Los elementos P/Invoke no deben estar visibles'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 9c1d4d9cc5e1550dee87609e5ef0e99dcd9d0cf5
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548632"
---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401: Los elementos P/Invoke no deben estar visibles

|||
|-|-|
|TypeName|PInvokesShouldNotBeVisible|
|Identificador de comprobación|CA1401|
|Categoría|Microsoft.Interoperability|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método público o protegido en un tipo público tiene el <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> atributo (también se implementa por la `Declare` palabra clave en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

## <a name="rule-description"></a>Descripción de la regla
 Los métodos marcados con el <xref:System.Runtime.InteropServices.DllImportAttribute> atributo (o métodos que se definen mediante la `Declare` palabra clave en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) usar servicios de invocación de plataforma para tener acceso a código no administrado. No se deberían exponer estos métodos. Al mantener estos métodos privados o internos, se asegura de que no se puede usar la biblioteca de infringir la seguridad al permitir el acceso a las API no administradas que no puede llamar en caso contrario, los autores de llamadas.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie el nivel de acceso del método.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente declara un método que infringe esta regla.

 [!code-vb[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/VisualBasic/ca1401-p-invokes-should-not-be-visible_1.vb)]
 [!code-csharp[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/CSharp/ca1401-p-invokes-should-not-be-visible_1.cs)]