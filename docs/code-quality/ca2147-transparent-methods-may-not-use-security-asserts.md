---
title: 'CA2147: Los métodos transparentes no pueden usar aserciones de seguridad'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- SecurityTransparentCodeShouldNotAssert
- CA2147
- CA2128
helpviewer_keywords:
- CA2128
- SecurityTransparentCodeShouldNotAssert
ms.assetid: 5d31e940-e599-4b23-9b28-1c336f8d910e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4daf5d4183c8226a0bed613c5e175ddbd620f43a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53912498"
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147: Los métodos transparentes no pueden usar aserciones de seguridad

|||
|-|-|
|TypeName|SecurityTransparentCodeShouldNotAssert|
|Identificador de comprobación|CA2147|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Código que está marcado como <xref:System.Security.SecurityTransparentAttribute> no tiene permisos suficientes para imponerse.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla analiza todos los métodos y tipos de un ensamblado que es ya sea 100% transparente o mixto transparente y crítico y marca cualquier uso declarativo o imperativo de <xref:System.Security.CodeAccessPermission.Assert%2A>.

 En tiempo de ejecución, las llamadas a <xref:System.Security.CodeAccessPermission.Assert%2A> desde código transparente provocará un <xref:System.InvalidOperationException> que se produzca. Esto puede ocurrir en ambos ensamblados transparentes del 100% y también en los ensamblados mixtos transparente y crítico donde un método o tipo se declara transparente, pero incluye una aserción declarativa o imperativa.

 .NET Framework 2.0 incorporó una característica denominada *transparencia*. Tipos, campos, interfaces, clases y métodos individuales pueden ser transparente o crítico.

 El código transparente no se permite para elevar los privilegios de seguridad. Por lo tanto, los permisos concedidos o que se le se pasan automáticamente a través del código para el dominio de aplicación host o el autor de llamada. Ejemplos de las elevaciones de aserciones, LinkDemands, SuppressUnmanagedCode, y `unsafe` código.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para resolver el problema, marque el código que llama a la aserción con el <xref:System.Security.SecurityCriticalAttribute>, o quitar la aserción.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima un mensaje de esta regla.

## <a name="example"></a>Ejemplo
 Este código generará un error si `SecurityTestClass` es transparente, cuando el `Assert` método produce una <xref:System.InvalidOperationException>.

 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_1.cs)]

## <a name="example"></a>Ejemplo
 Una opción consiste en revisar el código del método SecurityTransparentMethod en el ejemplo siguiente y si el método se considera seguro para la elevación, marcar SecurityTransparentMethod con crítico. Esto requiere que se debe realizar una auditoría de seguridad detallada, completa y sin errores en el método junto con las leyendas que se producen dentro del método en la aserción:

 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_2.cs)]

 Otra opción es quitar la aserción del código y permitir que cualquier archivo posteriores E/S flujo de las demandas de permiso más allá de SecurityTransparentMethod al llamador. Esto permite que las comprobaciones de seguridad. En este caso, no se necesita ninguna auditoría de seguridad, ya que las peticiones de permiso fluirán al autor de la llamada o el dominio de aplicación. Las demandas de permisos se controlan estrechamente a través de la directiva de seguridad, entornos de hospedaje y concede permiso de código fuente.

## <a name="see-also"></a>Vea también
 [Advertencias de seguridad](../code-quality/security-warnings.md)