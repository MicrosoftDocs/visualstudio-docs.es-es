---
title: 'CA1018: Marcar atributos con AttributeUsageAttribute'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7949477e7fec9e215fd84eaa15d937be969fa102
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
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
 Cuando se define un atributo personalizado, márquelo utilizando <xref:System.AttributeUsageAttribute> para indicar dónde se puede aplicar el atributo personalizado en el código fuente. El significado de un atributo y el uso que se le va a dar determinará sus ubicaciones válidas en código. Por ejemplo, podría definir un atributo que identifica a la persona que es responsable de mantener y mejorar cada tipo en una biblioteca y responsabilidad siempre se asigna en el nivel de tipo. En este caso, los compiladores deben habilitar el atributo en clases, enumeraciones e interfaces, pero no deben habilitar en los métodos, eventos o propiedades. Procedimientos y directivas organizativas se determinan si el atributo debe estar habilitado en ensamblados.

 El <xref:System.AttributeTargets?displayProperty=fullName> enumeración define los destinos que puede especificar para un atributo personalizado. Si se omite <xref:System.AttributeUsageAttribute>, el atributo personalizado será válido para todos los destinos, tal como se define por la `All` valo <xref:System.AttributeTargets> enumeración.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, especificar destinos para el atributo mediante <xref:System.AttributeUsageAttribute>. Vea el ejemplo siguiente.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Debe corregir una infracción de esta regla en lugar de excluir el mensaje. Aunque el atributo hereda <xref:System.AttributeUsageAttribute>, el atributo debe estar presente para simplificar el mantenimiento del código.

## <a name="example"></a>Ejemplo
 El siguiente ejemplo define dos atributos. `BadCodeMaintainerAttribute` omite incorrectamente la <xref:System.AttributeUsageAttribute> (instrucción), y `GoodCodeMaintainerAttribute` implementa correctamente el atributo descrito anteriormente en esta sección. Tenga en cuenta que la propiedad `DeveloperName` requerido por la regla de diseño [CA1019: definir descriptores de acceso para los argumentos de atributo](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) y se incluye por integridad.

 [!code-csharp[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1019: Definir descriptores de acceso para los argumentos de atributo](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1813: Evitar atributos no sellados](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Vea también
 [Atributos](/dotnet/standard/design-guidelines/attributes)