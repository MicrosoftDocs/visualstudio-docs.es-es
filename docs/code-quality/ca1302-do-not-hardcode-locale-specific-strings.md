---
title: "CA1302: No codificar las cadenas espec&#237;ficas de configuraci&#243;n regional | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotHardcodeLocaleSpecificStrings"
  - "CA1302"
helpviewer_keywords: 
  - "DoNotHardcodeLocaleSpecificStrings"
  - "CA1302"
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1302: No codificar las cadenas espec&#237;ficas de configuraci&#243;n regional
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotHardcodeLocaleSpecificStrings|  
|Identificador de comprobación|CA1302|  
|Categoría|Microsoft.Globalization|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Un método utiliza un literal de cadena que representa parte de la ruta de acceso de determinadas carpetas del sistema.  
  
## Descripción de la regla  
 La enumeración <xref:System.Environment.SpecialFolder?displayProperty=fullName> contiene miembros que hacen referencia a carpetas del sistema especiales.  La ubicación de estas carpetas puede tener diferentes valores en sistemas operativos distintos, el usuario puede cambiar alguna de estas ubicaciones y además, están adaptadas.  Un ejemplo de carpeta especial es la carpeta System, que es la carpeta "C:\\WINDOWS\\system32" en [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)], pero "C:\\WINNT\\system32" en [!INCLUDE[win2kfamily](../code-quality/includes/win2kfamily_md.md)].  El método <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> devuelve las ubicaciones asociadas a la enumeración <xref:System.Environment.SpecialFolder>.  Las ubicaciones devueltas por <xref:System.Environment.GetFolderPath%2A> se adaptan y se adecuan al equipo actualmente en ejecución.  
  
 Esta regla asigna un símbolo \(token\) a las rutas de acceso de la carpeta recuperadas mediante el método <xref:System.Environment.GetFolderPath%2A> en niveles de directorio independientes.  Cada literal de cadena se compara con los tokens.  Si se encuentra alguna coincidencia, se supone que el método compila una cadena que hace referencia a la ubicación del sistema asociada al token.  Para la portabilidad y adaptabilidad, utilice el método <xref:System.Environment.GetFolderPath%2A> para recuperar las ubicaciones de las carpetas del sistema especiales en lugar de utilizar los literales de cadena.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, recupere la ubicación mediante el método <xref:System.Environment.GetFolderPath%2A>.  
  
## Cuándo suprimir advertencias  
 Suprimir las advertencias de esta regla es un método seguro si el literal de cadena no se usa para hacer referencia a una de las ubicaciones del sistema asociadas a la enumeración <xref:System.Environment.SpecialFolder>.  
  
## Ejemplo  
 El ejemplo siguiente compila la ruta de acceso de la carpeta de datos de la aplicación común, que genera tres advertencias de esta regla.  Después, el ejemplo recupera la ruta de acceso mediante el método <xref:System.Environment.GetFolderPath%2A>.  
  
 [!code-cs[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/CSharp/ca1302-do-not-hardcode-locale-specific-strings_1.cs)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/VisualBasic/ca1302-do-not-hardcode-locale-specific-strings_1.vb)]  
  
## Reglas relacionadas  
 [CA1303: No pasar literales como parámetros localizados](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)