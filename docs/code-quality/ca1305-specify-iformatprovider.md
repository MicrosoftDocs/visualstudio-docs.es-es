---
title: 'CA1305: Especificar IFormatProvider'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyIFormatProvider
- CA1305
helpviewer_keywords:
- CA1305
- SpecifyIFormatProvider
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 73ac9fe384088d509d7eee800b066571f995dd24
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305: Especificar IFormatProvider
|||
|-|-|
|TypeName|SpecifyIFormatProvider|
|Identificador de comprobación|CA1305|
|Categoría|Microsoft.Globalization|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un método o constructor llama a uno o más miembros que tienen sobrecargas que aceptan un <xref:System.IFormatProvider?displayProperty=fullName> parámetro y el método o constructor no llama a la sobrecarga que toma el <xref:System.IFormatProvider> parámetro. Esta regla omite las llamadas a [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] métodos que se documentan omitiendo el <xref:System.IFormatProvider> parámetro y, además, los métodos siguientes:

-   <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>

-   <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>

-   <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>

## <a name="rule-description"></a>Descripción de la regla
 Cuando un <xref:System.Globalization.CultureInfo?displayProperty=fullName> o <xref:System.IFormatProvider> no se proporciona el objeto, el valor de predeterminado proporcionado por el miembro sobrecargado podría no surtir el efecto deseado en todas las configuraciones regionales. Además, [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] miembros eligen la referencia cultural predeterminada y dan formato basándose en suposiciones que pueden no ser correctas para el código. Para asegurarse de que el código funciona según lo previsto para los escenarios, también debe proporcionar información de referencia cultural según las instrucciones siguientes:

-   Si el valor se mostrará al usuario, use la referencia cultural actual. Vea <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.

-   Si el valor se almacena y se tiene acceso por software (guardado en un archivo o base de datos), utilice la referencia cultural invariable. Vea <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.

-   Si no conoce el destino del valor, tiene el consumidor de datos o proveedor de especificar la referencia cultural.

 Tenga en cuenta que <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> sólo se utiliza para recuperar recursos localizados mediante una instancia de la <xref:System.Resources.ResourceManager?displayProperty=fullName> clase.

 Aunque el comportamiento predeterminado del miembro sobrecargado es adecuado para sus necesidades, es mejor llamar explícitamente a la sobrecarga de la referencia cultural específica para que el código sea más fácil de mantener y documenten por sí mismos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, utilice la sobrecarga que toma un <xref:System.Globalization.CultureInfo> o <xref:System.IFormatProvider> y especifique el argumento siguiendo las instrucciones que se han mencionado anteriormente.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla cuando se tiene la certeza de que el proveedor de formato/referencia cultural predeterminada es la elección correcta y donde el mantenimiento del código no es una prioridad de desarrollo importante.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente, `BadMethod` hace dos infracciones de esta regla. `GoodMethod` corrige la primera infracción pasando la referencia cultural invariable a <xref:System.String.Compare%2A>y corrige la segunda infracción pasando la referencia cultural actual a <xref:System.String.ToLower%2A> porque `string3` se muestra al usuario.

 [!code-csharp[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1305-specify-iformatprovider_1.cs)]

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra el efecto de la referencia cultural actual en el valor predeterminado <xref:System.IFormatProvider> que está activada de forma el <xref:System.DateTime> tipo.

 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1305-specify-iformatprovider_2.cs)]

 Este ejemplo produce el siguiente resultado:

 **6/4/1900 12:15:12 PM**
 ** /06/04/1900 12:15:12**
## <a name="related-rules"></a>Reglas relacionadas
 [CA1304: Especificar CultureInfo](../code-quality/ca1304-specify-cultureinfo.md)

## <a name="see-also"></a>Vea también
[Uso de la clase CultureInfo](/dotnet/standard/globalization-localization/globalization#Cultures)