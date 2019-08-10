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
ms.openlocfilehash: 78917bcd4c67e1da205595bac07c8e0e5947318d
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923060"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018: Marcar atributos con AttributeUsageAttribute

|||
|-|-|
|TypeName|MarkAttributesWithAttributeUsage|
|Identificador de comprobación|CA1018|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
El <xref:System.AttributeUsageAttribute?displayProperty=fullName> atributo no está presente en el atributo personalizado.

## <a name="rule-description"></a>Descripción de la regla
Al definir un atributo personalizado, márquelo <xref:System.AttributeUsageAttribute> con para indicar dónde se puede aplicar el atributo personalizado en el código fuente. El significado de un atributo y el uso que se le va a dar determinará sus ubicaciones válidas en código. Por ejemplo, podría definir un atributo que identifique a la persona responsable de mantener y mejorar cada tipo en una biblioteca, y esa responsabilidad siempre se asigna en el nivel de tipo. En este caso, los compiladores deberían habilitar el atributo en las clases, enumeraciones e interfaces, pero no deben habilitarlo en métodos, eventos o propiedades. Las directivas y los procedimientos de la organización determinarán si el atributo debe estar habilitado en los ensamblados.

La <xref:System.AttributeTargets?displayProperty=fullName> enumeración define los destinos que se pueden especificar para un atributo personalizado. Si se omite <xref:System.AttributeUsageAttribute>, el atributo personalizado será válido para todos los destinos, tal y como se `All` define en <xref:System.AttributeTargets> el valor de enumeración.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, especifique los destinos para el atributo <xref:System.AttributeUsageAttribute>mediante. Consulte el ejemplo siguiente.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Debe corregir una infracción de esta regla en lugar de excluir el mensaje. Incluso si el atributo hereda <xref:System.AttributeUsageAttribute>, el atributo debe estar presente para simplificar el mantenimiento del código.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se definen dos atributos. `BadCodeMaintainerAttribute`omite incorrectamente la <xref:System.AttributeUsageAttribute> instrucción y `GoodCodeMaintainerAttribute` implementa correctamente el atributo que se ha descrito anteriormente en esta sección. Tenga en cuenta que `DeveloperName` la regla [de diseño requiere la propiedad CA1019: Definir los descriptores de](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) acceso para los argumentos de atributo y se incluye por integridad.

[!code-csharp[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
[!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas
[CA1019: Definir los descriptores de acceso para los argumentos de atributo](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

[CA1813: Evitar atributos no sellados](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Vea también

- [Atributos](/dotnet/standard/design-guidelines/attributes)