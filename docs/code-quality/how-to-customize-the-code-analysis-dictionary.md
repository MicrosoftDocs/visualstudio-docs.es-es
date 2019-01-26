---
title: Procedimiento Personalizar el diccionario de análisis de código
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- code analysis dictionary
- custom dictionary, code analysis
- dictionary, code analysis
ms.assetid: 667e3b4e-beff-48be-b3d1-376e1716a895
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 19ad0da444f99e0fbf618d97729c64a1e5ed5666
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54971824"
---
# <a name="how-to-customize-the-code-analysis-dictionary"></a>Procedimiento Personalizar el diccionario de análisis de código
Análisis de código usa un diccionario integrado para comprobar los identificadores en el código para los errores de ortografía, caso gramatical y otras convenciones de nomenclatura de las directrices de .NET Framework. Puede crear un archivo Xml de diccionario personalizado para agregar, quitar o modificar los términos, abreviaturas y acrónimos al diccionario integrado.

 Por ejemplo, suponga que el código contiene una clase denominada **DoorKnokker**. Análisis de código podría identificar el nombre como un compuesto de dos palabras: **puerta** y **knokker**. A continuación, generaría una advertencia que **knokker** no se ha escrito correctamente. Para forzar a reconocer la ortografía de análisis de código, puede agregar el término **knokker** al diccionario personalizado.

## <a name="to-create-a-custom-dictionary"></a>Para crear un diccionario personalizado
 Cree un archivo denominado **CustomDictionary.xml**.

 Defina las palabras personalizadas mediante el uso de la estructura XML siguiente:

```
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

## <a name="custom-dictionary-elements"></a>Elementos del diccionario personalizado
 Puede modificar el comportamiento del diccionario de análisis de código mediante la adición de términos como texto interno de los siguientes elementos en el diccionario personalizado:

- [Dictionary/Words/Recognized/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsRecognizedWord)

- [Dictionary/Words/Unrecognized/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsUnrecognizedWord)

- [Diccionario/palabras/en desuso o término [@PreferredAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDeprecatedTermPreferredAlternate)

- [Diccionario, palabras, compuesta/Term [@CompoundAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsCompoundTermCompoundAlternate)

- [Dictionary/Words/DiscreteExceptions/Term](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDiscreteExceptionsTerm)

- [Dictionary/Acronyms/CasingExceptions/Acronym](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryAcronymsCasingExceptionsAcronym)

###  <a name="BKMK_DictionaryWordsRecognizedWord"></a> Dictionary/Words/Recognized/Word
 Para incluir un término en la lista de términos que identifica el análisis de código escrito correctamente, agregue el término como el texto interno de un elemento de la palabra/diccionario/palabras/reconoce. Términos de los elementos de la palabra/diccionario/palabras/reconoce no distinguen mayúsculas de minúsculas.

 **Ejemplo**

```
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

 Se aplican las condiciones en los nodos de palabras/diccionario/reconoce las siguientes reglas de análisis de código:

