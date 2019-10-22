---
title: 'CA1704: los identificadores deberían estar escritos correctamente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
helpviewer_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 56ac5e60964621859c77bf53dc4f6c14480b4a83
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669242"
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704: Los identificadores deberían tener la ortografía correcta
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldBeSpelledCorrectly|
|Identificador de comprobación|CA1704|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 El nombre de un identificador contiene una o varias palabras que la biblioteca de corrector ortográfico de Microsoft no reconoce. Esta regla no comprueba los constructores ni los miembros con nombre especial como Get y set Property descriptores de acceso.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla analiza el identificador en tokens y comprueba la ortografía de cada token. El algoritmo de análisis realiza las transformaciones siguientes:

- Las letras mayúsculas inician un nuevo token. Por ejemplo, MyNameIsJoe acorta a "My", "Name", "is", "Joe".

- En el caso de varias letras mayúsculas, la última letra mayúscula inicia un nuevo token. Por ejemplo, GUIEditor acorta a "GUI", "Editor".

- Se quitan los apóstrofos iniciales y finales. Por ejemplo, "Sender" acorta a "Sender".

- Los guiones bajos indican el final de un token y se quitan. Por ejemplo, Hello_world acorta a "Hello", "World".

- Se quitan las y comercial incrustadas. Por ejemplo, para & paspartú acorta a "format".

  De forma predeterminada, se usa la versión en inglés (en) del corrector ortográfico. Actualmente no hay otros diccionarios de idioma disponibles.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, corrija la ortografía de la palabra o agréguela a un diccionario personalizado denominado CustomDictionary. Xml. Coloque el Diccionario en el directorio de instalación de la herramienta, el directorio del proyecto o en el directorio que está asociado a la herramienta en el perfil del usuario (%USERPROFILE%\Application Data \\...). Para obtener información sobre cómo agregar el diccionario personalizado a un proyecto en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], consulte [Cómo: personalizar el Diccionario de análisis de código.](../code-quality/how-to-customize-the-code-analysis-dictionary.md)

- Agregue palabras que no deben provocar una infracción en el Diccionario/palabras/ruta de acceso reconocida.

- Agregue palabras que produzcan una infracción en el Diccionario/palabras/ruta de acceso no reconocida.

- Agregue palabras que se deben marcar como obsoletas en el Diccionario/palabras/ruta de acceso desusada. Vea el tema de la regla relacionada [CA1726: Use los términos preferidos](../code-quality/ca1726-use-preferred-terms.md)para obtener más información.

- Agregue excepciones a las reglas de mayúsculas y minúsculas de acrónimo a la ruta de acceso Dictionary/acrónimos/CasingExceptions.

  El siguiente es un ejemplo de la estructura de un archivo de diccionario personalizado.

```
<Dictionary>
   <Words>
      <Unrecognized>
         <Word>cb</Word>
      </Unrecognized>
      <Recognized>
         <Word>stylesheet</Word>
         <Word>GotDotNet</Word>
      </Recognized>
      <Deprecated>
         <Term PreferredAlternate="EnterpriseServices">ComPlus</Term>
      </Deprecated>
   </Words>
   <Acronyms>
      <CasingExceptions>
         <Acronym>CJK</Acronym>
         <Acronym>Pi</Acronym>
      </CasingExceptions>
   </Acronyms>
</Dictionary>
```

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla solo si la palabra está mal escrita y la palabra se aplica a un conjunto limitado de la biblioteca. Las palabras escritas correctamente reducen la curva de aprendizaje necesaria para las nuevas bibliotecas de software.

## <a name="related-rules"></a>Reglas relacionadas
 [CA2204: Los literales deben estar escritos correctamente ](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

 [CA1703: Las cadenas de recursos deberían tener la ortografía correcta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

 [CA1709: Los identificadores deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Los identificadores se deberían diferenciar en algo más que en el uso de mayúsculas y minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: Los identificadores no deberían contener subrayado](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1726: Utilizar términos preferidos](../code-quality/ca1726-use-preferred-terms.md)

## <a name="see-also"></a>Vea también
 [Cómo: Personalizar el diccionario de análisis de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md)
