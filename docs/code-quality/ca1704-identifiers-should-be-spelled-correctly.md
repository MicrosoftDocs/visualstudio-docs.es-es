---
title: "CA1704: Los identificadores deber&#237;an tener la ortograf&#237;a correcta | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1704"
  - "IdentifiersShouldBeSpelledCorrectly"
helpviewer_keywords: 
  - "CA1704"
  - "IdentifiersShouldBeSpelledCorrectly"
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
caps.latest.revision: 25
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 25
---
# CA1704: Los identificadores deber&#237;an tener la ortograf&#237;a correcta
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldBeSpelledCorrectly|  
|Identificador de comprobación|CA1704|  
|Categoría|Microsoft.Naming|  
|Cambio problemático|Problemático|  
  
## Motivo  
 El nombre de un identificador contiene una o varias palabras que la biblioteca de correctores ortográficos de Microsoft no reconoce.  Esta regla no comprueba los constructores ni los miembros con nombres especiales como los descriptores de acceso de propiedad get y set.  
  
## Descripción de la regla  
 Esta regla analiza el identificador en tokens y comprueba la ortografía de cada uno.  El algoritmo de análisis realiza las transformaciones siguientes:  
  
-   Las letras mayúsculas inician un nuevo token.  Por ejemplo, MiNombreEsJuan se convierte en los tokens "Mi", "Nombre", "Es", "Juan".  
  
-   Si hay varias letras mayúsculas, la última inicia un nuevo token.  Por ejemplo, GUIEditor se convierte en los tokens "GUI" y "Editor".  
  
-   Se quitan los apóstrofos iniciales y finales.  Por ejemplo, 'remitente' se convierte en el token "remitente".  
  
-   Los caracteres de subrayado indican el final de un token y se quitan.  Por ejemplo, Hola\_a\_todos se convierte en los tokens "Hola" "a" "todos".  
  
-   Los símbolos incrustados de Y comercial se quitan.  Por ejemplo, el formato&tokenizes “para dar formato”.  
  
 De forma predeterminada, se utiliza la versión inglesa \(en\) del corrector ortográfico.  No hay otros diccionarios de idiomas disponibles actualmente.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, escriba la palabra correctamente o agréguela a un diccionario personalizado denominado CustomDictionary.xml.  Coloque el diccionario en el directorio de instalación de la herramienta, en el directorio del proyecto o en el directorio asociado a la herramienta bajo el perfil del usuario \(%PERFILDEUSUARIO%\\Datos de programa\\...\).  Para obtener información sobre cómo agregar el diccionario personalizado a un proyecto en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vea [Cómo: Personalizar el diccionario de análisis de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
  
-   Agregue las palabras que no deben causar una infracción a la ruta de acceso Dictionary\/Words\/Recognized.  
  
-   Agregue las palabras que deben causar una infracción a la ruta de acceso Dictionary\/Words\/Unrecognized.  
  
-   Agregue las palabras que deben marcarse como obsoletas a la ruta de acceso Dictionary\/Words\/Deprecated.  Vea el tema de la regla relacionado [CA1726: Utilizar términos preferidos](../code-quality/ca1726-use-preferred-terms.md) para obtener más información.  
  
-   Agregue las excepciones a las reglas de grafía de los acrónimos a la ruta de acceso Dictionary\/Acronyms\/CasingExceptions.  
  
 A continuación, se muestra un ejemplo de la estructura de un archivo de diccionario personalizado.  
  
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
  
## Cuándo suprimir advertencias  
 Suprima una advertencia de esta regla sólo si la palabra está escrita incorrectamente de manera intencionada y se aplica a un conjunto limitado de la biblioteca.  Las palabras escritas correctamente reducen la curva de aprendizaje necesaria para las nuevas bibliotecas de software.  
  
## Reglas relacionadas  
 [CA2204: Debe escribir correctamente los literales](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
 [CA1703: Las cadenas de recursos deberían tener la ortografía correcta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
 [CA1709: Los identificadores deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Los identificadores se deberían diferenciar en algo más que en el uso de mayúsculas y minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707: Los identificadores no deberían contener subrayado](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)  
  
 [CA1726: Utilizar términos preferidos](../code-quality/ca1726-use-preferred-terms.md)  
  
## Vea también  
 [Cómo: Personalizar el diccionario de análisis de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md)