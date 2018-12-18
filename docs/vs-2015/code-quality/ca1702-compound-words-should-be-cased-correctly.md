---
title: 'CA1702: en las palabras compuestas se deberían utilizan las mayúsculas y minúsculas correctamente | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
ms.openlocfilehash: cfc723e94b8be2f427be7b42d676218b0d9aa68d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49201144"
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702: En las palabras compuestas se deberían utilizar las mayúsculas y minúsculas correctamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obtener la documentación más reciente de Visual Studio 2017, consulte [CA1702: en las palabras compuestas se deberían escribirse correctamente](https://docs.microsoft.com/visualstudio/code-quality/ca1702-compound-words-should-be-cased-correctly) en docs.microsoft.com.  
  
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
 [CA1701: En las palabras compuestas de la cadena de recursos se deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
 [CA1709: Los identificadores deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Los identificadores se deberían diferenciar en algo más que en el uso de mayúsculas y minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
## <a name="see-also"></a>Vea también  
 [Directrices de nomenclatura](http://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3)   
 [Convenciones sobre el uso de minúsculas y mayúsculas](http://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d)

