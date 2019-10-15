---
title: 'CA1018: Marcar atributos con AttributeUsageAttribute'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
helpviewer_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 133ee073398817c037af95e2009c5acc98e1e5a2
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306136"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018: Marcar atributos con AttributeUsageAttribute

|||
|-|-|
|TypeName|MarkAttributesWithAttributeUsage|
|Identificador de comprobación|CA1018|
|Category|Microsoft.Design|
|Cambio importante|Problemático|

## <a name="cause"></a>Motivo
El atributo <xref:System.AttributeUsageAttribute?displayProperty=fullName> no está presente en el atributo personalizado.

## <a name="rule-description"></a>Descripción de la regla
Al definir un atributo personalizado, márquelo con <xref:System.AttributeUsageAttribute> para indicar en qué lugar del código fuente se puede aplicar el atributo personalizado. El significado de un atributo y el uso que se le va a dar determinará sus ubicaciones válidas en código. Por ejemplo, podría definir un atributo que identifique a la persona responsable de mantener y mejorar cada tipo en una biblioteca, y esa responsabilidad siempre se asigna en el nivel de tipo. En este caso, los compiladores deberían habilitar el atributo en las clases, enumeraciones e interfaces, pero no deben habilitarlo en métodos, eventos o propiedades. Las directivas y los procedimientos de la organización determinarán si el atributo debe estar habilitado en los ensamblados.

La enumeración <xref:System.AttributeTargets?displayProperty=fullName> define los destinos que se pueden especificar para un atributo personalizado. Si omite <xref:System.AttributeUsageAttribute>, el atributo personalizado será válido para todos los destinos, tal y como se define en el valor `All` de la enumeración <xref:System.AttributeTargets>.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, especifique los destinos para el atributo mediante <xref:System.AttributeUsageAttribute>. Vea el ejemplo siguiente.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Debe corregir una infracción de esta regla en lugar de excluir el mensaje. Incluso si el atributo hereda <xref:System.AttributeUsageAttribute>, el atributo debe estar presente para simplificar el mantenimiento del código.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se definen dos atributos. `BadCodeMaintainerAttribute` omite incorrectamente la instrucción <xref:System.AttributeUsageAttribute> y `GoodCodeMaintainerAttribute` implementa correctamente el atributo que se ha descrito anteriormente en esta sección. Observe que la propiedad `DeveloperName` es necesaria para la regla de diseño [CA1019: Definir los descriptores de acceso para los argumentos de atributo @ no__t-0 y se incluye por integridad.

[!code-csharp[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
[!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas
[CA1019: Definir los descriptores de acceso para los argumentos de atributo @ no__t-0

[CA1813: Evitar atributos no sellados @ no__t-0

## <a name="see-also"></a>Vea también

- [Atributos](/dotnet/standard/design-guidelines/attributes)