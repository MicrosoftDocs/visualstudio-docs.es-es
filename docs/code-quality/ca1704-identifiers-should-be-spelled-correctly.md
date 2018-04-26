---
title: 'CA1704: Los identificadores deberían tener la ortografía correcta'
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 710e18f4ce8199c76c34683c510d3a64160544e6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704: Los identificadores deberían tener la ortografía correcta

|||
|-|-|
|TypeName|IdentifiersShouldBeSpelledCorrectly|
|Identificador de comprobación|CA1704|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo

El nombre de un identificador contiene una o varias palabras que no son reconocidas por la biblioteca de correctores ortográficos de Microsoft. Esta regla no comprueba los constructores ni los miembros con nombres especiales, como get y establecer los descriptores de acceso de propiedad.

## <a name="rule-description"></a>Descripción de la regla

Esta regla analiza el identificador en tokens y comprueba la ortografía de cada token. El algoritmo de análisis realiza las transformaciones siguientes:

- Las letras mayúsculas inician un nuevo token. Por ejemplo, MiNombreEsJuan acorta "Mi", "Name", "Es", "Joe".

- Para varias letras mayúsculas, la última letra mayúscula inicia un nuevo token. Por ejemplo, GUIEditor acorta "GUI", "Editor".

- Se quitan los apóstrofos iniciales y finales. Por ejemplo, 'remitente' acorta "remitente".

- Caracteres de subrayado significan el final de un token y se quitan. Por ejemplo, acorta Hello_world en "Hello", "world".

- Se quitan y comerciales incrustados. Por ejemplo, para & Esterilla acorta para "format".

## <a name="language"></a>Lenguaje

El corrector ortográfico comprueba actualmente solo con los diccionarios de la referencia cultural basada en inglés. Puede cambiar la referencia cultural del proyecto en el archivo de proyecto, agregando la **CodeAnalysisCulture** elemento.

Por ejemplo:

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> Si establece la referencia cultural a algo distinto de una referencia cultural basada en inglés, esta regla de análisis de código está deshabilitada en modo silencioso.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, corrija la ortografía de la palabra o agregue la palabra a un diccionario personalizado.

### <a name="to-add-words-to-a-custom-dictionary"></a>Para agregar palabras a un diccionario personalizado

Asignar nombre al archivo de diccionario personalizado XML *CustomDictionary.xml*. Coloque el diccionario en el directorio de instalación de la herramienta, el directorio del proyecto, o en el directorio que está asociado a la herramienta en el perfil del usuario (*%USERPROFILE%\Application datos\\...* ). Para obtener información sobre cómo agregar el diccionario personalizado a un proyecto en Visual Studio, vea [Cómo: personalizar el diccionario de análisis de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

- Agregar palabras que no deberían causar una infracción en la ruta de acceso Dictionary/Words/Recognized.

- Agregar palabras que deben causar una infracción en la ruta de acceso de diccionario/palabras/no reconocida.

- Agregar palabras que deben estar marcadas como obsoleta en la ruta de acceso Dictionary/Words/Deprecated. Vea el tema de regla relacionado [CA1726: utilizar términos preferidos](../code-quality/ca1726-use-preferred-terms.md) para obtener más información.

- Agregar excepciones a las reglas de mayúsculas y minúsculas acrónimo para la ruta de acceso de diccionario acrónimos/Acronyms/CasingExceptions.

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

Suprimir una advertencia de esta regla sólo si la palabra mal escrita intencionadamente y la palabra se aplica a un conjunto limitado de la biblioteca. Palabras escritas correctamente reducen la curva de aprendizaje necesaria para las nuevas bibliotecas de software.

## <a name="related-rules"></a>Reglas relacionadas

- [CA2204: Los literales deben estar escritos correctamente ](../code-quality/ca2204-literals-should-be-spelled-correctly.md)
- [CA1703: Las cadenas de recursos deberían tener la ortografía correcta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1709: Los identificadores deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Los identificadores se deberían diferenciar en algo más que en el uso de mayúsculas y minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
- [CA1707: Los identificadores no deberían contener subrayado](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
- [CA1726: Utilizar términos preferidos](../code-quality/ca1726-use-preferred-terms.md)

## <a name="see-also"></a>Vea también

- [Cómo: Personalizar el diccionario de análisis de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md)
