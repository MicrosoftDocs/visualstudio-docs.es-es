---
title: 'CA2122: No exponer indirectamente métodos con peticiones de vínculos'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2122
- DoNotIndirectlyExposeMethodsWithLinkDemands
helpviewer_keywords:
- DoNotIndirectlyExposeMethodsWithLinkDemands
- CA2122
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8d17c2981e4dabe82817aeedcf4fcab93e970b47
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548904"
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122: No exponer indirectamente métodos con peticiones de vínculos

|||
|-|-|
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|
|Identificador de comprobación|CA2122|
|Categoría|Microsoft.Security|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Un miembro público o protegido tiene un [peticiones de vínculo](/dotnet/framework/misc/link-demands) y se llama a un miembro que no realiza ninguna comprobación de seguridad.

## <a name="rule-description"></a>Descripción de la regla
 Una solicitud de vínculo sólo comprueba los permisos del llamador inmediato. Si un miembro `X` ningún demandas de seguridad de sus llamadores y las llamadas de código protegido por una petición de vínculo, un llamador sin el permiso necesario puede utilizar `X` para tener acceso al miembro protegido.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Agregar una seguridad [datos y modelado](/dotnet/framework/data/index) o vincular a petición para el miembro de modo que ya no proporciona acceso no seguro al miembro protegido por solicitud de vínculo.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Para suprimir una advertencia de esta regla de forma segura, debe asegurarse de que el código no tiene acceso a las operaciones o los recursos que se pueden usar de forma destructiva sus llamadores.

## <a name="example-1"></a>Ejemplo 1
 Los ejemplos siguientes muestran una biblioteca que infringe la regla y una aplicación que muestra el punto débil de la biblioteca. La biblioteca de ejemplo proporciona dos métodos que juntos infringen la regla. El `EnvironmentSetting` método está protegido por una petición de vínculo para el acceso sin restricciones a las variables de entorno. El `DomainInformation` método no realiza ninguna petición de seguridad de sus llamadores antes de llamar a `EnvironmentSetting`.

 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_1.cs)]

## <a name="example-2"></a>Ejemplo 2
 La siguiente aplicación llama al miembro de biblioteca no segura.

 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_2.cs)]

Este ejemplo produce el siguiente resultado:

```txt
*Value from unsecured member: seattle.corp.contoso.com
```

## <a name="see-also"></a>Vea también

- [Instrucciones de codificación segura](/dotnet/standard/security/secure-coding-guidelines)
- [Peticiones de vínculo](/dotnet/framework/misc/link-demands)
- [Datos y modelado](/dotnet/framework/data/index)