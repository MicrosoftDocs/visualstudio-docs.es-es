---
title: "Cómo: personalizar el diccionario de análisis de código | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code analysis dictionary
- custom dictionary, code analysis
- dictionary, code analysis
ms.assetid: 667e3b4e-beff-48be-b3d1-376e1716a895
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7fa5f88a3578998fca325500a3815b909b6ce4a9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-customize-the-code-analysis-dictionary"></a>Cómo: Personalizar el diccionario de análisis de código
Análisis de código usa un diccionario integrado para comprobar los identificadores en el código para los errores de ortografía, mayúsculas gramaticales y otras convenciones de nomenclatura de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] directrices. Puede crear un archivo de diccionario personalizado Xml para agregar, quitar o modificar los términos y abreviaturas, acrónimos al diccionario integrado.  
  
 Por ejemplo, suponga que el código contiene una clase denominada **DoorKnokker**. Análisis de código identificaría el nombre como un compuesto de dos palabras: **puerta** y **knokker**. A continuación, generaría una advertencia que **knokker** no se ha escrito correctamente. Para forzar que el análisis de código para que reconozca la ortografía, puede agregar el término **knokker** al diccionario personalizado.  
  
## <a name="to-create-a-custom-dictionary"></a>Para crear un diccionario personalizado  
 Crear un archivo que se denomina **CustomDictionary.xml**.  
  
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
  
## <a name="custom-dictionary-elements"></a>Elementos de diccionario personalizado  
 También puede modificar el comportamiento del diccionario de análisis de código mediante la adición de términos como el texto interno de los siguientes elementos en el diccionario personalizado:  
  
-   [/ Palabras/reconoce/palabra del diccionario](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsRecognizedWord)  
  
-   [/ Palabras/reconocido/palabra del diccionario](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsUnrecognizedWord)  
  
