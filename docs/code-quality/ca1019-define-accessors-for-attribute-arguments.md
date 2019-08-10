---
title: 'CA1019: Definir descriptores de acceso para los argumentos de atributo'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
helpviewer_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8422427997db291aa24bc8a8bacfdc59abe35998
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923072"
---
# <a name="ca1019-define-accessors-for-attribute-arguments"></a>CA1019: Definir descriptores de acceso para los argumentos de atributo

|||
|-|-|
|TypeName|DefineAccessorsForAttributeArguments|
|Identificador de comprobación|CA1019|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
En su constructor, un atributo define los argumentos que no tienen las propiedades correspondientes.

## <a name="rule-description"></a>Descripción de la regla
Los atributos pueden definir argumentos obligatorios que deben especificarse al aplicar el atributo a un destino. Éstos también se denominan argumentos posicionales porque se proporcionan para atribuir constructores como parámetros posicionales. Para cada argumento obligatorio, el atributo debe proporcionar también una propiedad de sólo lectura correspondiente de modo que el valor del argumento se pueda recuperar en tiempo de ejecución. Esta regla comprueba que, para cada parámetro de constructor, se ha definido la propiedad correspondiente.

Los atributos también pueden definir argumentos opcionales, que también se denominan argumentos con nombre. Estos argumentos se proporcionan para atribuir constructores por nombre y deben tener una propiedad de lectura/escritura correspondiente.

En el caso de los argumentos obligatorios y opcionales, las propiedades y los parámetros de constructor correspondientes deben usar el mismo nombre pero diferentes mayúsculas y minúsculas. Las propiedades usan mayúsculas y minúsculas Pascal y los parámetros usan mayúsculas y minúsculas Camel.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, agregue una propiedad de solo lectura para cada parámetro del constructor que no tenga ninguno.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Suprima una advertencia de esta regla si no desea que se pueda recuperar el valor del argumento obligatorio.

## <a name="custom-attributes-example"></a>Ejemplo de atributos personalizados

En el ejemplo siguiente se muestran dos atributos que definen un parámetro obligatorio (posicional). La primera implementación del atributo está definida incorrectamente. La segunda implementación es correcta.

[!code-csharp[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_1.cs)]
[!code-vb[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/VisualBasic/ca1019-define-accessors-for-attribute-arguments_1.vb)]

## <a name="positional-and-named-arguments"></a>Argumentos posicionales y con nombre

Los argumentos con nombre y posicionales lo hacen claro a los consumidores de la biblioteca qué argumentos son obligatorios para el atributo y qué argumentos son opcionales.

En el ejemplo siguiente se muestra una implementación de un atributo que tiene argumentos posicionales y con nombre:

[!code-csharp[FxCop.Design.AttributeAccessorsNamed#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_2.cs)]

En el ejemplo siguiente se muestra cómo aplicar el atributo personalizado a dos propiedades:

[!code-csharp[FxCop.Design.AttributeAccessorsNamedApplied#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_3.cs)]

## <a name="related-rules"></a>Reglas relacionadas
[CA1813: Evitar atributos no sellados](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Vea también
[Atributos](/dotnet/standard/design-guidelines/attributes)