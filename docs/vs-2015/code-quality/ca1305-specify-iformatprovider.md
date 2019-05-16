---
title: 'CA1305: Especificar IFormatProvider | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyIFormatProvider
- CA1305
helpviewer_keywords:
- CA1305
- SpecifyIFormatProvider
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 93bf7f17f77008ce8e9898c1871926edf2e8439f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694772"
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305: Especificar IFormatProvider
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyIFormatProvider|
|Identificador de comprobación|CA1305|
|Categoría|Microsoft.Globalization|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un método o constructor llama a uno o más miembros que tienen sobrecargas que aceptan un <xref:System.IFormatProvider?displayProperty=fullName> parámetro y el método o constructor no llama a la sobrecarga que toma el <xref:System.IFormatProvider> parámetro. Esta regla omite las llamadas a [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] métodos que se documentan omitiendo el <xref:System.IFormatProvider> parámetro y, además, los métodos siguientes:

- <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>

## <a name="rule-description"></a>Descripción de la regla
 Cuando un <xref:System.Globalization.CultureInfo?displayProperty=fullName> o <xref:System.IFormatProvider> objeto no se proporciona, el valor predeterminado proporcionado por el miembro sobrecargado podría no tener el efecto deseado en todas las configuraciones regionales. Además, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] miembros eligen la referencia cultural predeterminada y el formato basado en suposiciones que pueden no ser correctas para su código. Para asegurarse de que el código funciona según lo esperado para sus escenarios, debería proporcionar información de referencia cultural específica según las siguientes directrices:

- Si el valor se mostrará al usuario, use la referencia cultural actual. Vea <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.

- Si el valor se almacenará y acceso a software (guardado en un archivo o base de datos), use la referencia cultural invariable. Vea <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.

- Si no conoce el destino del valor, tiene el consumidor de datos o proveedor de especificar la referencia cultural.

  Tenga en cuenta que <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> sólo se utiliza para recuperar recursos localizados mediante el uso de una instancia de la <xref:System.Resources.ResourceManager?displayProperty=fullName> clase.

  Aunque el comportamiento predeterminado del miembro sobrecargado es adecuado para sus necesidades, es mejor llamar explícitamente a la sobrecarga de la referencia cultural específica para que el código sea más fácil de mantener y documenten por sí mismos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, use la sobrecarga que toma un <xref:System.Globalization.CultureInfo> o <xref:System.IFormatProvider> y especifique el argumento siguiendo las instrucciones que se han mencionado anteriormente.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla cuando está seguro de que el proveedor de la referencia cultural o el formato predeterminado es la elección correcta y donde el mantenimiento del código no es una prioridad de desarrollo importante.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente, `BadMethod` hace que dos infracciones de esta regla. `GoodMethod` corrige la primera infracción pasando la referencia cultural a <xref:System.String.Compare%2A>y corrige la segunda infracción pasando la referencia cultural actual a <xref:System.String.ToLower%2A> porque `string3` se muestra al usuario.

 [!code-csharp[FxCop.Globalization.CultureInfo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.CultureInfo/cs/FxCop.Globalization.CultureInfo.cs#1)]

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra el efecto de la referencia cultural actual en el valor predeterminado <xref:System.IFormatProvider> está activada de manera el <xref:System.DateTime> tipo.

 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.IFormatProvider/cs/FxCop.Globalization.IFormatProvider.cs#1)]

 Este ejemplo produce el siguiente resultado:

 **4/6/1900 12:15:12 PM**
 **/06/04/1900 12:15:12**
## <a name="related-rules"></a>Reglas relacionadas
 [CA1304: Especificar CultureInfo](../code-quality/ca1304-specify-cultureinfo.md)

## <a name="see-also"></a>Vea también
 [NIB: Uso de la clase CultureInfo](https://msdn.microsoft.com/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)
