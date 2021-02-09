---
title: 'Cómo: Personalizar el diccionario de análisis de código'
ms.date: 11/04/2016
description: Obtenga información sobre el Diccionario de análisis de código que identifica los errores de la Convención de nomenclatura y la ortografía. Vea cómo crear un diccionario personalizado y aplicarlo a un proyecto.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- code analysis dictionary
- custom dictionary, code analysis
- dictionary, code analysis
ms.assetid: 667e3b4e-beff-48be-b3d1-376e1716a895
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 10466acedcd5c7f5fda835d66e654128a556d0a4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860105"
---
# <a name="how-to-customize-the-code-analysis-dictionary"></a>Cómo: Personalizar el diccionario de análisis de código

El análisis de código usa un diccionario integrado para comprobar los identificadores en el código en busca de errores de ortografía, de mayúsculas y minúsculas, y otras convenciones de nomenclatura de las instrucciones de diseño de .NET. Puede crear un archivo XML de diccionario personalizado para agregar, quitar o modificar términos, abreviaturas y acrónimos al diccionario integrado.

Por ejemplo, suponga que el código contiene una clase denominada **DoorKnokker**. El análisis de código identificaría el nombre como un compuesto de dos palabras: **puerta** y **knokker**. A continuación, se genera una advertencia que indica que **knokker** no se ha escrito correctamente. Para forzar el análisis de código para que reconozca la ortografía, puede Agregar el término **knokker** al diccionario personalizado.

## <a name="to-create-a-custom-dictionary"></a>Para crear un diccionario personalizado

Cree un archivo denominado **CustomDictionary.xml**.

Defina las palabras personalizadas mediante la siguiente estructura XML:

```xml
<Dictionary>
      <Words>
         <Unrecognized>
            <Word>knokker</Word>
         </Unrecognized>
         <Recognized>
            <Word></Word>
         </Recognized>
         <Deprecated>
            <Term PreferredAlternate=""></Term>
         </Deprecated>
         <Compound>
            <Term CompoundAlternate=""></Term>
         </Compound>
         <DiscreteExceptions>
            <Term></Term>
         </DiscreteExceptions>
      </Words>
      <Acronyms>
         <CasingExceptions>
            <Acronym></Acronym>
         </CasingExceptions>
      </Acronyms>
   </Dictionary>
```

## <a name="custom-dictionary-elements"></a>Elementos de diccionario personalizados

Puede modificar el comportamiento del Diccionario de análisis de código agregando términos como texto interno de los siguientes elementos en el diccionario personalizado:

- [Diccionario/palabras/reconocido/palabra](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsRecognizedWord)

- [Diccionario/palabras/desconocido/palabra](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsUnrecognizedWord)

- [Diccionario/palabras/en desuso/término [ @PreferredAlternate ]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDeprecatedTermPreferredAlternate)

- [Diccionario/palabras/compuesto/término [ @CompoundAlternate ]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsCompoundTermCompoundAlternate)

- [Diccionario/palabras/DiscreteExceptions/término](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDiscreteExceptionsTerm)

- [Dictionary/acrónimos/CasingExceptions/acrónimo](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryAcronymsCasingExceptionsAcronym)

### <a name="dictionarywordsrecognizedword"></a><a name="BKMK_DictionaryWordsRecognizedWord"></a> Diccionario/palabras/reconocido/palabra

Para incluir un término en la lista de términos que el análisis de código identifica como correctamente escrito, agregue el término como texto interno de un elemento Dictionary/Words/reconocid/Word. Los términos de los elementos Dictionary/Words/reconocid/Word no distinguen mayúsculas de minúsculas.

**Ejemplo**

```xml
<Dictionary>
      <Words>
         <Recognized>
            <Word>knokker</Word>
            ...
         </Recognized>
         ...
      </Words>
      ...
</Dictionary>
```

Los términos en Diccionario/palabras/nodos reconocidos se aplican a las siguientes reglas de análisis de código:

- [CA1701: En las palabras compuestas de la cadena de recursos se deben utilizar mayúsculas y minúsculas correctamente](../code-quality/ca1701.md)

- [CA1702: En las palabras compuestas se deben utilizar mayúsculas y minúsculas correctamente](../code-quality/ca1702.md)

- [CA1703: La ortografía de las cadenas de recursos debe ser correcta](../code-quality/ca1703.md)

- [CA1704: La ortografía de los identificadores debe ser correcta](../code-quality/ca1704.md)

- [CA1709: Los identificadores deben utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1709.md)

