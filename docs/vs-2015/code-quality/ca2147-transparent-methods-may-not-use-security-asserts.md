---
title: 'CA2147: Los métodos transparentes no pueden usar seguridad aserciones | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3e8ac2e907e3c13a019e5f534faf86ae425ae30a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58994883"
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147: Los métodos transparentes no pueden usar aserciones de seguridad
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

 El [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 2.0 incorporó una característica denominada *transparencia*. Tipos, campos, interfaces, clases y métodos individuales pueden ser transparente o crítico.

 El código transparente no se permite para elevar los privilegios de seguridad. Por lo tanto, los permisos concedidos o que se le se pasan automáticamente a través del código para el dominio de aplicación host o el autor de llamada. Ejemplos de las elevaciones de aserciones, LinkDemands, SuppressUnmanagedCode, y `unsafe` código.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para resolver el problema, marque el código que llama a la aserción con el <xref:System.Security.SecurityCriticalAttribute>, o quitar la aserción.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima un mensaje de esta regla.

## <a name="example"></a>Ejemplo
 Este código generará un error si `SecurityTestClass` es transparente, cuando el `Assert` método produce una <xref:System.InvalidOperationException>.

 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2147.transparentmethodsmustnotusesecurityasserts/cs/ca2147 - transparentmethodsmustnotusesecurityasserts.cs#1)]

## <a name="example"></a>Ejemplo
 Una opción consiste en revisar el código del método SecurityTransparentMethod en el ejemplo siguiente y si el método se considera seguro para la elevación, marcar SecurityTransparentMethod con crítico Esto requiere que una seguridad detallada, completa y sin errores auditoría debe realizarse en el método junto con las leyendas que se producen dentro del método en la aserción:

 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SecurityTransparentCode2/cs/FxCop.Security.SecurityTransparentCode2.cs#1)]

 Otra opción es quitar la aserción del código y permitir que cualquier archivo posteriores E/S flujo de las demandas de permiso más allá de SecurityTransparentMethod al llamador. Esto permite que las comprobaciones de seguridad. En este caso, ninguna auditoría de seguridad generalmente es necesario, puesto que las peticiones de permiso fluirán al autor de la llamada o el dominio de aplicación. Las demandas de permisos se controlan estrechamente a través de la directiva de seguridad, entornos de hospedaje y concede permiso de código fuente.

## <a name="see-also"></a>Vea también
 [Advertencias de seguridad](../code-quality/security-warnings.md)
