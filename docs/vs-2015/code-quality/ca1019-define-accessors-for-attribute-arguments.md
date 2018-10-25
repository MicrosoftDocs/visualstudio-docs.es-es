---
title: 'CA1019: Definir descriptores de acceso para los argumentos de atributo | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
helpviewer_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ff0329c5c9d565685d4e5c0ff950b31dea3299f6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49854895"
---
# <a name="ca1019-define-accessors-for-attribute-arguments"></a>CA1019: Definir descriptores de acceso para los argumentos de atributo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DefineAccessorsForAttributeArguments|
|Identificador de comprobación|CA1019|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 En su constructor, un atributo define los argumentos que no tienen propiedades correspondientes.

## <a name="rule-description"></a>Descripción de la regla
 Los atributos pueden definir argumentos obligatorios que deben especificarse al aplicar el atributo a un destino. Éstos también se denominan argumentos posicionales porque se proporcionan para atribuir constructores como parámetros posicionales. Para cada argumento obligatorio, el atributo debe proporcionar también una propiedad de sólo lectura correspondiente de modo que el valor del argumento se pueda recuperar en tiempo de ejecución. Esta regla comprueba que para cada parámetro de constructor, ha definido la propiedad correspondiente.

 Los atributos también pueden definir argumentos opcionales, que también se denominan argumentos con nombre. Estos argumentos se proporcionan para atribuir constructores por nombre y deben tener una propiedad de lectura/escritura correspondiente.

 Para los argumentos obligatorios y opcionales, las propiedades correspondientes y los parámetros del constructor deben utilizar el mismo nombre pero distintas mayúsculas y minúsculas. Propiedades usan casillas Pascal de mayúsculas y minúsculas y mayúsculas y minúsculas tipo camel de uso de parámetros.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, agregue una propiedad de solo lectura para cada parámetro de constructor que no tiene uno.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla si no desea que el valor del argumento obligatorio sea recuperable.

## <a name="custom-attributes-example"></a>Ejemplo de atributos personalizados

### <a name="description"></a>Descripción
 El ejemplo siguiente muestra dos atributos que definen un parámetro obligatorio (posicional). La primera implementación del atributo está definida de forma incorrecta. La segunda implementación es correcta.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Design.AttributeAccessors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessors/cs/FxCop.Design.AttributeAccessors.cs#1)]
 [!code-vb[FxCop.Design.AttributeAccessors#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessors/vb/FxCop.Design.AttributeAccessors.vb#1)]

## <a name="positional-and-named-arguments"></a>Argumentos posicionales y con nombre

### <a name="description"></a>Descripción
 Asegúrese de argumentos posicionales y con nombre aclaran a los usuarios de la biblioteca que los argumentos son obligatorios para el atributo y que los argumentos son opcionales.

 El ejemplo siguiente muestra una implementación de un atributo que tiene argumentos posicionales y con nombre.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Design.AttributeAccessorsNamed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessorsNamed/cs/FxCop.Design.AttributeAccessorsNamed.cs#1)]

### <a name="comments"></a>Comentarios
 El ejemplo siguiente muestra cómo aplicar el atributo personalizado a dos propiedades.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Design.AttributeAccessorsNamedApplied#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessorsNamedApplied/cs/FxCop.Design.AttributeAccessorsNamedApplied.cs#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1813: Evitar atributos no sellados](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Vea también
 [Atributos](http://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)



