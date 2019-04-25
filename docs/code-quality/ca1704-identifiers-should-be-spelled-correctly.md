---
title: 'CA1704: La ortografía de los identificadores debe ser correcta'
ms.date: 03/28/2018
ms.topic: reference
f1_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
helpviewer_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8dbfc8081f980b7b9e978da782f1627a88a716a3
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55941289"
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704: La ortografía de los identificadores debe ser correcta

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

## <a name="language"></a>Lenguaje

El corrector ortográfico comprueba actualmente sólo con los diccionarios de la referencia cultural en inglés. Puede cambiar la referencia cultural de su proyecto en el archivo de proyecto, agregando la **CodeAnalysisCulture** elemento.

Por ejemplo:

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> Si la referencia cultural se establece en algo distinto de una referencia cultural de inglés, esta regla de análisis de código se deshabilita de forma silenciosa.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, corrija la ortografía de la palabra o agregar la palabra a un diccionario personalizado.

### <a name="to-add-words-to-a-custom-dictionary"></a>Para agregar palabras a un diccionario personalizado

Nombre del archivo de diccionario personalizado XML *CustomDictionary.xml*. Coloque el diccionario en el directorio de instalación de la herramienta, el directorio del proyecto, o en el directorio que está asociado con la herramienta en el perfil del usuario (*%USERPROFILE%\Application datos\\...* ). Para saber cómo agregar el diccionario personalizado a un proyecto en Visual Studio, vea [Cómo: Personalizar el diccionario de análisis de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

- Agregar palabras que no deben causar una infracción a la ruta de acceso Dictionary/Words/Recognized.

- Agregue las palabras que deben causar una infracción a la ruta de acceso Dictionary/Words/Unrecognized.

- Agregue las palabras que deben marcarse como obsoletas a la ruta de acceso Dictionary/Words/Deprecated. Consulte el tema de regla relacionado [CA1726: Utilice términos preferidos](../code-quality/ca1726-use-preferred-terms.md) para obtener más información.

- Agregar excepciones a las reglas de grafía a la ruta de acceso de diccionario acrónimos/Acronyms/CasingExceptions.

El siguiente es un ejemplo de la estructura de un archivo de diccionario personalizado:

```xml
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

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Suprimir una advertencia de esta regla sólo si la palabra es intencionalmente incorrecta y la palabra se aplica a un conjunto limitado de la biblioteca. Palabras escritas correctamente reducen la curva de aprendizaje necesaria para las nuevas bibliotecas de software.

## <a name="related-rules"></a>Reglas relacionadas

- [CA2204: Deben escribir correctamente los literales](../code-quality/ca2204-literals-should-be-spelled-correctly.md)
- [CA1703: Cadenas de recursos deberían tener la ortografía correcta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1709: Los identificadores deberían escribirse correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Los identificadores deben diferenciarse por algo más que el caso](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
- [CA1707: Los identificadores no deberían contener subrayado](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
- [CA1726: Utilizar términos preferidos](../code-quality/ca1726-use-preferred-terms.md)

## <a name="see-also"></a>Vea también

- [Cómo: Personalizar el diccionario de análisis de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md)
