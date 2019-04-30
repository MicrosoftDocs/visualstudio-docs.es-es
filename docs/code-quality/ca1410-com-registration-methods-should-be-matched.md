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
ms.openlocfilehash: c606a55be00ac8e44d54bad289076498e2655af1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546419"
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410: Los métodos de registro COM deben coincidir

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldBeMatched|
|Identificador de comprobación|CA1410|
|Categoría|Microsoft.Interoperability|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un tipo declara un método marcado con el <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> atributo pero no declara un método marcado con el <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> atributo, o viceversa.

## <a name="rule-description"></a>Descripción de la regla
 Para que los clientes del modelo de objetos componentes (COM) crear un tipo de .NET Framework, el tipo debe registrarse primero. Si está disponible, un método marcado con el <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> atributo se denomina durante el proceso de registro para ejecutar el código especificado por el usuario. Un método correspondiente que está marcado con el <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> atributo se denomina durante el proceso de anulación del registro para revertir las operaciones del método de registro.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, agregue el método de anulación del registro o el registro correspondiente.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo que infringe la regla. El código comentado muestra la corrección de la infracción.

 [!code-csharp[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/CSharp/ca1410-com-registration-methods-should-be-matched_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/VisualBasic/ca1410-com-registration-methods-should-be-matched_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1411: Métodos de registro COM no deben ser visibles](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)

## <a name="see-also"></a>Vea también

- <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>
- [Registrar ensamblados con COM](/dotnet/framework/interop/registering-assemblies-with-com)
- [Regasm.exe (Herramienta de registro de ensamblados)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)