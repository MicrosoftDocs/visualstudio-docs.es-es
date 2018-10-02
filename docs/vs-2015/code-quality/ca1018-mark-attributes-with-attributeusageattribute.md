---
title: 'CA1018: Marcar atributos con AttributeUsageAttribute | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
helpviewer_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: bfb9e7d954697fab554749dbd42155f92030ce88
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591331"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018: Marcar atributos con AttributeUsageAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [CA1018: marcar atributos con AttributeUsageAttribute](https://docs.microsoft.com/visualstudio/code-quality/ca1018-mark-attributes-with-attributeusageattribute).

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

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Debe corregir una infracción de esta regla en lugar de excluir el mensaje. Incluso si el atributo hereda <xref:System.AttributeUsageAttribute>, el atributo debe estar presente para simplificar el mantenimiento del código.

## <a name="example"></a>Ejemplo
 El siguiente ejemplo define dos atributos. `BadCodeMaintainerAttribute` omite incorrectamente la <xref:System.AttributeUsageAttribute> instrucción, y `GoodCodeMaintainerAttribute` implementa correctamente el atributo que se describe anteriormente en esta sección. Tenga en cuenta que la propiedad `DeveloperName` requerido por la regla de diseño [CA1019: definir descriptores de acceso para los argumentos de atributo](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) y se incluye por razones de integridad.

 [!code-csharp[FxCop.Design.AttributeUsage#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeUsage/cs/FxCop.Design.AttributeUsage.cs#1)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeUsage/vb/FxCop.Design.AttributeUsage.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1019: Definir descriptores de acceso para los argumentos de atributo](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1813: Evitar atributos no sellados](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Vea también
 [Atributos](http://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)



