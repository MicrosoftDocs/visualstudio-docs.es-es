---
title: 'CA1302: No codificar las cadenas específicas de configuración regional'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
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
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e56c57343ae61709b6d5875c865857a7475363fd
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550497"
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
 El <xref:System.Environment.SpecialFolder?displayProperty=fullName> enumeración contiene miembros que hacen referencia a las carpetas del sistema especiales. Las ubicaciones de estas carpetas pueden tener valores diferentes en distintos sistemas operativos, el usuario puede cambiar algunas de las ubicaciones y las ubicaciones están localizadas. Un ejemplo de una carpeta especial es la carpeta del sistema, que es "C:\WINDOWS\system32" en [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)] pero "C:\WINNT\system32" en [!INCLUDE[win2kfamily](../code-quality/includes/win2kfamily_md.md)]. El <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> método devuelve las ubicaciones que están asociadas con el <xref:System.Environment.SpecialFolder> enumeración. Las ubicaciones devueltas por <xref:System.Environment.GetFolderPath%2A> están localizados y adecuados para el equipo que se está ejecutando.

 Esta regla acorta las rutas de acceso de carpeta que se recuperan mediante el <xref:System.Environment.GetFolderPath%2A> método en los niveles de directorio independiente. Cada literal de cadena se compara con los tokens. Si se encuentra una coincidencia, se supone que el método genera una cadena que hace referencia a la ubicación del sistema que está asociada con el token. Para la portabilidad y localizabilidad, utilice el <xref:System.Environment.GetFolderPath%2A> método para recuperar las ubicaciones de las carpetas especiales del sistema en lugar de utilizar literales de cadena.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, recupere la ubicación mediante el <xref:System.Environment.GetFolderPath%2A> método.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el literal de cadena no se usa para hacer referencia a una de las ubicaciones del sistema que está asociado el <xref:System.Environment.SpecialFolder> enumeración.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente genera la ruta de acceso de la carpeta de datos de aplicación comunes, que genera tres advertencias de esta regla. A continuación, en el ejemplo se recupera la ruta de acceso mediante la <xref:System.Environment.GetFolderPath%2A> método.

 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/CSharp/ca1302-do-not-hardcode-locale-specific-strings_1.cs)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/VisualBasic/ca1302-do-not-hardcode-locale-specific-strings_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1303: No pasar literales como parámetros localizados](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)