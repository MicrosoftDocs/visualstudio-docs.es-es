---
title: 'CA2147: Los métodos transparentes no pueden usar aserciones de seguridad'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
ms.openlocfilehash: f732e22d53b4d469f73c4ef3efc753240fa6841f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31918102"
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147: Los métodos transparentes no pueden usar aserciones de seguridad
|||
|-|-|
|TypeName|SecurityTransparentCodeShouldNotAssert|
|Identificador de comprobación|CA2147|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 El código marcado como <xref:System.Security.SecurityTransparentAttribute> no tiene permisos suficientes para imponerse.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla analiza todos los métodos y tipos de un ensamblado que está ya sea 100% transparente o mixto de transparente y crítico y marca cualquier uso declarativo o imperativo de <xref:System.Security.CodeAccessPermission.Assert%2A>.

 Durante la ejecución, las llamadas a <xref:System.Security.CodeAccessPermission.Assert%2A> desde código transparente hará que un <xref:System.InvalidOperationException> que se produzca. Esto puede ocurrir en los ensamblados 100% transparentes y también en los ensamblados mixtos de transparente y crítico donde un método o tipo se declara transparente, pero incluye una aserción declarativa o imperativa.

 El [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 incorporó una característica denominada *transparencia*. Tipos, campos, interfaces, clases y métodos individuales pueden ser transparente o crítico.

 El código transparente no puede elevar los privilegios de seguridad. Por lo tanto, cualquier permiso concedido o demandado del mismo automáticamente se pasa a través del código para el dominio de aplicación del llamador o del host. Ejemplos de elevaciones aserciones, LinkDemands, SuppressUnmanagedCode, y `unsafe` código.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para resolver el problema, marque el código que llama la aserción con el <xref:System.Security.SecurityCriticalAttribute>, o quitar la aserción.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima un mensaje de esta regla.

## <a name="example"></a>Ejemplo
 Este código generará un error si `SecurityTestClass` es transparente, cuando la `Assert` método produce un <xref:System.InvalidOperationException>.

 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_1.cs)]

## <a name="example"></a>Ejemplo
 Una opción es revisar el código del método SecurityTransparentMethod en el ejemplo siguiente y si el método se considera seguro para la elevación, marcar SecurityTransparentMethod con crítico seguro Esto requiere que una seguridad detallada, completa y sin errores auditoría debe realizarse en el método junto con cualquier llamada de salida que se producen dentro del método bajo la aserción:

 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_2.cs)]

 Otra opción es quitar la aserción del código y permitir que cualquier archivo posterior E/S permiso peticiones flujo más allá de SecurityTransparentMethod al llamador. Esto permite que las comprobaciones de seguridad. En este caso, ninguna auditoría de seguridad por lo general es necesario, porque las demandas de permiso se desplazarán hasta el autor de llamada o el dominio de aplicación. Las peticiones de permisos se controlan estrechamente a través de la directiva de seguridad, entornos de hospedaje y concede permiso de código fuente.

## <a name="see-also"></a>Vea también
 [Advertencias de seguridad](../code-quality/security-warnings.md)