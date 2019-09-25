---
title: 'CA2002: No bloquear objetos con identidad débil'
ms.date: 01/31/2018
ms.topic: reference
f1_keywords:
- DoNotLockOnObjectsWithWeakIdentity
- CA2002
helpviewer_keywords:
- CA2002
- DoNotLockOnObjectsWithWeakIdentity
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: fc4504e917daeadc93963c6d6870c00515a5065a
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233162"
---
# <a name="ca2002-do-not-lock-on-objects-with-weak-identity"></a>CA2002: No bloquear objetos con identidad débil

|||
|-|-|
|TypeName|DoNotLockOnObjectsWithWeakIdentity|
|Identificador de comprobación|CA2002|
|Categoría|Microsoft.Reliability|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

Un subproceso intenta adquirir un bloqueo en un objeto que tiene una identidad débil.

## <a name="rule-description"></a>Descripción de la regla

Se dice que un objeto tiene una identidad débil cuando se puede tener acceso directamente a través de los límites del dominio de aplicación. Un subproceso que intenta obtener un bloqueo en un objeto que tiene identidad débil se puede bloquear con un segundo subproceso en un dominio de aplicación diferente que tenga bloqueado el mismo objeto.

Los tipos siguientes tienen una identidad débil y están marcados por la regla:

- <xref:System.String>

- Matrices de tipos de valor, incluidos los [tipos enteros](/dotnet/csharp/language-reference/keywords/integral-types-table), los [tipos de punto flotante](/dotnet/csharp/language-reference/keywords/floating-point-types-table)y <xref:System.Boolean>.

- <xref:System.MarshalByRefObject>

- <xref:System.ExecutionEngineException>

- <xref:System.OutOfMemoryException>

- <xref:System.StackOverflowException>

- <xref:System.Reflection.MemberInfo>

- <xref:System.Reflection.ParameterInfo>

- <xref:System.Threading.Thread>

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, use un objeto de un tipo que no esté en la lista de la sección Descripción.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

No suprima las advertencias de esta regla.

## <a name="related-rules"></a>Reglas relacionadas

[CA2213: los campos descartables deben ser descartables](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestran algunos bloqueos de objetos que infringen la regla.

[!code-vb[FxCop.Reliability.LockWeakObjects#1](../code-quality/codesnippet/VisualBasic/ca2002-do-not-lock-on-objects-with-weak-identity_1.vb)]
[!code-csharp[FxCop.Reliability.LockWeakObjects#1](../code-quality/codesnippet/CSharp/ca2002-do-not-lock-on-objects-with-weak-identity_1.cs)]

## <a name="see-also"></a>Vea también

- <xref:System.Threading.Monitor>
- <xref:System.AppDomain>
- [Lock (instrucciónC#) ()](/dotnet/csharp/language-reference/keywords/lock-statement)
- [Instrucción SyncLock (Visual Basic)](/dotnet/visual-basic/language-reference/statements/synclock-statement)