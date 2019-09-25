---
title: 'CA2102: Detectar las excepciones que no son CLSCompliant en los controladores generales'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords:
- CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f62ad97bbb96f49a7263edd29f0f8a7c263bec4c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233011"
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102: Detectar las excepciones que no son CLSCompliant en los controladores generales

|||
|-|-|
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|
|Identificador de comprobación|CA2102|
|Categoría|Microsoft.Security|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

Un miembro de un ensamblado que no está marcado con <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> o está marcado `RuntimeCompatibility(WrapNonExceptionThrows = false)` contiene un bloque catch que controla <xref:System.Exception?displayProperty=fullName> y no contiene un bloque catch general inmediatamente después. Esta regla omite [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] los ensamblados.

## <a name="rule-description"></a>Descripción de la regla

Un bloque catch que controla <xref:System.Exception> todas las excepciones conformes A Common Language Specification (CLS). Sin embargo, no detecta excepciones no conformes a CLS. Las excepciones no conformes a CLS se pueden iniciar desde código nativo o desde código administrado generado por el ensamblador de lenguaje intermedio de Microsoft (MSIL). Tenga en cuenta C# que [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] los compiladores y no permiten que se produzcan excepciones no conformes [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] a CLS y no detectan excepciones no conformes a CLS. Si la intención del bloque catch es controlar todas las excepciones, use la siguiente sintaxis de bloque catch general.

- C#: `catch {}`

- C++: `catch(...) {}` o`catch(Object^) {}`

Una excepción no controlada no conforme a CLS se convierte en un problema de seguridad cuando se quitan los permisos previamente permitidos en el bloque catch. Dado que no se detectan excepciones no conformes a CLS, un método malintencionado que produce una excepción no conforme a CLS podría ejecutarse con permisos elevados.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla cuando la intención es detectar todas las excepciones, sustituya o agregue un bloque catch general o marque `RuntimeCompatibility(WrapNonExceptionThrows = true)`el ensamblado. Si se quitan permisos en el bloque catch, duplique la funcionalidad en el bloque catch general. Si no es el objetivo de controlar todas las excepciones, reemplace el bloque catch que controla <xref:System.Exception> los bloques catch que controlan los tipos de excepción específicos.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Es seguro suprimir una advertencia de esta regla si el bloque try no contiene instrucciones que puedan generar una excepción no conforme a CLS. Dado que cualquier código nativo o administrado podría producir una excepción no conforme a CLS, es necesario conocer todo el código que se puede ejecutar en todas las rutas de acceso de código dentro del bloque try. Tenga en cuenta que las excepciones no conformes a CLS no se producen en el Common Language Runtime.

## <a name="example-1"></a>Ejemplo 1

En el ejemplo siguiente se muestra una clase MSIL que produce una excepción no conforme a CLS.

```cpp
.assembly ThrowNonClsCompliantException {}
.class public auto ansi beforefieldinit ThrowsExceptions
{
   .method public hidebysig static void
         ThrowNonClsException() cil managed
   {
      .maxstack  1
      IL_0000:  newobj     instance void [mscorlib]System.Object::.ctor()
      IL_0005:  throw
   }
}
```

## <a name="example-2"></a>Ejemplo 2

En el ejemplo siguiente se muestra un método que contiene un bloque catch general que cumple la regla.

[!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../code-quality/codesnippet/CSharp/ca2102-catch-non-clscompliant-exceptions-in-general-handlers_1.cs)]

Compile los ejemplos anteriores como se indica a continuación.

```cpp
ilasm /dll ThrowNonClsCompliantException.il
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs
```

## <a name="related-rules"></a>Reglas relacionadas

[CA1031: No detectar tipos de excepción general](../code-quality/ca1031-do-not-catch-general-exception-types.md)

## <a name="see-also"></a>Vea también

- [Excepciones y control de excepciones](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling)
- [Ilasm.exe (Ensamblador de IL)](/dotnet/framework/tools/ilasm-exe-il-assembler)
- [Independencia del lenguaje y componentes independientes del lenguaje](/dotnet/standard/language-independence-and-language-independent-components)