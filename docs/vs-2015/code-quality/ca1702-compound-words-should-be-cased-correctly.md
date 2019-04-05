---
title: 'CA1702: Las palabras compuestas se deberían escribirse correctamente | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9f4844431215d952f03ab9acc3f11ab57644abde
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2019
ms.locfileid: "59003084"
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702: En las palabras compuestas se deben utilizar mayúsculas y minúsculas correctamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obtener la documentación más reciente de Visual Studio, consulte [CA1702: Las palabras compuestas se deberían escribirse correctamente](https://docs.microsoft.com/visualstudio/code-quality/ca1702-compound-words-should-be-cased-correctly) en docs.microsoft.com.  
  
|||  
|-|-|  
|TypeName|CompoundWordsShouldBeCasedCorrectly|  
|Identificador de comprobación|CA1702|  
|Categoría|Microsoft.Naming|  
|Cambio problemático|Importante cuando se desencadena en ensamblados.<br /><br /> Indivisible: cuando se desencadena en parámetros de tipo.|  
  
## <a name="cause"></a>Motivo  
 El nombre de un identificador contiene varias palabras y al menos una de las palabras parece ser una palabra compuesta que no es mayúsculas y minúsculas correctamente.  
  
## <a name="rule-description"></a>Descripción de la regla  
 El nombre del identificador se divide en palabras que se basan en las mayúsculas y minúsculas. La biblioteca de correctores ortográficos de Microsoft comprueba cada combinación de dos palabras contigua. Si lo reconoce, el identificador genera una infracción de la regla. Ejemplos de palabras compuestas que originan una infracción son "CheckSum" y "MultiPart", que debería escribirse como "Checksum" y "Multipart", respectivamente. Debido al uso común anterior, se generan varias excepciones a la regla, y se marcan algunas palabras únicas, como "Toolbar" y "Filename", que deberían escribirse como dos palabras distintas (en este caso, "ToolBar" y "FileName").  
  
 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Cambie el nombre por lo que es con grafía correctamente.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla si el diccionario ortográfico reconoce ambas partes de la palabra compuesta y se pretende utilizar dos palabras.  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1701: Palabras compuestas de la cadena de recursos deberían escribirse correctamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
 [CA1709: Los identificadores deberían escribirse correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Los identificadores deben diferenciarse por algo más que el caso](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
## <a name="see-also"></a>Vea también  
 [Directrices de nomenclatura](http://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3)   
 [Convenciones sobre el uso de minúsculas y mayúsculas](http://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d)
