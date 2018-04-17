---
title: 'CA1302: No codificar las cadenas específicas de configuración regional | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
helpviewer_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f01bcbf0d717ff8728d87b55f2cfd1c7c5af34d3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302: No codificar las cadenas específicas de configuración regional
|||  
|-|-|  
|TypeName|DoNotHardcodeLocaleSpecificStrings|  
|Identificador de comprobación|CA1302|  
|Categoría|Microsoft.Globalization|  
|Cambio problemático|Poco problemático|  
  
## <a name="cause"></a>Motivo  
 Un método utiliza un literal de cadena que representa la parte de la ruta de acceso de determinadas carpetas del sistema.  
  
## <a name="rule-description"></a>Descripción de la regla  
 El <xref:System.Environment.SpecialFolder?displayProperty=fullName> enumeración contiene miembros que hacen referencia a carpetas del sistema especiales. Las ubicaciones de estas carpetas pueden tener diferentes valores en sistemas operativos distintos, el usuario puede cambiar alguna de las ubicaciones y además, están adaptadas. Un ejemplo de una carpeta especial es la carpeta del sistema, que es "C:\WINDOWS\system32" en [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)] "c:\Winnt\System32" en [!INCLUDE[win2kfamily](../code-quality/includes/win2kfamily_md.md)]. El <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> método devuelve las ubicaciones que están asociadas a la <xref:System.Environment.SpecialFolder> enumeración. Las ubicaciones que se devuelven por <xref:System.Environment.GetFolderPath%2A> están localizados y adecuados para el equipo que se está ejecutando.  
  
 Esta regla acorta las rutas de acceso de carpeta que se recuperan mediante el uso de la <xref:System.Environment.GetFolderPath%2A> método en niveles de directorio independiente. Cada literal de cadena se compara con los tokens. Si se encuentra una coincidencia, se supone que el método genera una cadena que hace referencia a la ubicación del sistema que está asociada con el token. Portabilidad y adaptabilidad, utilice el <xref:System.Environment.GetFolderPath%2A> método para recuperar las ubicaciones de las carpetas del sistema especiales en lugar de usar literales de cadena.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, recuperar la ubicación mediante la <xref:System.Environment.GetFolderPath%2A> método.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla si el literal de cadena no se usa para hacer referencia a una de las ubicaciones del sistema que está asociado el <xref:System.Environment.SpecialFolder> enumeración.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la ruta de acceso de la carpeta de datos de aplicación común, que genera tres advertencias de esta regla. A continuación, en el ejemplo se recupera la ruta de acceso mediante el <xref:System.Environment.GetFolderPath%2A> método.  
  
 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/CSharp/ca1302-do-not-hardcode-locale-specific-strings_1.cs)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/VisualBasic/ca1302-do-not-hardcode-locale-specific-strings_1.vb)]  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1303: No pasar literales como parámetros localizados](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)