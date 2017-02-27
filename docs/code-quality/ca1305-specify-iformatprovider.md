---
title: "CA1305: Especificar IFormatProvider | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SpecifyIFormatProvider"
  - "CA1305"
helpviewer_keywords: 
  - "CA1305"
  - "SpecifyIFormatProvider"
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 22
---
# CA1305: Especificar IFormatProvider
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SpecifyIFormatProvider|  
|Identificador de comprobación|CA1305|  
|Categoría|Microsoft.Globalization|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Un método o constructor llama a uno o más miembros que tiene sobrecargas que aceptan un parámetro <xref:System.IFormatProvider?displayProperty=fullName>, y el método o constructor no llama a la sobrecarga que toma el parámetro <xref:System.IFormatProvider>.  Esta regla omite las llamadas a métodos de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que se documentan omitiendo el parámetro <xref:System.IFormatProvider> y junto con los métodos siguientes:  
  
-   <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>  
  
## Descripción de la regla  
 Si no se proporciona un objeto <xref:System.Globalization.CultureInfo?displayProperty=fullName> o <xref:System.IFormatProvider>, el valor predeterminado proporcionado por el miembro sobrecargado podría no surtir el efecto deseado en todas las variables locales.  Además, los miembros de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] eligen la referencia cultural predeterminada y dan formato basándose en suposiciones que podrían ser incorrectas para su código.  Para asegurarse de que el código funciona como se espera para sus escenarios, debería proporcionar la información específica de la referencia cultural según las instrucciones siguientes:  
  
-   Si el valor se muestra al usuario, utilice la referencia cultural actual.  Vea <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.  
  
-   Si el valor se almacena y se obtiene acceso a él mediante software \(almacenado en un archivo o base de datos\) utilice la referencia cultural para todos los idiomas.  Vea <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.  
  
-   Si no conoce el destino del valor, haga que el consumidor o proveedor de datos especifique la referencia cultural.  
  
 Observe que <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> solo se utiliza para recuperar recursos adaptados mediante una instancia de la clase <xref:System.Resources.ResourceManager?displayProperty=fullName>.  
  
 Incluso si el comportamiento predeterminado del miembro sobrecargado es adecuado para sus necesidades, es mejor llamar explícitamente a la sobrecarga específica de la referencia cultural para que el código se autodocumente y se mantenga de forma más sencilla.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, utilice la sobrecarga que toma un <xref:System.Globalization.CultureInfo> o <xref:System.IFormatProvider> y especifique el argumento siguiendo las instrucciones mostradas anteriormente.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla cuando el proveedor de formato\/referencia cultural predeterminado sea la elección correcta y donde el mantenimiento del código no sea una prioridad de desarrollo importante.  
  
## Ejemplo  
 En el ejemplo siguiente, `BadMethod` causa dos infracciones de esta regla.  `GoodMethod` corrige la primera infracción pasando la referencia cultural de todos los idiomas a <xref:System.String.Compare%2A> y corrige la segunda infracción pasando la referencia cultural actual a <xref:System.String.ToLower%2A> puesto que `string3` se muestra al usuario.  
  
 [!code-cs[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1305-specify-iformatprovider_1.cs)]  
  
## Ejemplo  
 El ejemplo siguiente muestra el efecto de la referencia cultural actual en el <xref:System.IFormatProvider> predeterminado seleccionado por el tipo <xref:System.DateTime>.  
  
 [!code-cs[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1305-specify-iformatprovider_2.cs)]  
  
 Este ejemplo produce el siguiente resultado:  
  
  **6\/4\/1900 12:15:12 PM**  
**06\/04\/1900 12:15:12**   
## Reglas relacionadas  
 [CA1304: Especificar CultureInfo](../code-quality/ca1304-specify-cultureinfo.md)  
  
## Vea también  
 [NIB: Using the CultureInfo Class](http://msdn.microsoft.com/es-es/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)