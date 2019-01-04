---
title: 'CA2102: Detectar las excepciones que no son CLSCompliant en los controladores generales'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords:
- CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: de5bb494822b2faabce0bdf8a3b2a1e2e9a80b99
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53840400"
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102: Detectar las excepciones que no son CLSCompliant en los controladores generales

|||
|-|-|
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|
|Identificador de comprobación|CA2102|
|Categoría|Microsoft.Security|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo

Un miembro de un ensamblado que no está marcado con el <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> o está marcado como `RuntimeCompatibility(WrapNonExceptionThrows = false)` contiene un bloque catch que controla <xref:System.Exception?displayProperty=fullName> y no contiene un bloque catch general inmediatamente después. Esta regla omite [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ensamblados.

## <a name="rule-description"></a>Descripción de la regla

Un bloque catch que controla <xref:System.Exception> detecta todas las excepciones compatible con Common Language Specification (CLS). Sin embargo, no detecta excepciones conforme a CLS. No conforme a CLS pueden producir excepciones compatibles desde código nativo o desde código administrado generado por Microsoft lenguaje intermedio (MSIL) ensamblador. Tenga en cuenta que C# y [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compiladores no permiten que no son conformes a CLS que se produzcan excepciones conformes y [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] no detecta excepciones conforme a CLS. Si es la intención del bloque catch controlar todas las excepciones, use la siguiente sintaxis del bloque catch general.

- C#: `catch {}`

- C++: `catch(...) {}` o `catch(Object^) {}`

Una excepción conforme no controlada que no son conformes a CLS se convierte en un problema de seguridad cuando se quitan los permisos concedidos previamente en el bloque catch. Dado que no se detectan excepciones conforme a CLS, podría ejecutar un método malintencionado que excepción no conforme a CLS conforme con permisos elevados.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla cuando la intención es capturar todas las excepciones, sustituya o agregue un bloque catch general o marque el ensamblado `RuntimeCompatibility(WrapNonExceptionThrows = true)`. Si se quitan los permisos en el bloque catch, duplicados en general la funcionalidad de bloque catch. Si no es la intención de controlar todas las excepciones, reemplace el bloque catch que controla <xref:System.Exception> con bloques catch que controlan los tipos de excepción específica.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Es seguro suprimir una advertencia de esta regla si el bloque try no contiene ninguna instrucción que podría generar una excepción conforme a CLS. Dado que cualquier código nativo o administrado es posible que la excepción no conforme a CLS conforme, esto requiere el conocimiento de todo el código que se puede ejecutar en todas las rutas de código dentro del bloque try. Tenga en cuenta que common language runtime no inicia excepciones conforme a CLS.

## <a name="example-1"></a>Ejemplo 1

El ejemplo siguiente muestra una clase MSIL que se produce una excepción conforme a CLS.

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

El ejemplo siguiente muestra un método que contiene un bloque catch general que cumple la regla.

[!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../code-quality/codesnippet/CSharp/ca2102-catch-non-clscompliant-exceptions-in-general-handlers_1.cs)]

Compile los ejemplos anteriores como sigue.

```cpp
ilasm /dll ThrowNonClsCompliantException.il
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs
```

## <a name="related-rules"></a>Reglas relacionadas

[CA1031: No capturar los tipos de excepción general](../code-quality/ca1031-do-not-catch-general-exception-types.md)

## <a name="see-also"></a>Vea también

- [Excepciones y control de excepciones](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling)
- [Ilasm.exe (Ensamblador de IL)](/dotnet/framework/tools/ilasm-exe-il-assembler)
- [Independencia del lenguaje y componentes independientes del lenguaje](/dotnet/standard/language-independence-and-language-independent-components)