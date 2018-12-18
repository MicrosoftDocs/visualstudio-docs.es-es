---
title: 'CA1415: Declare los elementos P/Invoke correctamente'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f95c3e68190acbd53c4b75ceb81abf2885d15bce
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49922632"
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415: Declare los elementos P/Invoke correctamente

|||
|-|-|
|TypeName|DeclarePInvokesCorrectly|
|Identificador de comprobación|CA1415|
|Categoría|Microsoft.Interoperability|
|Cambio problemático|No problemático: si el valor de P/Invoke que declara el parámetro no puede verse fuera del ensamblado. Problemático: si P/Invoke que declara el parámetro puede verse fuera del ensamblado.|

## <a name="cause"></a>Motivo
 Una plataforma de invocación de método se ha declarado incorrectamente.

## <a name="rule-description"></a>Descripción de la regla
 Una plataforma de invocación de método tiene acceso al código no administrado y se define utilizando el `Declare` palabra clave en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] o <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. Actualmente, esta regla busca declaraciones de métodos que tienen como destino las funciones de Win32 que tienen un puntero a un parámetro de estructura OVERLAPPED de invocación de plataforma y el parámetro administrado correspondiente no es un puntero a un <xref:System.Threading.NativeOverlapped?displayProperty=fullName> estructura.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, debe declarar correctamente la plataforma de invocación de método.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra los métodos que infringen la regla y que cumplen la regla de invocación de plataforma.

 [!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../code-quality/codesnippet/CSharp/ca1415-declare-p-invokes-correctly_1.cs)]

## <a name="see-also"></a>Vea también
 [Interoperating with Unmanaged Code](/dotnet/framework/interop/index) (Interoperar con código no administrado)