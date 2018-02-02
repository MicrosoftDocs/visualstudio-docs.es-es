---
title: "CA2002: No bloquear objetos con identidad débil | Documentos de Microsoft"
ms.custom: 
ms.date: 01/31/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.topic: article
f1_keywords:
- DoNotLockOnObjectsWithWeakIdentity
- CA2002
helpviewer_keywords:
- CA2002
- DoNotLockOnObjectsWithWeakIdentity
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e27af6104b06b1f6a01ae6a98bfe88e8a0e967b1
ms.sourcegitcommit: ba29e4d37db92ec784d4acf9c6e120cf0ea677e9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2018
---
# <a name="ca2002-do-not-lock-on-objects-with-weak-identity"></a>CA2002: No bloquear objetos con identidad débil

|||
|-|-|
|TypeName|DoNotLockOnObjectsWithWeakIdentity|
|Identificador de comprobación|CA2002|
|Categoría|Microsoft.Reliability|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo

Un subproceso intenta adquirir un bloqueo en un objeto que tiene identidad débil.

## <a name="rule-description"></a>Descripción de la regla

Se dice que un objeto tiene una identidad débil cuando se puede tener acceso directamente a través de los límites del dominio de aplicación. Un subproceso que intenta obtener un bloqueo en un objeto que tiene identidad débil se puede bloquear con un segundo subproceso en un dominio de aplicación diferente que tenga bloqueado el mismo objeto.

Los siguientes tipos tienen una identidad débil y se marcan mediante la regla:

- <xref:System.String>

- Matrices de tipos de valor, incluidos los [tipos integrales](/dotnet/csharp/language-reference/keywords/integral-types-table), [tipos de punto flotante](/dotnet/csharp/language-reference/keywords/floating-point-types-table), y <xref:System.Boolean>.

- <xref:System.MarshalByRefObject>

- <xref:System.ExecutionEngineException>

- <xref:System.OutOfMemoryException>

- <xref:System.StackOverflowException>

- <xref:System.Reflection.MemberInfo>

- <xref:System.Reflection.ParameterInfo>

- <xref:System.Threading.Thread>

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, utilice un objeto de un tipo que no está en la lista en la sección de descripción.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

No suprima las advertencias de esta regla.

## <a name="related-rules"></a>Reglas relacionadas

[CA2213: Aplique Dispose a los campos a los que se pueda](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra algunos bloqueos de objeto que infringen la regla.

[!code-vb[FxCop.Reliability.LockWeakObjects#1](../code-quality/codesnippet/VisualBasic/ca2002-do-not-lock-on-objects-with-weak-identity_1.vb)]
[!code-csharp[FxCop.Reliability.LockWeakObjects#1](../code-quality/codesnippet/CSharp/ca2002-do-not-lock-on-objects-with-weak-identity_1.cs)]

## <a name="see-also"></a>Vea también

<xref:System.Threading.Monitor>  
<xref:System.AppDomain>  
[lock (instrucción) (C#)](/dotnet/csharp/language-reference/keywords/lock-statement)  
[SyncLock (instrucción) (Visual Basic)](/dotnet/visual-basic/language-reference/statements/synclock-statement)