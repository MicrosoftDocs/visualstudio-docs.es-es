---
title: "C&#243;mo: Personalizar el diccionario de an&#225;lisis de c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "diccionario de análisis de código"
  - "diccionarios personalizados, análisis de código"
  - "diccionario, análisis de código"
ms.assetid: 667e3b4e-beff-48be-b3d1-376e1716a895
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 21
---
# C&#243;mo: Personalizar el diccionario de an&#225;lisis de c&#243;digo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El análisis de código utiliza un diccionario integrado para comprobar los identificadores en el código en busca de faltas de ortografía, errores gramaticales y otras convenciones de nomenclatura de las instrucciones de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Puede crear un archivo Xml de diccionario personalizado para agregar, quitar o modificar términos, abreviaturas y acrónimos en el diccionario integrado.  
  
 Por ejemplo, supongamos que el código contiene una clase denominada **DoorKnokker**.  La herramienta de análisis de código consideraría el nombre como un término compuesto de dos palabras: **door** y **knokker**.  Entonces mostraría una advertencia para indicar que **knokker** no se ha escrito correctamente.  Para obligar al análisis de código a reconocer la ortografía, agregue el término **knokker** al diccionario personalizado.  
  
## Para crear un diccionario personalizado  
 Cree un archivo denominado **CustomDictionary.xml**.  
  
 Defina las palabras personalizadas mediante la estructura XML siguiente:  
  
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
            <Term PreferredAlternate=""></Term>  
         </Deprecated>  
         <Compound>  
            <Term CompoundAlternate=""></Term>  
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
  
## Elementos del diccionario personalizado  
 Puede modificar el comportamiento del diccionario de análisis de código agregando términos como el texto interno de los siguientes elementos del diccionario personalizado:  
  
-   [Dictionary/Words/Recognized/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsRecognizedWord)  
  
-   [Dictionary/Words/Unrecognized/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsUnrecognizedWord)  
  
