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
ms.openlocfilehash: c5dd8a4b2d0b32a8c52f75dee6fd765a7ea6ec9a
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547559"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051: No declarar campos de instancia visibles

|||
|-|-|
|TypeName|DoNotDeclareVisibleInstanceFields|
|Identificador de comprobación|CA1051|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa

Un tipo tiene un campo de instancia no privado.

De forma predeterminada, esta regla solo examina los tipos visibles externamente, pero esto es [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

El uso principal de un campo debe ser como un detalle de implementación. Los campos deben `private` ser `internal` o y deben exponerse mediante propiedades. Es tan fácil acceder a una propiedad a medida que se tiene acceso a un campo, y el código de los descriptores de acceso de una propiedad puede cambiar a medida que las características del tipo se expanden sin introducir cambios importantes. Las propiedades que devuelven el valor de un campo privado o interno están optimizadas para realizarse en par con el acceso a un campo. un aumento del rendimiento muy bajo se asocia al uso de campos visibles externamente en las propiedades.

Externamente visible hace referencia `public`a los niveles `protected internal` de`Public`accesibilidad `Protected`, `protected` `Protected Friend` y (, y en Visual Basic).

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, haga que `private` el `internal` campo o y lo exponga mediante una propiedad externamente visible.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

No suprima las advertencias de esta regla. Los campos visibles externamente no proporcionan ninguna ventaja que no esté disponible para las propiedades. Además, los campos públicos no se pueden proteger mediante [peticiones de vínculo](/dotnet/framework/misc/link-demands). Consulte [CA2112: Los tipos seguros no deben exponer](../code-quality/ca2112-secured-types-should-not-expose-fields.md)los campos.

## <a name="configurability"></a>Configurabilidad

Si está ejecutando esta regla desde los [analizadores de FxCop](install-fxcop-analyzers.md) (y no con el análisis heredado), puede configurar en qué partes del código base ejecutar esta regla, según su accesibilidad. Por ejemplo, para especificar que la regla se debe ejecutar solo en la superficie de API no pública, agregue el siguiente par clave-valor a un archivo. editorconfig en el proyecto:

```ini
dotnet_code_quality.ca1051.api_surface = private, internal
```

Puede configurar esta opción solo para esta regla, para todas las reglas o para todas las reglas de esta categoría (diseño). Para obtener más información, vea [configurar analizadores de FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra un`BadPublicInstanceFields`tipo () que infringe esta regla. `GoodPublicInstanceFields`muestra el código corregido.

[!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../code-quality/codesnippet/CSharp/ca1051-do-not-declare-visible-instance-fields_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas

- [CA2112: Los tipos seguros no deberían exponer campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>Vea también

- [Peticiones de vínculo](/dotnet/framework/misc/link-demands)