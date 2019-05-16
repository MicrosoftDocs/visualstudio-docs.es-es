---
title: 'CA2002: No bloquear objetos con identidad débil | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotLockOnObjectsWithWeakIdentity
- CA2002
helpviewer_keywords:
- CA2002
- DoNotLockOnObjectsWithWeakIdentity
ms.assetid: 16100b39-c6fc-452b-8fca-8b459a26c286
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 39d233c126d35f303a30a955310859dd9a678c56
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65681376"
---
# <a name="ca2002-do-not-lock-on-objects-with-weak-identity"></a>CA2002: No bloquear objetos con identidad débil
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotLockOnObjectsWithWeakIdentity|
|Identificador de comprobación|CA2002|
|Categoría|Microsoft.Reliability|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un subproceso intenta adquirir un bloqueo en un objeto que tiene identidad débil.

## <a name="rule-description"></a>Descripción de la regla
 Se dice que un objeto tiene una identidad débil cuando se puede tener acceso directamente a través de los límites del dominio de aplicación. Un subproceso que intenta obtener un bloqueo en un objeto que tiene identidad débil se puede bloquear con un segundo subproceso en un dominio de aplicación diferente que tenga bloqueado el mismo objeto. Los siguientes tipos tienen una identidad débil y se marcan mediante la regla:

- <xref:System.MarshalByRefObject>

- <xref:System.ExecutionEngineException>

- <xref:System.OutOfMemoryException>

- <xref:System.StackOverflowException>

- <xref:System.String>

- <xref:System.Reflection.MemberInfo>

- <xref:System.Reflection.ParameterInfo>

- <xref:System.Threading.Thread>

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, utilice un objeto de un tipo que no está en la lista en la sección de descripción.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="related-rules"></a>Reglas relacionadas
 [CA2213: los campos descartables deben ser descartables](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra algunos bloqueos de objeto que infringen la regla.

 [!code-csharp[FxCop.Reliability.LockWeakObjects#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Reliability.LockWeakObjects/cs/FxCop.Reliability.LockWeakObjects.cs#1)]
 [!code-vb[FxCop.Reliability.LockWeakObjects#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Reliability.LockWeakObjects/vb/FxCop.Reliability.LockWeakObjects.vb#1)]

## <a name="see-also"></a>Vea también
 <xref:System.Threading.Monitor> <xref:System.AppDomain>
 [lock (instrucción)](https://msdn.microsoft.com/library/656da1a4-707e-4ef6-9c6e-6d13b646af42) [SyncLock (instrucción)](https://msdn.microsoft.com/library/14501703-298f-4d43-b139-c4b6366af176)