-   [Diccionario/palabras/en desuso/Term [@PreferredAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDeprecatedTermPreferredAlternate)  
  
-   [Diccionario/palabras/compuesta/Term [@CompoundAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsCompoundTermCompoundAlternate)  
  
-   [Diccionario/palabras/DiscreteExceptions/Term](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDiscreteExceptionsTerm)  
  
-   [Diccionario/acrónimos/CasingExceptions/acrónimo](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryAcronymsCasingExceptionsAcronym)  
  
###  <a name="BKMK_DictionaryWordsRecognizedWord"></a>/ Palabras/reconoce/palabra del diccionario  
 Para incluir un término en la lista de términos que identifica el análisis de código como la revisión ortográfica, agregue el término como el texto interno de un elemento/palabras/reconoce/palabra del diccionario. Términos de elementos/palabras/reconoce/palabra del diccionario no distinguen mayúsculas de minúsculas.  
  
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
  
 Términos de diccionario/Words/Recognized nodos se aplican a las reglas de análisis de código siguiente:  
  
-   [CA1701: En las palabras compuestas de la cadena de recursos se deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: En las palabras compuestas se deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: Las cadenas de recursos deberían tener la ortografía correcta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: Los identificadores deberían tener la ortografía correcta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1709: Los identificadores deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
-   [CA1726: Utilizar términos preferidos](../code-quality/ca1726-use-preferred-terms.md)  
  
-   [CA2204: Los literales deben estar escritos correctamente ](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsUnrecognizedWord"></a>/ Palabras/reconocido/palabra del diccionario  
 Para excluir un término de la lista de términos que identifica el análisis de código como la revisión ortográfica, agregue el término que excluya como el texto interno de un elemento/palabras/no reconocida/palabra del diccionario. Términos de elementos/palabras/no reconocida/palabra del diccionario no distinguen mayúsculas de minúsculas.  
  
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
  
 Se aplican las condiciones en el nodo de diccionario/palabras/no reconocida para las reglas de análisis de código siguiente:  
  
-   [CA1701: En las palabras compuestas de la cadena de recursos se deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: En las palabras compuestas se deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: Las cadenas de recursos deberían tener la ortografía correcta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: Los identificadores deberían tener la ortografía correcta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1709: Los identificadores deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
-   [CA1726: Utilizar términos preferidos](../code-quality/ca1726-use-preferred-terms.md)  
  
-   [CA2204: Los literales deben estar escritos correctamente ](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsDeprecatedTermPreferredAlternate"></a>Diccionario/palabras/en desuso/Term [@PreferredAlternate]  
 Para incluir un término en la lista de términos que identifica de análisis de código como obsoleto, agregue el término como el texto interno de un elemento de diccionario, palabras, ya no se utiliza/Term. Un término en desuso es una palabra que se ha escrito correctamente, pero no debe usarse.  
  
 Para incluir un término alternativo sugerido de la advertencia, especifique a alternativo en el atributo PreferredAlternate del elemento término. Puede dejar el valor de atributo vacío si no desea sugerir a una alternativa.  
  
-   El término en desuso en palabras del diccionario / / elemento en desuso/término no distingue mayúsculas de minúsculas.  
  
-   El valor del atributo PreferredAlternate distingue mayúsculas de minúsculas. Utilice mayúsculas y minúsculas Pascal para compuesta alternativas.  
  
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
  
 Términos en el nodo de diccionario/Words/Deprecated se aplican a las reglas de análisis de código siguiente:  
  
-   [CA1701: En las palabras compuestas de la cadena de recursos se deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: En las palabras compuestas se deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: Las cadenas de recursos deberían tener la ortografía correcta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: Los identificadores deberían tener la ortografía correcta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1726: Utilizar términos preferidos](../code-quality/ca1726-use-preferred-terms.md)  
  
###  <a name="BKMK_DictionaryWordsCompoundTermCompoundAlternate"></a>Diccionario/palabras/compuesta/Term [@CompoundAlternate]  
 El diccionario integrado identifica algunos de los términos como términos discretos, únicos en lugar de un término compuesto. Para incluir un término en la lista de términos que identifica el análisis de código como una palabra compuesta y para especificar la grafía correcta del término, agregue el término como el texto interno de un elemento de diccionario, palabras, compuesta/Term. En el atributo CompoundAlternate del elemento término, especifique las palabras individuales que componen el término compuesto por poner en mayúsculas la primera letra de las palabras individuales (mayúsculas y minúsculas Pascal). Tenga en cuenta que el término especificado en el texto interno se agrega automáticamente a la lista de palabras de diccionario/DiscreteExceptions.  
  
-   El término en desuso en palabras del diccionario / / elemento en desuso/término no distingue mayúsculas de minúsculas.  
  
-   El valor del atributo PreferredAlternate distingue mayúsculas de minúsculas. Utilice mayúsculas y minúsculas Pascal para compuesta alternativas.  
  
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
  
 Términos en el nodo de diccionario, palabras/compuesta se aplican a las reglas de análisis de código siguiente:  
  
-   [CA1701: En las palabras compuestas de la cadena de recursos se deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: En las palabras compuestas se deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: Las cadenas de recursos deberían tener la ortografía correcta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: Los identificadores deberían tener la ortografía correcta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsDiscreteExceptionsTerm"></a>Diccionario/palabras/DiscreteExceptions/Term  
 Para excluir un término en la lista de términos que identifica el análisis de código como una sola, discreta word cuando se activa el término por las reglas de mayúsculas y minúsculas de las palabras compuestas, agregue el término como el texto interno de un elemento de diccionario/palabras/DiscreteExceptions/Term. El término en el elemento de diccionario/palabras/DiscreteExceptions/término no distingue mayúsculas de minúsculas.  
  
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
  
 Se aplican las condiciones en el nodo de diccionario, palabras/DiscreteExceptions a las reglas de análisis de código siguiente:  
  
-   [CA1701: En las palabras compuestas de la cadena de recursos se deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: En las palabras compuestas se deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
###  <a name="BKMK_DictionaryAcronymsCasingExceptionsAcronym"></a>Diccionario/acrónimos/CasingExceptions/acrónimo  
 Para incluir un acrónimo en la lista de términos que identifica el análisis de código que está escrita correctamente e indicar cómo las reglas el acrónimo cuando se activa el término por las mayúsculas y minúsculas para palabras compuestas, agregue el término como el texto interno de un diccionario, acrónimos/CasingExceptions / Elemento Acronym. El acrónimo en el elemento de diccionario/acrónimos/CasingExceptions/acrónimo distingue mayúsculas de minúsculas.  
  
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
  
 Se aplican las condiciones en el nodo de diccionario acrónimos/Acronyms/CasingExceptions a las reglas de análisis de código siguiente:  
  
-   [CA1709: Los identificadores deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
##  <a name="BKMK_ToApplyACustomDictionaryToAProject"></a>Para aplicar un diccionario personalizado a un proyecto  
  
1.  En **el Explorador de soluciones**, utilice uno de los siguientes procedimientos:  
  
2.  Para agregar un diccionario a un proyecto único, haga clic en el nombre del proyecto y, a continuación, haga clic en **Agregar elemento existente**. Especifique el archivo en el **Agregar elemento existente** cuadro de diálogo.  
  
3.  Para agregar un diccionario que se comparte entre dos o más proyectos, busque el archivo para compartirlo en el **Agregar elemento existente** diálogo cuadro, haga clic en la flecha hacia abajo en la **agregar** botón y, a continuación, haga clic en **agregar como vínculo** .  
  
4.  En **el Explorador de soluciones**, haga clic en el **CustomDictionary.xml** nombre de archivo y haga clic en **propiedades**.  
  
5.  Desde el **acción de compilación** lista, seleccione **CodeAnalysisDictionary**.  
  
6.  Desde el **copiar en el directorio de salida** lista, seleccione **no copie**.