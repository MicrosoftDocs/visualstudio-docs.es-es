---
title: 'CA1410: Los métodos de registro COM deben coincidir'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
helpviewer_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: bca9e06c861ab2bcaceead8bf8ee195b64e45c83
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234733"
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410: Los métodos de registro COM deben coincidir

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldBeMatched|
|Identificador de comprobación|CA1410|
|Categoría|Microsoft.Interoperability|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

Un tipo declara un método que está marcado con el <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> atributo, pero no declara un método marcado con el <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> atributo, o viceversa.

## <a name="rule-description"></a>Descripción de la regla

Para que los clientes del modelo de objetos componentes (COM) creen un tipo .NET, primero se debe registrar el tipo. Si está disponible, se llama a un método marcado con el <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> atributo durante el proceso de registro para ejecutar el código especificado por el usuario. Un método correspondiente marcado con el <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> atributo se llama durante el proceso de anulación del registro para invertir las operaciones del método de registro.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, agregue el método de registro o anulación de registro correspondiente.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra un tipo que infringe la regla. El código comentado muestra la corrección de la infracción.

[!code-csharp[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/CSharp/ca1410-com-registration-methods-should-be-matched_1.cs)]
[!code-vb[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/VisualBasic/ca1410-com-registration-methods-should-be-matched_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas

[CA1411: Los métodos de registro COM no deben ser visibles](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)

## <a name="see-also"></a>Vea también

- <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>
- [Registrar ensamblados con COM](/dotnet/framework/interop/registering-assemblies-with-com)
- [Regasm.exe (Herramienta de registro de ensamblados)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)