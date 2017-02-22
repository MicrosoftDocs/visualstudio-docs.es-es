---
title: "CA1304: Especificar CultureInfo | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SpecifyCultureInfo"
  - "CA1304"
helpviewer_keywords: 
  - "SpecifyCultureInfo"
  - "CA1304"
ms.assetid: b912d76a-54fd-4c93-b25d-16491e0ae319
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1304: Especificar CultureInfo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SpecifyCultureInfo|  
|Identificador de comprobación|CA1304|  
|Categoría|Microsoft.Globalization|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Un método o constructor llama a un miembro que tiene una sobrecarga que acepta un parámetro <xref:System.Globalization.CultureInfo?displayProperty=fullName> y el método o constructor no llama a la sobrecarga que toma el parámetro <xref:System.Globalization.CultureInfo>.  Esta regla omite las llamadas a los métodos siguientes:  
  
-   <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>  
  
## Descripción de la regla  
 Si no se proporciona un objeto <xref:System.Globalization.CultureInfo> o <xref:System.IFormatProvider?displayProperty=fullName>, el valor predeterminado proporcionado por el miembro sobrecargado podría no surtir el efecto deseado en todas las variables locales.  Además, los miembros de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] eligen la referencia cultural predeterminada y dan formato basándose en suposiciones que podrían ser incorrectas para su código.  Para garantizar que el código funciona como se espera para sus escenarios, debería proporcionar la información específica de la referencia cultural según las instrucciones siguientes:  
  
-   Si el valor se muestra al usuario, utilice la referencia cultural actual.  Vea <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.  
  
-   Si el valor se almacena y se obtiene acceso a él mediante software, eso es, almacenado en un archivo o base de datos, utilice la referencia cultural para todos los idiomas.  Vea <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.  
  
-   Si no conoce el destino del valor, haga que el consumidor o proveedor de datos especifique la referencia cultural.  
  
 Observe que <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> solo se utiliza para recuperar recursos adaptados mediante una instancia de la clase <xref:System.Resources.ResourceManager?displayProperty=fullName>.  
  
 Incluso si el comportamiento predeterminado del miembro sobrecargado es adecuado para sus necesidades, es mejor llamar explícitamente a la sobrecarga específica de la referencia cultural para que el código se autodocumente y se mantenga de forma más sencilla.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, utilice la sobrecarga que toma un <xref:System.Globalization.CultureInfo> o <xref:System.IFormatProvider> y especifique el argumento siguiendo las instrucciones mostradas anteriormente.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla cuando el proveedor de formato\/referencia cultural predeterminado sea la elección correcta, y donde el mantenimiento del código no sea una prioridad de desarrollo importante.  
  
## Ejemplo  
 En el ejemplo siguiente, `BadMethod` causa dos infracciones de esta regla.  `GoodMethod` corrige la primera infracción pasando la referencia cultural de todos los idiomas a System.String.Compare, y corrige la segunda infracción pasando la referencia cultural actual a <xref:System.String.ToLower%2A> puesto que `string3` se muestra al usuario.  
  
 [!code-cs[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_1.cs)]  
  
## Ejemplo  
 El ejemplo siguiente muestra el efecto de la referencia cultural actual en el <xref:System.IFormatProvider> predeterminado seleccionado por el tipo <xref:System.DateTime>.  
  
 [!code-cs[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_2.cs)]  
  
 Este ejemplo produce el siguiente resultado:  
  
  **6\/4\/1900 12:15:12 PM**  
**06\/04\/1900 12:15:12**   
## Reglas relacionadas  
 [CA1305: Especificar IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)  
  
## Vea también  
 [NIB: Using the CultureInfo Class](http://msdn.microsoft.com/es-es/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)