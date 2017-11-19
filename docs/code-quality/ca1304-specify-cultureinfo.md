---
title: 'CA1304: Especificar CultureInfo | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SpecifyCultureInfo
- CA1304
helpviewer_keywords:
- SpecifyCultureInfo
- CA1304
ms.assetid: b912d76a-54fd-4c93-b25d-16491e0ae319
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4cd654145fed46594fd2fcd076a20b30e393a23b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ca1304-specify-cultureinfo"></a>CA1304: Especificar CultureInfo
|||  
|-|-|  
|TypeName|SpecifyCultureInfo|  
|Identificador de comprobación|CA1304|  
|Categoría|Microsoft.Globalization|  
|Cambio problemático|Poco problemático|  
  
## <a name="cause"></a>Motivo  
 Un método o constructor llama a un miembro que tiene una sobrecarga que acepta un <xref:System.Globalization.CultureInfo?displayProperty=fullName> parámetro y el método o constructor no llama a la sobrecarga que toma el <xref:System.Globalization.CultureInfo> parámetro. Esta regla omite las llamadas a los métodos siguientes:  
  
-   <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>  
  
## <a name="rule-description"></a>Descripción de la regla  
 Cuando un <xref:System.Globalization.CultureInfo> o <xref:System.IFormatProvider?displayProperty=fullName> no se proporciona el objeto, el valor de predeterminado proporcionado por el miembro sobrecargado podría no surtir el efecto deseado en todas las configuraciones regionales. Además, [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] miembros eligen la referencia cultural predeterminada y dan formato basándose en suposiciones que pueden no ser correctas para el código. Para asegurarse de que el código funciona según lo previsto para los escenarios, también debe proporcionar información de referencia cultural según las instrucciones siguientes:  
  
-   Si el valor se mostrará al usuario, use la referencia cultural actual. Consulta <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.  
  
-   Si el valor se almacena y se tiene acceso con el software, es decir, almacenado en un archivo o base de datos, utilice la referencia cultural invariable. Consulta <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.  
  
-   Si no conoce el destino del valor, tiene el consumidor de datos o proveedor de especificar la referencia cultural.  
  
 Tenga en cuenta que <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> sólo se utiliza para recuperar recursos localizados mediante una instancia de la <xref:System.Resources.ResourceManager?displayProperty=fullName> clase.  
  
 Aunque el comportamiento predeterminado del miembro sobrecargado es adecuado para sus necesidades, es mejor llamar explícitamente a la sobrecarga de la referencia cultural específica para que el código sea más fácil de mantener y documenten por sí mismos.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, utilice la sobrecarga que toma un <xref:System.Globalization.CultureInfo> o <xref:System.IFormatProvider> y especifique el argumento siguiendo las instrucciones que se han mencionado anteriormente.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla cuando se tiene la certeza de que el proveedor de formato/referencia cultural predeterminada es la elección correcta y donde el mantenimiento del código no es una prioridad de desarrollo importante.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, `BadMethod` hace dos infracciones de esta regla. `GoodMethod`corrige la primera infracción pasando la referencia cultural de todos los idiomas a System.String.Compare y corrige la segunda infracción pasando la referencia cultural actual a <xref:System.String.ToLower%2A> porque `string3` se muestra al usuario.  
  
 [!code-csharp[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_1.cs)]  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el efecto de la referencia cultural actual en el valor predeterminado <xref:System.IFormatProvider> que está activada de forma el <xref:System.DateTime> tipo.  
  
 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_2.cs)]  
  
 Este ejemplo produce el siguiente resultado:  
  
 **6/4/1900 12:15:12 PM**  
**06/04/1900 12:15:12**   
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1305: Especificar IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)  
  
## <a name="see-also"></a>Vea también  
[Uso de la clase CultureInfo](/dotnet/standard/globalization-localization/globalization#Cultures)  