---
title: 'CA2122: No exponer indirectamente métodos con peticiones de vínculos'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 340d8f0a45506f15cdd9281f7ecda463583c3144
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920825"
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122: No exponer indirectamente métodos con peticiones de vínculos

|||
|-|-|
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|
|Identificador de comprobación|CA2122|
|Categoría|Microsoft.Security|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa
Un miembro público o protegido tiene una [petición de vínculo](/dotnet/framework/misc/link-demands) y lo llama un miembro que no realiza ninguna comprobación de seguridad.

## <a name="rule-description"></a>Descripción de la regla
Una solicitud de vínculo sólo comprueba los permisos del llamador inmediato. Si un miembro `X` no realiza ninguna solicitud de seguridad de sus llamadores y llama al código protegido por una petición de vínculo, un llamador sin el permiso `X` necesario puede utilizar para tener acceso al miembro protegido.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Agregue datos de seguridad [y modelado](/dotnet/framework/data/index) o petición de vínculo al miembro para que ya no proporcione acceso no seguro al miembro protegido por petición de vínculo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Para suprimir de forma segura una advertencia de esta regla, debe asegurarse de que el código no concede a sus llamadores acceso a las operaciones o recursos que se pueden usar de forma destructiva.

## <a name="example-1"></a>Ejemplo 1
En los siguientes ejemplos se muestra una biblioteca que infringe la regla y una aplicación que muestra la debilidad de la biblioteca. La biblioteca de ejemplo proporciona dos métodos que juntos infringen la regla. El `EnvironmentSetting` método está protegido por una petición de vínculo para el acceso no restringido a las variables de entorno. El `DomainInformation` método no realiza ninguna petición de seguridad de sus llamadores antes `EnvironmentSetting`de llamar a.

[!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_1.cs)]

## <a name="example-2"></a>Ejemplo 2
La siguiente aplicación llama al miembro de biblioteca no seguro.

[!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_2.cs)]

Este ejemplo produce el siguiente resultado:

```txt
*Value from unsecured member: seattle.corp.contoso.com
```

## <a name="see-also"></a>Vea también

- [Instrucciones de codificación segura](/dotnet/standard/security/secure-coding-guidelines)
- [Peticiones de vínculo](/dotnet/framework/misc/link-demands)
- [Datos y modelado](/dotnet/framework/data/index)