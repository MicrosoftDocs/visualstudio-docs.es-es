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
ms.openlocfilehash: 18da0471b1ac62f0e61b303c60b46c15cdc2e428
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539014"
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302: No codificar las cadenas específicas de configuración regional
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|DoNotHardcodeLocaleSpecificStrings|
|Identificador de comprobación|CA1302|
|Category|Microsoft. Globalization|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
 Un método utiliza un literal de cadena que representa parte de la ruta de acceso de ciertas carpetas del sistema.

## <a name="rule-description"></a>Descripción de la regla
 La <xref:System.Environment.SpecialFolder?displayProperty=fullName> enumeración contiene miembros que hacen referencia a carpetas especiales del sistema. Las ubicaciones de estas carpetas pueden tener valores diferentes en distintos sistemas operativos, el usuario puede cambiar algunas de las ubicaciones y se localizan las ubicaciones. Un ejemplo de una carpeta especial es la carpeta del sistema, que es "C:\WINDOWS\system32" en, [!INCLUDE[winxp](../includes/winxp-md.md)] pero "C:\winnt\system32" en [!INCLUDE[win2kfamily](../includes/win2kfamily-md.md)] . El <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> método devuelve las ubicaciones que están asociadas a la <xref:System.Environment.SpecialFolder> enumeración. Las ubicaciones devueltas por <xref:System.Environment.GetFolderPath%2A> se localizan y son adecuadas para el equipo que se está ejecutando actualmente.

 Esta regla acorta las rutas de acceso de carpetas que se recuperan mediante el <xref:System.Environment.GetFolderPath%2A> método en niveles de directorio independientes. Cada literal de cadena se compara con los tokens. Si se encuentra una coincidencia, se supone que el método está compilando una cadena que hace referencia a la ubicación del sistema asociada al token. Para la portabilidad y la localizabilidad, utilice el <xref:System.Environment.GetFolderPath%2A> método para recuperar las ubicaciones de las carpetas especiales del sistema en lugar de utilizar literales de cadena.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, recupere la ubicación mediante el <xref:System.Environment.GetFolderPath%2A> método.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el literal de cadena no se utiliza para hacer referencia a una de las ubicaciones del sistema asociadas a la <xref:System.Environment.SpecialFolder> enumeración.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se crea la ruta de acceso de la carpeta de datos de la aplicación común, que genera tres advertencias de esta regla. A continuación, en el ejemplo se recupera la ruta de acceso mediante el <xref:System.Environment.GetFolderPath%2A> método.

 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/cs/FxCop.Globalization.HardcodedLocaleStrings.cs#1)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/vb/FxCop.Globalization.HardcodedLocaleStrings.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1303: No pasar literales como parámetros localizados](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)
