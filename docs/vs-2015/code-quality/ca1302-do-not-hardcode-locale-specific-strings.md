---
title: 'CA1302: no codificar cadenas específicas de la configuración regional | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
helpviewer_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6e16fff154b5c0df660b06e5bf9e9e838762adff
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661474"
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302: No codificar las cadenas específicas de configuración regional
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotHardcodeLocaleSpecificStrings|
|Identificador de comprobación|CA1302|
|Categoría|Microsoft. Globalization|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un método utiliza un literal de cadena que representa parte de la ruta de acceso de ciertas carpetas del sistema.

## <a name="rule-description"></a>Descripción de la regla
 La enumeración <xref:System.Environment.SpecialFolder?displayProperty=fullName> contiene miembros que hacen referencia a carpetas especiales del sistema. Las ubicaciones de estas carpetas pueden tener valores diferentes en distintos sistemas operativos, el usuario puede cambiar algunas de las ubicaciones y se localizan las ubicaciones. Un ejemplo de una carpeta especial es la carpeta del sistema, que es "C:\WINDOWS\system32" en [!INCLUDE[winxp](../includes/winxp-md.md)] pero "C:\WINNT\system32" en [!INCLUDE[win2kfamily](../includes/win2kfamily-md.md)]. El método <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> devuelve las ubicaciones que están asociadas a la enumeración <xref:System.Environment.SpecialFolder>. Las ubicaciones devueltas por <xref:System.Environment.GetFolderPath%2A> están localizadas y adecuadas para el equipo que se está ejecutando actualmente.

 Esta regla acorta las rutas de carpeta que se recuperan mediante el método <xref:System.Environment.GetFolderPath%2A> en niveles de directorio independientes. Cada literal de cadena se compara con los tokens. Si se encuentra una coincidencia, se supone que el método está compilando una cadena que hace referencia a la ubicación del sistema asociada al token. Para la portabilidad y la localizabilidad, utilice el método <xref:System.Environment.GetFolderPath%2A> para recuperar las ubicaciones de las carpetas especiales del sistema en lugar de utilizar literales de cadena.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, recupere la ubicación mediante el método <xref:System.Environment.GetFolderPath%2A>.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el literal de cadena no se utiliza para hacer referencia a una de las ubicaciones del sistema asociadas a la enumeración de <xref:System.Environment.SpecialFolder>.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se crea la ruta de acceso de la carpeta de datos de la aplicación común, que genera tres advertencias de esta regla. A continuación, en el ejemplo se recupera la ruta de acceso mediante el método <xref:System.Environment.GetFolderPath%2A>.

 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/cs/FxCop.Globalization.HardcodedLocaleStrings.cs#1)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/vb/FxCop.Globalization.HardcodedLocaleStrings.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1303: No pasar literales como parámetros localizados](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)
