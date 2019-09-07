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
ms.openlocfilehash: 455ab619f293981c5ebd3afba6336c63f2fe7f49
ms.sourcegitcommit: 0f44ec8ba0263056ad04d2d0dc904ad4206ce8fc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2019
ms.locfileid: "70766054"
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

El uso principal de un campo debe ser como un detalle de implementación. Los campos deben `private` ser `internal` o y deben exponerse mediante propiedades. Es tan fácil tener acceso a una propiedad, ya que tiene acceso a un campo, y el código de los descriptores de acceso de una propiedad puede cambiar a medida que las características del tipo se expanden sin introducir cambios importantes.

Las propiedades que devuelven el valor de un campo privado o interno están optimizadas para realizarse en par con el acceso a un campo. la ganancia de rendimiento del uso de campos visibles externamente en lugar de propiedades es mínima. *Externamente visible* hace referencia `public`a los niveles `protected internal` de`Public`accesibilidad `Protected`, `protected`y `Protected Friend` (, y en Visual Basic).

Además, los campos públicos no se pueden proteger mediante [peticiones de vínculo](/dotnet/framework/misc/link-demands). Para obtener más información, [vea CA2112: Los tipos seguros no deben exponer](../code-quality/ca2112-secured-types-should-not-expose-fields.md)los campos. (Las peticiones de vínculo no son aplicables a las aplicaciones .NET Core).

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, haga que `private` el `internal` campo o y lo exponga mediante una propiedad externamente visible.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Solo debe suprimir esta advertencia si está seguro de que los consumidores necesitan acceso directo al campo. Para la mayoría de las aplicaciones, los campos expuestos no proporcionan ventajas de rendimiento o mantenimiento con respecto a las propiedades.

Los consumidores pueden necesitar acceso de campo en las situaciones siguientes:

- en ASP.NET controles de contenido de formularios Web Forms
- Cuando la plataforma de destino hace uso `ref` de para modificar los campos, como los marcos de modelo-vista-ViewModel (MVVM) para WPF y UWP

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
