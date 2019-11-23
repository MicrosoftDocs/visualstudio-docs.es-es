---
title: 'CA1304: Especifique CultureInfo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyCultureInfo
- CA1304
helpviewer_keywords:
- SpecifyCultureInfo
- CA1304
ms.assetid: b912d76a-54fd-4c93-b25d-16491e0ae319
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 202f3759026bbedd5e99e94bba76e956b83357b3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661469"
---
# <a name="ca1304-specify-cultureinfo"></a>CA1304: Especificar CultureInfo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyCultureInfo|
|Identificador de comprobación|CA1304|
|Categoría|Microsoft. Globalization|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un método o constructor llama a un miembro que tiene una sobrecarga que acepta un parámetro <xref:System.Globalization.CultureInfo?displayProperty=fullName>, y el método o constructor no llama a la sobrecarga que toma el parámetro <xref:System.Globalization.CultureInfo>. Esta regla omite las llamadas a los métodos siguientes:

- <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>

## <a name="rule-description"></a>Descripción de la regla
 Cuando no se proporciona un objeto <xref:System.Globalization.CultureInfo> o <xref:System.IFormatProvider?displayProperty=fullName>, es posible que el valor predeterminado proporcionado por el miembro sobrecargado no tenga el efecto deseado en todas las configuraciones regionales. Además, los miembros de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] eligen la referencia cultural y el formato predeterminados en función de las suposiciones que podrían no ser correctas para el código. Para asegurarse de que el código funciona según lo previsto en los escenarios, debe proporcionar información específica de la referencia cultural según las siguientes directrices:

- Si el valor se va a mostrar al usuario, use la referencia cultural actual. Vea <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.

- Si el valor se almacenará y tendrá acceso a él mediante software, es decir, se conserva en un archivo o base de datos, use la referencia cultural de todos los idiomas. Vea <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.

- Si no conoce el destino del valor, haga que el consumidor de datos o el proveedor especifiquen la referencia cultural.

  Tenga en cuenta que <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> solo se utiliza para recuperar recursos localizados mediante una instancia de la clase <xref:System.Resources.ResourceManager?displayProperty=fullName>.

  Incluso si el comportamiento predeterminado del miembro sobrecargado es adecuado para sus necesidades, es mejor llamar explícitamente a la sobrecarga específica de la referencia cultural para que el código se autodocumente y se mantenga más fácilmente.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, use la sobrecarga que toma un <xref:System.Globalization.CultureInfo> o <xref:System.IFormatProvider> y especifique el argumento de acuerdo con las instrucciones que se enumeraron anteriormente.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla cuando está seguro de que el proveedor de formato o referencia cultural predeterminado es la opción correcta, y donde el mantenimiento del código no es una prioridad de desarrollo importante.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente, `BadMethod` provoca dos infracciones de esta regla. `GoodMethod` corrige la primera infracción pasando la referencia cultural de todos los idiomas a System. String. Compare y corrige la segunda infracción pasando la referencia cultural actual a <xref:System.String.ToLower%2A> porque `string3` se muestra al usuario.

 [!code-csharp[FxCop.Globalization.CultureInfo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.CultureInfo/cs/FxCop.Globalization.CultureInfo.cs#1)]

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra el efecto de la referencia cultural actual en el <xref:System.IFormatProvider> predeterminado seleccionado por el tipo de <xref:System.DateTime>.

 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.IFormatProvider/cs/FxCop.Globalization.IFormatProvider.cs#1)]

 Este ejemplo produce el siguiente resultado:

 **4/6/1900 12:15:12 PM**
 **/06/04/1900 12:15:12**
## <a name="related-rules"></a>Reglas relacionadas
 [CA1305: Especificar IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)

## <a name="see-also"></a>Vea también
 [NIB: usar la clase CultureInfo](https://msdn.microsoft.com/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)
