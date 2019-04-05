---
title: 'CA1704: Los identificadores deben estar escritos correctamente | Documentos de Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d77e5ffcb7cc6688ea07cd99760e79e8f92aeb43
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58996415"
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704: La ortografía de los identificadores debe ser correcta
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldBeSpelledCorrectly|
|Identificador de comprobación|CA1704|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 El nombre de un identificador contiene una o varias palabras que la biblioteca de correctores ortográficos de Microsoft no reconoce. Esta regla no comprueba los constructores ni los miembros con nombres especiales como obtener y establecer los descriptores de acceso de propiedad.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla analiza el identificador en tokens y comprueba la ortografía de cada símbolo. El algoritmo de análisis realiza las siguientes transformaciones:

- Las letras mayúsculas inician un nuevo token. Por ejemplo, MiNombreEsJuan convierte en los tokens "Mi", "Nombre", "Es", "Joe".

- Para varias letras mayúsculas, la última letra mayúscula inicia un nuevo token. Por ejemplo, GUIEditor convierte en los tokens "GUI", "Editor".

- Se quitan los apóstrofos iniciales y finales. Por ejemplo, 'remitente' convierte en el token "remitente".

- Caracteres de subrayado indican el final de un token y se quitan. Por ejemplo, se acorta Hello_world a "Hello", "world".

- Se quita y comercial incrustado. Por ejemplo, para & mat convierte en el token "formato".

  De forma predeterminada, se utiliza la versión inglesa (en) del corrector ortográfico. No hay otros diccionarios de idioma están disponibles actualmente.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, corrija la ortografía de la palabra o agregar la palabra al diccionario personalizado denominado CustomDictionary.xml. Coloque el diccionario en el directorio de instalación de la herramienta, el directorio del proyecto, o en el directorio que está asociado con la herramienta en el perfil del usuario (%USERPROFILE%\Application datos\\...). Para obtener información sobre cómo agregar el diccionario personalizado a un proyecto en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], vea [Cómo: Personalizar el diccionario de análisis de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md)

- Agregar palabras que no deben causar una infracción a la ruta de acceso Dictionary/Words/Recognized.

- Agregue las palabras que deben causar una infracción a la ruta de acceso Dictionary/Words/Unrecognized.

- Agregue las palabras que deben marcarse como obsoletas a la ruta de acceso Dictionary/Words/Deprecated. Consulte el tema de regla relacionado [CA1726: Utilizar términos preferidos](../code-quality/ca1726-use-preferred-terms.md)para obtener más información.

- Agregar excepciones a las reglas de grafía a la ruta de acceso de diccionario acrónimos/Acronyms/CasingExceptions.

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
 Suprimir una advertencia de esta regla sólo si la palabra es intencionalmente incorrecta y la palabra se aplica a un conjunto limitado de la biblioteca. Palabras escritas correctamente reducen la curva de aprendizaje necesaria para las nuevas bibliotecas de software.

## <a name="related-rules"></a>Reglas relacionadas
 [CA2204: Deben escribir correctamente los literales](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

 [CA1703: Cadenas de recursos deberían tener la ortografía correcta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

 [CA1709: Los identificadores deberían escribirse correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Los identificadores deben diferenciarse por algo más que el caso](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: Los identificadores no deberían contener subrayado](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1726: Utilizar términos preferidos](../code-quality/ca1726-use-preferred-terms.md)

## <a name="see-also"></a>Vea también
 [Cómo: Personalizar el diccionario de análisis de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md)
