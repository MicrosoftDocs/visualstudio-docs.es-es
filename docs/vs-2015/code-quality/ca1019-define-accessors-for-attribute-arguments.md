---
title: 'CA1019: definir descriptores de acceso para los argumentos de atributo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
helpviewer_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ec9be9dae502ec48570a85576f483518ed0d75d6
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534958"
---
# <a name="ca1019-define-accessors-for-attribute-arguments"></a>CA1019: Definir descriptores de acceso para los argumentos de atributo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|DefineAccessorsForAttributeArguments|
|Identificador de comprobación|CA1019|
|Category|Microsoft. Design|
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

### <a name="description"></a>Descripción
 En el ejemplo siguiente se muestran dos atributos que definen un parámetro obligatorio (posicional). La primera implementación del atributo está definida incorrectamente. La segunda implementación es correcta.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Design.AttributeAccessors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessors/cs/FxCop.Design.AttributeAccessors.cs#1)]
 [!code-vb[FxCop.Design.AttributeAccessors#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessors/vb/FxCop.Design.AttributeAccessors.vb#1)]

## <a name="positional-and-named-arguments"></a>Argumentos posicionales y con nombre

### <a name="description"></a>Descripción
 Los argumentos con nombre y posicionales hacen que resulten claros a los consumidores de la biblioteca qué argumentos son obligatorios para el atributo y qué argumentos son opcionales.

 En el ejemplo siguiente se muestra una implementación de un atributo que tiene argumentos posicionales y con nombre.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Design.AttributeAccessorsNamed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessorsNamed/cs/FxCop.Design.AttributeAccessorsNamed.cs#1)]

### <a name="comments"></a>Comentarios
 En el ejemplo siguiente se muestra cómo aplicar el atributo personalizado a dos propiedades.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Design.AttributeAccessorsNamedApplied#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessorsNamedApplied/cs/FxCop.Design.AttributeAccessorsNamedApplied.cs#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1813: Evitar los atributos no sellados](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Consulte también
 [Atributos](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)
