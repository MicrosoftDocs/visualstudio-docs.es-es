---
title: 'CA2102: detectar las excepciones que no son CLSCompliant en los controladores generales | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords:
- CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e2335b6d2bc3a5e99f0e6de1afefac4f42de0501
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85521308"
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102: Detectar las excepciones que no son CLSCompliant en los controladores generales
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Valor|
|-|-|
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|
|Identificador de comprobación|CA2102|
|Categoría|Microsoft.Security|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
 Un miembro de un ensamblado que no está marcado con <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> o está marcado `RuntimeCompatibility(WrapNonExceptionThrows = false)` contiene un bloque catch que controla <xref:System.Exception?displayProperty=fullName> y no contiene un bloque catch general inmediatamente después. Esta regla omite los [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ensamblados.

## <a name="rule-description"></a>Descripción de la regla
 Un bloque catch que controla <xref:System.Exception> todas las excepciones conformes A Common Language Specification (CLS). Sin embargo, no detecta excepciones no conformes a CLS. Las excepciones no conformes a CLS se pueden iniciar desde código nativo o desde código administrado generado por el ensamblador de lenguaje intermedio de Microsoft (MSIL). Tenga en cuenta que los [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] compiladores de C# y no permiten que se inicien excepciones no conformes a CLS y no [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] detectan excepciones no conformes a CLS. Si la intención del bloque catch es controlar todas las excepciones, use la siguiente sintaxis de bloque catch general.

- C#: `catch {}`

- C++: `catch(...) {}` o`catch(Object^) {}`

  Una excepción no controlada no conforme a CLS se convierte en un problema de seguridad cuando se quitan los permisos previamente permitidos en el bloque catch. Dado que no se detectan excepciones no conformes a CLS, un método malintencionado que produce una excepción no conforme a CLS podría ejecutarse con permisos elevados.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla cuando la intención es detectar todas las excepciones, sustituya o agregue un bloque catch general o marque el ensamblado `RuntimeCompatibility(WrapNonExceptionThrows = true)` . Si se quitan permisos en el bloque catch, duplique la funcionalidad en el bloque catch general. Si no es el objetivo de controlar todas las excepciones, reemplace el bloque catch que controla los <xref:System.Exception> bloques catch que controlan los tipos de excepción específicos.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el bloque try no contiene instrucciones que puedan generar una excepción no conforme a CLS. Dado que cualquier código nativo o administrado podría producir una excepción no conforme a CLS, es necesario conocer todo el código que se puede ejecutar en todas las rutas de acceso de código dentro del bloque try. Tenga en cuenta que las excepciones no conformes a CLS no se producen en el Common Language Runtime.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra una clase MSIL que produce una excepción no conforme a CLS.

```
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

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un método que contiene un bloque catch general que cumple la regla.

 [!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.CatchNonClsCompliantException/cs/FxCop.Security.CatchNonClsCompliantException.cs#1)]

 Compile los ejemplos anteriores como se indica a continuación.

```
ilasm /dll ThrowNonClsCompliantException.il
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs
```

## <a name="related-rules"></a>Reglas relacionadas
 [CA1031: No capturar los tipos de excepción general](../code-quality/ca1031-do-not-catch-general-exception-types.md)

## <a name="see-also"></a>Consulte también
 [Excepciones y control de](https://msdn.microsoft.com/library/0001887f-4fa2-47e2-8034-2819477e2344) excepciones [Ilasm.exe (ensamblador de IL)](https://msdn.microsoft.com/library/4ca3a4f0-4400-47ce-8936-8e219961c76f) [reemplazar seguridad comprueba](https://msdn.microsoft.com/4acdeff5-fc05-41bf-8505-7387cdbfca28) [la independencia del lenguaje y los componentes independientes del lenguaje](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
