---
title: 'CA1411: Los métodos de registro COM no deben ser visibles'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1411
- ComRegistrationMethodsShouldNotBeVisible
helpviewer_keywords:
- ComRegistrationMethodsShouldNotBeVisible
- CA1411
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: bd721edab080de7708ac395e2a7d7e486c504fba
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55950661"
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411: Los métodos de registro COM no deben ser visibles

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldNotBeVisible|
|Identificador de comprobación|CA1411|
|Categoría|Microsoft.Interoperability|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo

Un método marcado con el <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> o <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> atributo es visible externamente.

## <a name="rule-description"></a>Descripción de la regla
 Cuando un ensamblado se registra con el modelo de objetos componentes (COM), se agregan entradas al registro para cada tipo COM-visible en el ensamblado. Los métodos marcados con el <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> y <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> atributos se denominan durante los procesos de registro y anulación del registro, respectivamente, para ejecutar código de usuario que es específico para el registro o anulación del registro de estos tipos. No se debe llamar a este código fuera de estos procesos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie la accesibilidad del método que `private` o `internal` (`Friend` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra dos métodos que infringen la regla.

 [!code-csharp[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/CSharp/ca1411-com-registration-methods-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/VisualBasic/ca1411-com-registration-methods-should-not-be-visible_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1410: Métodos de registro COM se deben asociar](../code-quality/ca1410-com-registration-methods-should-be-matched.md)

## <a name="see-also"></a>Vea también

- <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>
- [Registrar ensamblados con COM](/dotnet/framework/interop/registering-assemblies-with-com)
- [Regasm.exe (Herramienta de registro de ensamblados)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)