- [CA1726: Utilizar términos preferidos](../code-quality/ca1726.md)

- [CA2204: Los literales deben estar escritos correctamente](../code-quality/ca2204.md)

### <a name="dictionarywordsunrecognizedword"></a><a name="BKMK_DictionaryWordsUnrecognizedWord"></a> Diccionario/palabras/desconocido/palabra

Para excluir un término de la lista de términos que el análisis de código identifica como correctamente escrito, agregue el término que se va a excluir como texto interno de un elemento Dictionary/Words/unreconocible/Word. Los términos de los elementos Dictionary/Words/unreconocible/Word no distinguen mayúsculas de minúsculas.

**Ejemplo**

```xml
<Dictionary>
      <Words>
         <Unrecognized>
            <Word>meth</Word>
            ...
         </Unrecognized>
         ...
      </Words>
      ...
</Dictionary>
```

Los términos del nodo Diccionario/palabras/no reconocido se aplican a las siguientes reglas de análisis de código:

- [CA1701: En las palabras compuestas de la cadena de recursos se deben utilizar mayúsculas y minúsculas correctamente](../code-quality/ca1701.md)

- [CA1702: En las palabras compuestas se deben utilizar mayúsculas y minúsculas correctamente](../code-quality/ca1702.md)

- [CA1703: La ortografía de las cadenas de recursos debe ser correcta](../code-quality/ca1703.md)

- [CA1704: La ortografía de los identificadores debe ser correcta](../code-quality/ca1704.md)

- [CA1709: Los identificadores deben utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1709.md)

- [CA1726: Utilizar términos preferidos](../code-quality/ca1726.md)

- [CA2204: Los literales deben estar escritos correctamente](../code-quality/ca2204.md)

### <a name="dictionarywordsdeprecatedtermpreferredalternate"></a><a name="BKMK_DictionaryWordsDeprecatedTermPreferredAlternate"></a> Diccionario/palabras/en desuso/término [ @PreferredAlternate ]

Para incluir un término en la lista de términos que el análisis de código identifica como desusado, agregue el término como texto interno de un elemento Dictionary/Words/deprecated/term. Un término en desuso es una palabra que está escrita correctamente pero que no debe usarse.

Para incluir un término alternativo sugerido en la advertencia, especifique la alternativa en el atributo PreferredAlternate del elemento term. Puede dejar el valor de atributo vacío si no desea sugerir un alternativo.

- El término en desuso en el elemento Dictionary/Words/deprecated/term no distingue entre mayúsculas y minúsculas.

- El valor del atributo PreferredAlternate distingue mayúsculas de minúsculas. Use mayúsculas y minúsculas Pascal para alternativas compuestas.

**Ejemplo**

```xml
<Dictionary>
      <Words>
         <Deprecated>
            <Term PreferredAlternate="LogOn">login</Term>
            ...
         </Deprecated>
         ...
      </Words>
      ...
</Dictionary>
```

Los términos del nodo Diccionario/palabras/en desuso se aplican a las siguientes reglas de análisis de código:

- [CA1701: En las palabras compuestas de la cadena de recursos se deben utilizar mayúsculas y minúsculas correctamente](../code-quality/ca1701.md)

- [CA1702: En las palabras compuestas se deben utilizar mayúsculas y minúsculas correctamente](../code-quality/ca1702.md)

- [CA1703: La ortografía de las cadenas de recursos debe ser correcta](../code-quality/ca1703.md)

- [CA1704: La ortografía de los identificadores debe ser correcta](../code-quality/ca1704.md)

- [CA1726: Utilizar términos preferidos](../code-quality/ca1726.md)

### <a name="dictionarywordscompoundtermcompoundalternate"></a><a name="BKMK_DictionaryWordsCompoundTermCompoundAlternate"></a> Diccionario/palabras/compuesto/término [ @CompoundAlternate ]

El diccionario integrado identifica algunos términos como términos únicos y discretos en lugar de un término compuesto. Para incluir un término en la lista de términos que el análisis de código identifica como una palabra compuesta y para especificar la grafía correcta del término, agregue el término como texto interno de un elemento de diccionario/palabras/compuesto/término. En el atributo CompoundAlternate del elemento term, especifique las palabras individuales que componen el término compuesto capitalizando la primera letra de las palabras individuales (mayúsculas y minúsculas Pascal). Tenga en cuenta que el término especificado en el texto interno se agrega automáticamente a la lista de diccionario, palabras y DiscreteExceptions.

- El término compuesto en el elemento de diccionario/palabras/compuesto/término no distingue entre mayúsculas y minúsculas.

