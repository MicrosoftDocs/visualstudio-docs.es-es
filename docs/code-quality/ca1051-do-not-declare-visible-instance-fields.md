---
title: 'CA1051: No declarar campos de instancia visibles'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
helpviewer_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fd4783f6327061da0ce522cc02082289cdee3d39
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55938103"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051: No declarar campos de instancia visibles

|||
|-|-|
|TypeName|DoNotDeclareVisibleInstanceFields|
|Identificador de comprobación|CA1051|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo visible externamente tiene un campo de instancia visible externamente.

## <a name="rule-description"></a>Descripción de la regla
 El uso principal de un campo debe ser como un detalle de implementación. Los campos deben ser `private` o `internal` y deben exponerse utilizando propiedades. Es tan fácil tener acceso a una propiedad como tal tener acceso a un campo, y puede cambiar el código en los descriptores de acceso de una propiedad como expanden las características del tipo sin introducir cambios importantes. Las propiedades que solo devuelven el valor de un campo privado o interno están optimizadas para llevar a cabo a la par de acceso a un campo; ganancia de rendimiento muy escasa está asociada con el uso de los campos visibles externamente a través de propiedades.

 Visible externamente se refiere a `public`, `protected`, y `protected internal` (`Public`, `Protected`, y `Protected Friend` en Visual Basic) los niveles de accesibilidad.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, hacer que el campo `private` o `internal` y exponerlo mediante el uso de una propiedad visible externamente.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima las advertencias de esta regla. Los campos visibles externamente no proporciona ninguna ventaja que no está disponible para las propiedades. Además, los campos públicos no puede proteger [peticiones de vínculo](/dotnet/framework/misc/link-demands). Consulte [CA2112: Los tipos seguros no deberían exponer campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo (`BadPublicInstanceFields`) que infringe esta regla. `GoodPublicInstanceFields` Muestra el código corregido.

 [!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../code-quality/codesnippet/CSharp/ca1051-do-not-declare-visible-instance-fields_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2112: Los tipos seguros no deberían exponer campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>Vea también
 [Peticiones de vínculo](/dotnet/framework/misc/link-demands)