-   [Dictionary/Words/Deprecated/Term[@PreferredAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDeprecatedTermPreferredAlternate)  
  
-   [Dictionary/Words/Compound/Term[@CompoundAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsCompoundTermCompoundAlternate)  
  
-   [Dictionary/Words/DiscreteExceptions/Term](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDiscreteExceptionsTerm)  
  
-   [Dictionary/Acronyms/CasingExceptions/Acronym](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryAcronymsCasingExceptionsAcronym)  
  
###  <a name="BKMK_DictionaryWordsRecognizedWord"></a> Dictionary\/Words\/Recognized\/Word  
 Para incluir un término en la lista de palabras que el análisis de código identifica como correctamente escritas, agregue el término como texto interno de un elemento Dictionary\/Words\/Recognized\/Word.  Las palabras de Dictionary\/Words\/Recognized\/Word no distinguen entre mayúsculas y minúsculas.  
  
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
  
 Las palabras de los nodos Dictionary\/Words\/Recognized se aplican a las siguientes reglas del análisis de código:  
  
-   [CA1701: En las palabras compuestas de la cadena de recursos se deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: En las palabras compuestas se deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: Las cadenas de recursos deberían tener la ortografía correcta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: Los identificadores deberían tener la ortografía correcta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1709: Los identificadores deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
-   [CA1726: Utilizar términos preferidos](../code-quality/ca1726-use-preferred-terms.md)  
  
-   [CA2204: Debe escribir correctamente los literales](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsUnrecognizedWord"></a> Dictionary\/Words\/Unrecognized\/Word  
 Para excluir un término de la lista de palabras que el análisis de código identifica como correctamente escritas, agregue el término que se va a excluir como texto interno de un elemento Dictionary\/Words\/Unrecognized\/Word.  Los términos de Dictionary\/Words\/Unrecognized\/Word no distinguen entre mayúsculas y minúsculas.  
  
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
  
 Los términos del nodo Dictionary\/Words\/Unrecognized se aplican a las siguientes reglas del análisis de código:  
  
-   [CA1701: En las palabras compuestas de la cadena de recursos se deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: En las palabras compuestas se deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: Las cadenas de recursos deberían tener la ortografía correcta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: Los identificadores deberían tener la ortografía correcta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1709: Los identificadores deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
-   [CA1726: Utilizar términos preferidos](../code-quality/ca1726-use-preferred-terms.md)  
  
-   [CA2204: Debe escribir correctamente los literales](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsDeprecatedTermPreferredAlternate"></a> Dictionary\/Words\/Deprecated\/Term\[@PreferredAlternate\]  
 Para incluir un término en la lista de palabras que el análisis de código identifica como en desuso, agregue el término como texto interno de un elemento Dictionary\/Words\/Deprecated\/Term.  Un término desusado es una palabra que está bien escrita pero no se debe utilizar.  
  
 Para incluir un término alternativo sugerido en la advertencia, especifíquelo en el atributo PreferredAlternate del elemento Term.  Puede dejar el valor de atributo vacío si no desea sugerir ninguno.  
  
-   El término desusado del elemento Dictionary\/Words\/Deprecated\/Term no distingue entre mayúsculas y minúsculas.  
  
-   El valor de atributo PreferredAlternate distingue entre mayúsculas y minúsculas.  Utilice la grafía Pascal para las alternativas compuestas.  
  
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
  
 Los términos del nodo Dictionary\/Words\/Deprecated se aplican a las siguientes reglas del análisis de código:  
  
-   [CA1701: En las palabras compuestas de la cadena de recursos se deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: En las palabras compuestas se deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: Las cadenas de recursos deberían tener la ortografía correcta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: Los identificadores deberían tener la ortografía correcta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1726: Utilizar términos preferidos](../code-quality/ca1726-use-preferred-terms.md)  
  
###  <a name="BKMK_DictionaryWordsCompoundTermCompoundAlternate"></a> Dictionary\/Words\/Compound\/Term\[@CompoundAlternate\]  
 El diccionario integrado identifica algunos términos como elementos únicos discretos, en lugar de como un término compuesto.  Para incluir un término en la lista de palabras que el análisis de código identifica como palabra compuesta y para especificar la grafía correcta del mismo, agréguelo como texto interno de un elemento Dictionary\/Words\/Compound\/Term.  En el atributo CompoundAlternate del elemento Term, especifique las palabras individuales que constituyen el término compuesto poniendo en mayúsculas la primera letra de cada palabra \(grafía Pascal\).  Observe que el término especificado en el texto interno se agrega automáticamente a la lista Dictionary\/Words\/DiscreteExceptions.  
  
-   El término desusado del elemento Dictionary\/Words\/Deprecated\/Term no distingue entre mayúsculas y minúsculas.  
  
-   El valor de atributo PreferredAlternate distingue entre mayúsculas y minúsculas.  Utilice la grafía Pascal para las alternativas compuestas.  
  
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
  
 Los términos del nodo Dictionary\/Words\/Compound se aplican a las siguientes reglas del análisis de código:  
  
-   [CA1701: En las palabras compuestas de la cadena de recursos se deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: En las palabras compuestas se deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: Las cadenas de recursos deberían tener la ortografía correcta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: Los identificadores deberían tener la ortografía correcta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsDiscreteExceptionsTerm"></a> Dictionary\/Words\/DiscreteExceptions\/Term  
 Para excluir un término en la lista de términos que el análisis de código identifica como una palabra única discreta cuando las reglas de grafía comprueban si es una palabra compuesta, agréguelo como texto interno de un elemento Dictionary\/Words\/DiscreteExceptions\/Term.  El término del elemento Dictionary\/Words\/DiscreteExceptions\/Term no distingue entre mayúsculas y minúsculas.  
  
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
  
 Los términos del nodo Dictionary\/Words\/DiscreteExceptions se aplican a las siguientes reglas del análisis de código:  
  
-   [CA1701: En las palabras compuestas de la cadena de recursos se deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: En las palabras compuestas se deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
###  <a name="BKMK_DictionaryAcronymsCasingExceptionsAcronym"></a> Dictionary\/Acronyms\/CasingExceptions\/Acronym  
 Para incluir un acrónimo en la lista de términos que el análisis de código identifica como correctamente escritos y para indicar cómo las reglas de grafía comprueban si es una palabra compuesta, agréguelo como texto interno de un elemento Dictionary\/Acronyms\/CasingExceptions\/Acronym.  El acrónimo del elemento Dictionary\/Acronyms\/CasingExceptions\/Acronym distingue entre mayúsculas y minúsculas.  
  
 **Ejemplo**  
  
```  
<Dictionary>  
      <Acronyms>  
         <CasingExceptions>  
            <Acronym>NESW</Acronym>   <!-- North East South West -->  
            ...  
         </CasingExceptions>  
         ...  
      </Acronyms>  
      ...  
</Dictionary>  
  
```  
  
 Los términos del nodo Dictionary\/Acronyms\/CasingExceptions se aplican a las siguientes reglas del análisis de código:  
  
-   [CA1709: Los identificadores deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
##  <a name="BKMK_ToApplyACustomDictionaryToAProject"></a> Para aplicar un diccionario personalizado a un proyecto  
  
1.  En el **Explorador de soluciones**, utilice uno de los siguientes procedimientos:  
  
2.  Para agregar un diccionario a un proyecto único, haga clic con el botón secundario en el nombre del proyecto y, a continuación, haga clic en **Agregar elemento existente**.  En el cuadro de diálogo **Agregar elemento existente**, especifique el archivo.  
  
3.  Para agregar un diccionario compartido entre dos o más proyectos, busque el archivo para compartir en el cuadro de diálogo **Agregar elemento existente**, haga clic en la flecha abajo del botón **Agregar** y, a continuación, haga clic en **Agregar como vínculo**.  
  
4.  En el **Explorador de soluciones**, haga clic con el botón secundario en el nombre de archivo **CustomDictionary.xml** y, a continuación, haga clic en **Propiedades**.  
  
5.  En la lista **Acción de compilación**, seleccione **CodeAnalysisDictionary**.  
  
6.  En la lista **Copiar en el directorio de salida**, seleccione **No copiar**.