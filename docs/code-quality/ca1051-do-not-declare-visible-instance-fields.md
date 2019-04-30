---
title: 'CA1051: No declarar campos de instancia visibles'
ms.date: 03/11/2019
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
ms.openlocfilehash: 7b7a2165b9b921865ce1fd45017c996e48917d12
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779057"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051: No declarar campos de instancia visibles

|||
|-|-|
|TypeName|DoNotDeclareVisibleInstanceFields|
|Identificador de comprobación|CA1051|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo

Un tipo tiene un campo de instancia no privados.

De forma predeterminada, esta regla busca solo en tipos visibles externamente, pero se trata de [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

El uso principal de un campo debe ser como un detalle de implementación. Los campos deben ser `private` o `internal` y deben exponerse utilizando propiedades. Es tan fácil tener acceso a una propiedad como tal tener acceso a un campo, y puede cambiar el código en los descriptores de acceso de una propiedad como expanden las características del tipo sin introducir cambios importantes. Las propiedades que solo devuelven el valor de un campo privado o interno están optimizadas para llevar a cabo a la par de acceso a un campo; ganancia de rendimiento muy escasa está asociada con el uso de los campos visibles externamente a través de propiedades.

Visible externamente se refiere a `public`, `protected`, y `protected internal` (`Public`, `Protected`, y `Protected Friend` en Visual Basic) los niveles de accesibilidad.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, hacer que el campo `private` o `internal` y exponerlo mediante el uso de una propiedad visible externamente.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

No suprima las advertencias de esta regla. Los campos visibles externamente no proporciona ninguna ventaja que no está disponible para las propiedades. Además, los campos públicos no puede proteger [peticiones de vínculo](/dotnet/framework/misc/link-demands). Consulte [CA2112: Los tipos seguros no deberían exponer campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="configurability"></a>Capacidad de configuración

Si ejecuta esta regla de [analizadores de FxCop](install-fxcop-analyzers.md) (y no a través de análisis de código estático), puede configurar qué partes de su código base para ejecutar esta regla en, en función de su accesibilidad. Por ejemplo, para especificar que debe ejecutarse la regla sólo con respecto a la superficie de API no públicos, agregue el siguiente par clave-valor a un archivo .editorconfig en el proyecto:

```
dotnet_code_quality.ca1051.api_surface = private, internal
```

Puede configurar esta opción para simplemente esta regla, para todas las reglas o para todas las reglas de esta categoría (diseño). Para obtener más información, consulte [analizadores de FxCop configurar](configure-fxcop-analyzers.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra un tipo (`BadPublicInstanceFields`) que infringe esta regla. `GoodPublicInstanceFields` Muestra el código corregido.

[!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../code-quality/codesnippet/CSharp/ca1051-do-not-declare-visible-instance-fields_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas

- [CA2112: Los tipos seguros no deberían exponer campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>Vea también

- [Peticiones de vínculo](/dotnet/framework/misc/link-demands)