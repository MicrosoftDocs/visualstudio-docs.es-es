---
title: 'CA2112: Los tipos seguros no deberían exponer campos'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2112
- SecuredTypesShouldNotExposeFields
helpviewer_keywords:
- SecuredTypesShouldNotExposeFields
- CA2112
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 538c7ac89643c168086d6bdcb514d88295e482dc
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548366"
---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112: Los tipos seguros no deberían exponer campos

|||
|-|-|
|TypeName|SecuredTypesShouldNotExposeFields|
|Identificador de comprobación|CA2112|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo público o protegido contiene campos públicos y está protegido por un [peticiones de vínculo](/dotnet/framework/misc/link-demands).

## <a name="rule-description"></a>Descripción de la regla
 Si el código tiene acceso a una instancia de tipo que está protegida por una solicitud de vínculo, el código no cumplirá la solicitud para obtener acceso a los campos del tipo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, que los campos no públicos y agregue propiedades públicas o los métodos que devuelven los datos del campo. Comprobaciones de seguridad de LinkDemand en tipos de protegen el acceso a las propiedades y métodos del tipo. Sin embargo, la seguridad de acceso del código no es aplicable a los campos.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Para problemas de seguridad y para un buen diseño, debe corregir las infracciones estableciendo el nonpublic campos públicos. Puede suprimir una advertencia de esta regla si el campo no contiene información que debe permanecer segura y no dependen del contenido del campo.

## <a name="example"></a>Ejemplo
 En el siguiente ejemplo se compone de un tipo de biblioteca (`SecuredTypeWithFields`) con campos no seguros, un tipo (`Distributor`) que puede crear instancias del tipo de biblioteca y las instancias pasadas errónea a tipos no tiene permiso para crearlos y código de aplicación puede leer los campos de la instancia, incluso aunque no tenga el permiso que protege el tipo.

 El siguiente código de biblioteca infringe la regla.

 [!code-csharp[FxCop.Security.LinkDemandOnField#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_1.cs)]

## <a name="example-1"></a>Ejemplo 1
 La aplicación no puede crear una instancia debido a la petición de vínculo que protege el tipo. La siguiente clase permite que la aplicación obtener una instancia del tipo protegido.

 [!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_2.cs)]

## <a name="example-2"></a>Ejemplo 2
 La aplicación siguiente muestra cómo hacerlo, sin permiso para tener acceso a los métodos de un tipo seguro, código puede tener acceso a sus campos.

 [!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_3.cs)]

Este ejemplo produce el siguiente resultado:

```txt
Creating an instance of SecuredTypeWithFields.
Secured type fields: 22, 33
Changing secured type's field...
Cached Object fields: 99, 33
```

## <a name="related-rules"></a>Reglas relacionadas

- [CA1051: No declarar campos de instancia visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Vea también

- [Peticiones de vínculo](/dotnet/framework/misc/link-demands)
- [Datos y modelado](/dotnet/framework/data/index)