- El valor del atributo CompoundAlternate distingue mayúsculas de minúsculas. Use mayúsculas y minúsculas Pascal para alternativas compuestas.

**Ejemplo**

```xml
<Dictionary>
      <Words>
         <Compound>
            <Term CompoundAlternate="CheckBox">checkbox</Term>
            ...
         </Compound>
         ...
      </Words>
      ...
</Dictionary>
```

Los términos del nodo Diccionario/palabras/compuesto se aplican a las siguientes reglas de análisis de código:

- [CA1701: En las palabras compuestas de la cadena de recursos se deben utilizar mayúsculas y minúsculas correctamente](../code-quality/ca1701.md)

- [CA1702: En las palabras compuestas se deben utilizar mayúsculas y minúsculas correctamente](../code-quality/ca1702.md)

- [CA1703: La ortografía de las cadenas de recursos debe ser correcta](../code-quality/ca1703.md)

- [CA1704: La ortografía de los identificadores debe ser correcta](../code-quality/ca1704.md)

### <a name="dictionarywordsdiscreteexceptionsterm"></a><a name="BKMK_DictionaryWordsDiscreteExceptionsTerm"></a> Diccionario/palabras/DiscreteExceptions/término

Para excluir un término en la lista de términos que el análisis de código identifica como una sola palabra independiente cuando el término se comprueba con las reglas de mayúsculas y minúsculas de las palabras compuestas, agregue el término como texto interno de un elemento Dictionary/Words/DiscreteExceptions/term. El término en el elemento Dictionary/Words/DiscreteExceptions/term no distingue entre mayúsculas y minúsculas.

**Ejemplo**

```xml
<Dictionary>
      <Words>
         <DiscreteExceptions>
            <Term>checkbox</Term>
            ...
         </DiscreteExceptions>
         ...
      </Words>
      ...
</Dictionary>
```

Los términos del nodo Dictionary/Words/DiscreteExceptions se aplican a las siguientes reglas de análisis de código:

- [CA1701: En las palabras compuestas de la cadena de recursos se deben utilizar mayúsculas y minúsculas correctamente](../code-quality/ca1701.md)

- [CA1702: En las palabras compuestas se deben utilizar mayúsculas y minúsculas correctamente](../code-quality/ca1702.md)

### <a name="dictionaryacronymscasingexceptionsacronym"></a><a name="BKMK_DictionaryAcronymsCasingExceptionsAcronym"></a> Dictionary/acrónimos/CasingExceptions/acrónimo

Para incluir un acrónimo en la lista de términos que el análisis de código identifica como escrito correctamente e indicar cómo se comprueba el acrónimo en el término según las reglas de mayúsculas y minúsculas de las palabras compuestas, agregue el término como texto interno de un elemento Dictionary/acrónimos/CasingExceptions/acronym. El acrónimo del elemento Dictionary/acrónimos/CasingExceptions/acronym distingue mayúsculas de minúsculas.

**Ejemplo**

```xml
<Dictionary>
      <Acronyms>
         <CasingExceptions>
            <Acronym>NESW</Acronym>   <!-- North East South West -->
            ...
         </CasingExceptions>
         ...
      </Acronyms>
      ...
</Dictionary>
```

Los términos del nodo Dictionary/acrónimos/CasingExceptions se aplican a las siguientes reglas de análisis de código:

- [CA1709: Los identificadores deben utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1709.md)

## <a name="to-apply-a-custom-dictionary-to-a-project"></a><a name="BKMK_ToApplyACustomDictionaryToAProject"></a> Para aplicar un diccionario personalizado a un proyecto

1. En **Explorador de soluciones**, use uno de los procedimientos siguientes:

    - Para agregar un diccionario a un solo proyecto, haga clic con el botón secundario en el nombre del proyecto y, a continuación, haga clic en **Agregar elemento existente**. Especifique el archivo en el cuadro de diálogo **Agregar elemento existente** .
  
    - Para agregar un diccionario compartido entre dos o más proyectos, busque el archivo que desea compartir en el cuadro de diálogo **Agregar elemento existente** , haga clic en la flecha hacia abajo del botón **Agregar** y, a continuación, haga clic en **Agregar como vínculo**.

2. En **Explorador de soluciones**, haga clic con el botón secundario en el nombre de archivo **CustomDictionary.xml** y haga clic en **propiedades**.

3. En la lista **acción de compilación** , seleccione **CodeAnalysisDictionary**.

4. En la lista **Copiar en el directorio de salida** , seleccione **no copiar**.
