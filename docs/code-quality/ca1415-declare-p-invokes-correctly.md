---
title: 'CA1415: Declarar elementos P-Invoke correctamente'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1415
- DeclarePInvokesCorrectly
helpviewer_keywords:
- CA1415
- DeclarePInvokesCorrectly
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5cc12d5d0a62f8d2530f13fcf860aba4e118ca4
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921850"
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415: Declarar elementos P/Invoke correctamente

|||
|-|-|
|TypeName|DeclarePInvokesCorrectly|
|Identificador de comprobación|CA1415|
|Categoría|Microsoft.Interoperability|
|Cambio problemático|No problemático: Si la P/Invoke que declara el parámetro no se puede considerar fuera del ensamblado. Interrumpir: Si la P/Invoke que declara el parámetro puede verse fuera del ensamblado.|

## <a name="cause"></a>Causa
No se ha declarado correctamente un método de invocación de plataforma.

## <a name="rule-description"></a>Descripción de la regla
Un método de invocación de plataforma tiene acceso al código no administrado y se define `Declare` mediante la [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] palabra clave <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>en o. Actualmente, esta regla busca declaraciones de método de invocación de plataforma que tienen como destino funciones de Win32 que tienen un puntero a un parámetro de estructura superpuesto y el parámetro administrado <xref:System.Threading.NativeOverlapped?displayProperty=fullName> correspondiente no es un puntero a una estructura.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, declare correctamente el método de invocación de plataforma.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestran métodos de invocación de plataforma que infringen la regla y satisfacen la regla.

[!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../code-quality/codesnippet/CSharp/ca1415-declare-p-invokes-correctly_1.cs)]

## <a name="see-also"></a>Vea también
[Interoperating with Unmanaged Code](/dotnet/framework/interop/index) (Interoperar con código no administrado)