-   [CA1701: Palabras compuestas de la cadena de recursos deberían escribirse correctamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

-   [CA1702: En las palabras compuestas se deberían escribirse correctamente](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

-   [CA1703: Cadenas de recursos deberían tener la ortografía correcta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

-   [CA1704: Los identificadores deberían tener la ortografía correcta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

-   [CA1709: Los identificadores deberían escribirse correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

-   [CA1726: Utilizar términos preferidos](../code-quality/ca1726-use-preferred-terms.md)

-   [CA2204: Deben escribir correctamente los literales](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

###  <a name="BKMK_DictionaryWordsUnrecognizedWord"></a> / Palabras/no reconocida/palabra del diccionario
 Para excluir un término de la lista de términos que identifica el análisis de código escrito correctamente, agregue el término para excluirlos como el texto interno de un elemento de la palabra/diccionario/palabras o no reconocida. Términos de elementos o las palabras/no reconocida/palabra del diccionario no distinguen mayúsculas de minúsculas.

 **Ejemplo**

```
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

 Los términos en el nodo de diccionario o palabras/no reconocida se aplican a las reglas de análisis de código siguiente:

-   [CA1701: Palabras compuestas de la cadena de recursos deberían escribirse correctamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

-   [CA1702: En las palabras compuestas se deberían escribirse correctamente](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

-   [CA1703: Cadenas de recursos deberían tener la ortografía correcta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

-   [CA1704: Los identificadores deberían tener la ortografía correcta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

-   [CA1709: Los identificadores deberían escribirse correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

-   [CA1726: Utilizar términos preferidos](../code-quality/ca1726-use-preferred-terms.md)

-   [CA2204: Deben escribir correctamente los literales](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

###  <a name="BKMK_DictionaryWordsDeprecatedTermPreferredAlternate"></a> Diccionario/palabras/en desuso o término [@PreferredAlternate]
 Para incluir un término en la lista de términos que análisis de código que se identifica como en desuso, agregar el término como texto interno de un elemento de término/diccionario/palabras/en desuso. Un término obsoleto es una palabra que se ha escrito correctamente, pero no se debe usar.

 Para incluir un término alternativo sugerido de la advertencia, especifique al texto alternativo en el atributo PreferredAlternate del elemento término. Puede dejar el valor de atributo vacío si no desea sugerir a una alternativa.

- El término en desuso en palabras del diccionario/elemento en desuso o término no distingue mayúsculas de minúsculas.

- El valor del atributo PreferredAlternate distingue mayúsculas de minúsculas. Utilice mayúsculas y minúsculas Pascal para suplentes compuestas.

  **Ejemplo**

```
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

 Los términos en el nodo de diccionario o palabras/en desuso se aplican a las reglas de análisis de código siguiente:

-   [CA1701: Palabras compuestas de la cadena de recursos deberían escribirse correctamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

-   [CA1702: En las palabras compuestas se deberían escribirse correctamente](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

-   [CA1703: Cadenas de recursos deberían tener la ortografía correcta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

-   [CA1704: Los identificadores deberían tener la ortografía correcta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

-   [CA1726: Utilizar términos preferidos](../code-quality/ca1726-use-preferred-terms.md)

###  <a name="BKMK_DictionaryWordsCompoundTermCompoundAlternate"></a> Diccionario, palabras, compuesta/Term [@CompoundAlternate]
 El diccionario integrado identifica algunos de los términos como términos discretos, únicos en lugar de un término compuesto. Para incluir un término en la lista de términos que análisis de código se identifica como una palabra compuesta y para especificar la grafía correcta del término, agregar el término como texto interno de un elemento de diccionario, palabras, compuesta/Term. En el atributo CompoundAlternate del elemento término, especifique las palabras individuales que componen el término compuesto por poner en mayúsculas la primera letra de las palabras individuales (mayúsculas y minúsculas Pascal). Tenga en cuenta que el término especificado en el texto interno se agrega automáticamente a la lista de palabras/diccionario/DiscreteExceptions.

- El término en desuso en palabras del diccionario/elemento en desuso o término no distingue mayúsculas de minúsculas.

- El valor del atributo PreferredAlternate distingue mayúsculas de minúsculas. Utilice mayúsculas y minúsculas Pascal para suplentes compuestas.

  **Ejemplo**

```
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

 Los términos en el nodo de diccionario o palabras/compuestos se aplican a las reglas de análisis de código siguiente:

-   [CA1701: Palabras compuestas de la cadena de recursos deberían escribirse correctamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

-   [CA1702: En las palabras compuestas se deberían escribirse correctamente](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

-   [CA1703: Cadenas de recursos deberían tener la ortografía correcta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

-   [CA1704: Los identificadores deberían tener la ortografía correcta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

###  <a name="BKMK_DictionaryWordsDiscreteExceptionsTerm"></a> Dictionary/Words/DiscreteExceptions/Term
 Para excluir un término en la lista de términos que análisis de código se identifica como una sola, discreto word cuando se activa el término por las reglas de mayúsculas y minúsculas de las palabras compuestas, agregar el término como texto interno de un elemento de diccionario, palabras, DiscreteExceptions/Term. El término en el elemento del diccionario, palabras, DiscreteExceptions/Term no distingue mayúsculas de minúsculas.

 **Ejemplo**

```
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

 Los términos en el nodo de palabras/diccionario/DiscreteExceptions se aplican a las reglas de análisis de código siguiente:

-   [CA1701: Palabras compuestas de la cadena de recursos deberían escribirse correctamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

-   [CA1702: En las palabras compuestas se deberían escribirse correctamente](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

###  <a name="BKMK_DictionaryAcronymsCasingExceptionsAcronym"></a> Dictionary/Acronyms/CasingExceptions/Acronym
 Para incluir un acrónimo en la lista de términos que identifica el análisis de código como está escrita correctamente y para indicar cómo las reglas de la sigla cuando se activa el término por el uso de mayúsculas y minúsculas de las palabras compuestas, agregar el término como el texto interno de un diccionario, acrónimos/CasingExceptions / Elemento Acronym. El acrónimo en el elemento Acronym/diccionario/acrónimos/CasingExceptions distingue mayúsculas de minúsculas.

 **Ejemplo**

```
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

 Los términos en el nodo de diccionario acrónimos/Acronyms/CasingExceptions se aplican a las reglas de análisis de código siguiente:

-   [CA1709: Los identificadores deberían escribirse correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

##  <a name="BKMK_ToApplyACustomDictionaryToAProject"></a> Para aplicar un diccionario personalizado a un proyecto

1.  En **el Explorador de soluciones**, utilice uno de los siguientes procedimientos:

2.  Para agregar un diccionario a un solo proyecto, haga clic en el nombre del proyecto y, a continuación, haga clic en **Agregar elemento existente**. Especifique el archivo en el **Agregar elemento existente** cuadro de diálogo.

3.  Para agregar un diccionario que se comparte entre dos o más proyectos, busque el archivo para compartirlo en el **Agregar elemento existente** diálogo cuadro, haga clic en la flecha hacia abajo en la **agregar** botón y, a continuación, haga clic en **agregar como vínculo** .

4.  En **el Explorador de soluciones**, haga clic en el **CustomDictionary.xml** nombre de archivo y haga clic en **propiedades**.

5.  Desde el **acción de compilación** lista, seleccione **CodeAnalysisDictionary**.

6.  Desde el **Copy to Output Directory** lista, seleccione **no copie**.