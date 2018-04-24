---
title: 'CA1051: No declarar campos de instancia visibles'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb322ffb6f3603001e9fa673eb9daf9f28d73b18
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
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
 El uso principal de un campo debe ser como un detalle de implementación. Los campos deben ser `private` o `internal` y deben exponerse utilizando propiedades. Es tan fácil de tener acceso a una propiedad es para tener acceso a un campo y el código en los descriptores de acceso de una propiedad puede cambiar a medida que amplían las características del tipo sin introducir cambios importantes. Propiedades que simplemente devuelven el valor de un campo privado o interno están optimizadas para llevar a cabo a la par de acceso a un campo; ganancia de rendimiento muy escasa está asociado con el uso de los campos visibles externamente sobre las propiedades.

 Visible externamente hace referencia a `public`, `protected`, y `protected internal` (`Public`, `Protected`, y `Protected Friend` en Visual Basic) niveles de accesibilidad.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, hacer que el campo `private` o `internal` y exponer mediante una propiedad visible externamente.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. Campos visibles externamente no proporciona ninguna ventaja que no está disponible a las propiedades. Además, los campos públicos no se puede proteger por [peticiones de vínculo](/dotnet/framework/misc/link-demands). Vea [CA2112: los tipos seguros no deberían exponer campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo (`BadPublicInstanceFields`) que infringe esta regla. `GoodPublicInstanceFields` Muestra el código corregido.

 [!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../code-quality/codesnippet/CSharp/ca1051-do-not-declare-visible-instance-fields_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2112: Los tipos seguros no deberían exponer campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>Vea también
 [Peticiones de vínculo](/dotnet/framework/misc/link-demands)