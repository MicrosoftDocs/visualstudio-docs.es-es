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
ms.openlocfilehash: 4c0aa3fe5c45e34445c49c4b3a5f0abad1e98739
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55943615"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018: Marcar atributos con AttributeUsageAttribute

|||
|-|-|
|TypeName|MarkAttributesWithAttributeUsage|
|Identificador de comprobación|CA1018|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 El <xref:System.AttributeUsageAttribute?displayProperty=fullName> atributo no está presente en el atributo personalizado.

## <a name="rule-description"></a>Descripción de la regla
 Al definir un atributo personalizado, márquelo utilizando <xref:System.AttributeUsageAttribute> para indicar dónde se puede aplicar el atributo personalizado en el código fuente. El significado de un atributo y el uso que se le va a dar determinará sus ubicaciones válidas en código. Por ejemplo, podría definir un atributo que identifica a la persona responsable de mantener y mejorar cada tipo en una biblioteca y que siempre se asigna la responsabilidad en el nivel de tipo. En este caso, los compiladores deben habilitar el atributo en clases, enumeraciones e interfaces, pero no deben habilitar en los métodos, eventos o propiedades. Procedimientos y directivas organizativas podrían dictar si el atributo debe estar habilitado en los ensamblados.

 El <xref:System.AttributeTargets?displayProperty=fullName> enumeración define los destinos que se pueden especificar para un atributo personalizado. Si se omite <xref:System.AttributeUsageAttribute>, el atributo personalizado será válido para todos los destinos, como se define en el `All` valor <xref:System.AttributeTargets> enumeración.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, especifique los destinos para el atributo con <xref:System.AttributeUsageAttribute>. Vea el ejemplo siguiente.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Debe corregir una infracción de esta regla en lugar de excluir el mensaje. Incluso si el atributo hereda <xref:System.AttributeUsageAttribute>, el atributo debe estar presente para simplificar el mantenimiento del código.

## <a name="example"></a>Ejemplo
 El siguiente ejemplo define dos atributos. `BadCodeMaintainerAttribute` omite incorrectamente la <xref:System.AttributeUsageAttribute> instrucción, y `GoodCodeMaintainerAttribute` implementa correctamente el atributo que se describe anteriormente en esta sección. Tenga en cuenta que la propiedad `DeveloperName` requerido por la regla de diseño [CA1019: Definir descriptores de acceso para los argumentos de atributo](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) y se incluye por razones de integridad.

 [!code-csharp[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1019: Definir descriptores de acceso para los argumentos de atributo](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1813: Evitar atributos no sellados](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Vea también

- [Atributos](/dotnet/standard/design-guidelines/attributes)