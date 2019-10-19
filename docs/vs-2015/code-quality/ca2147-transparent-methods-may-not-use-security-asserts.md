---
title: 'CA2147: los métodos transparentes no pueden usar aserciones de seguridad | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7f2bd0042b6f9a8e46939ab34c86294218fb79f4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610159"
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
 El código marcado como <xref:System.Security.SecurityTransparentAttribute> no tiene permisos suficientes para la aserción.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla analiza todos los métodos y tipos de un ensamblado que es un 100% transparente o mixto y crítico, y marca cualquier uso declarativo o imperativo de <xref:System.Security.CodeAccessPermission.Assert%2A>.

 En tiempo de ejecución, cualquier llamada a <xref:System.Security.CodeAccessPermission.Assert%2A> desde código transparente hará que se inicie una <xref:System.InvalidOperationException>. Esto puede ocurrir en ensamblados transparentes del 100%, y también en ensamblados transparentes y críticos mixtos donde un método o tipo se declara transparente, pero incluye una aserción declarativa o imperativa.

 El [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 2,0 presentó una característica denominada *transparencia*. Los métodos, los campos, las interfaces, las clases y los tipos individuales pueden ser transparentes o críticos.

 No se permite que el código transparente eleve los privilegios de seguridad. Por lo tanto, todos los permisos concedidos o solicitados se pasan automáticamente a través del código al dominio de aplicación host o del llamador. Entre los ejemplos de elevaciones se incluyen aserciones, LinkDemands, SuppressUnmanagedCode y `unsafe` código.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para resolver el problema, marque el código que llama a la aserción con el <xref:System.Security.SecurityCriticalAttribute> o quite la aserción.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima un mensaje de esta regla.

## <a name="example"></a>Ejemplo
 Este código producirá un error si `SecurityTestClass` es transparente, cuando el método `Assert` produce una <xref:System.InvalidOperationException>.

 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2147.transparentmethodsmustnotusesecurityasserts/cs/ca2147 - transparentmethodsmustnotusesecurityasserts.cs#1)]

## <a name="example"></a>Ejemplo
 Una opción consiste en revisar el código del método SecurityTransparentMethod en el ejemplo siguiente y, si se considera que el método es seguro para la elevación, Mark SecurityTransparentMethod con crítico para la seguridad, lo que requiere una seguridad detallada, completa y sin errores la auditoría debe realizarse en el método junto con las llamadas que se producen dentro del método bajo la aserción:

 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SecurityTransparentCode2/cs/FxCop.Security.SecurityTransparentCode2.cs#1)]

 Otra opción es quitar la aserción del código y permitir que las peticiones de permisos de e/s de archivos subsiguientes fluyan más allá de SecurityTransparentMethod al autor de la llamada. Esto habilita las comprobaciones de seguridad. En este caso, no es necesario realizar ninguna auditoría de seguridad, ya que las demandas de permiso fluyen al llamador o al dominio de aplicación. Las peticiones de permisos se controlan estrechamente a través de la Directiva de seguridad, el entorno de hospedaje y las concesiones de permisos de origen de código.

## <a name="see-also"></a>Vea también
 [Advertencias de seguridad](../code-quality/security-warnings.md)
