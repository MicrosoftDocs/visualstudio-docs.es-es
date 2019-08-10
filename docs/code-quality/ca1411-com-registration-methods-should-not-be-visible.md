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
ms.openlocfilehash: 4f6f40308255e0496b2bcccddf4299e83ea93100
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922049"
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411: Los métodos de registro COM no deben ser visibles

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldNotBeVisible|
|Identificador de comprobación|CA1411|
|Categoría|Microsoft.Interoperability|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa

Un método marcado con el <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> atributo o es visible externamente.

## <a name="rule-description"></a>Descripción de la regla
Cuando un ensamblado se registra con el modelo de objetos componentes (COM), las entradas se agregan al registro para cada tipo visible para COM en el ensamblado. Los métodos marcados con los <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> atributos <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> y se llaman durante los procesos de registro y anulación de registro, respectivamente, para ejecutar código de usuario específico del registro o anulación del registro de estos tipos. No se debe llamar a este código fuera de estos procesos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, cambie la accesibilidad del método a `private` o `internal` (`Friend` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestran dos métodos que infringen la regla.

[!code-csharp[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/CSharp/ca1411-com-registration-methods-should-not-be-visible_1.cs)]
[!code-vb[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/VisualBasic/ca1411-com-registration-methods-should-not-be-visible_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas
[CA1410: Se debe coincidir con los métodos de registro COM](../code-quality/ca1410-com-registration-methods-should-be-matched.md)

## <a name="see-also"></a>Vea también

- <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>
- [Registrar ensamblados con COM](/dotnet/framework/interop/registering-assemblies-with-com)
- [Regasm.exe (Herramienta de registro de ensamblados)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)