---
title: Sugerencias para la búsqueda de texto completo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- hv_search
helpviewer_keywords:
- Help Viewer 2.0, full-text search tips
- full-text search tips [Help Viewer 2.0]
ms.assetid: bcaad23d-2ca7-4bec-8b54-b884bc34e70b
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a015aeff983979bbb8f6ddedc245c74d3fb5f77b
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "54791713"
---
# <a name="full-text-search-tips"></a>Sugerencias para la búsqueda de texto completo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uno de los métodos más útiles de buscar información en la Ayuda consiste en realizar una búsqueda de texto completo. Para refinar y personalizar los resultados, debe entender cómo afecta la sintaxis a la consulta. En este tema se proporcionan sugerencias, procedimientos e información detallada de la sintaxis para ayudarle a crear mejor sus consultas.  
  
## <a name="full-text-search-tips"></a>Sugerencias para la búsqueda de texto completo  
 Podrá crear búsquedas más selectivas que devuelvan solo los temas que le interesan si entiende cómo interpreta la Ayuda el formato que usa en las consultas. Los formatos incluyen caracteres especiales, palabras reservadas y filtros.  
  
### <a name="general-guidelines"></a>Instrucciones generales  
 En la tabla siguiente se incluyen algunas reglas y directrices básicas para realizar consultas de búsqueda en la Ayuda.  
  
|Sintaxis|Descripción|  
|------------|-----------------|  
|Distinción de mayúsculas y minúsculas|Las búsquedas no distinguen entre mayúsculas y minúsculas. Desarrolle los criterios de búsqueda usando caracteres en mayúsculas o en minúsculas. Por ejemplo, "OLE" y "ole" devuelven los mismos resultados.|  
|Combinaciones de caracteres|No es posible buscar una sola letra (a-z) o un solo número (0-9). Si intenta buscar ciertas palabras reservadas, por ejemplo "y", "de" y "con", estas se omitirán. Para obtener más información, vea "Palabras omitidas en las búsquedas (palabras irrelevantes)" más adelante en este tema.|  
|Orden de evaluación|Las consultas de búsqueda se evalúan de izquierda a derecha.|  
  
### <a name="search-syntax"></a>Sintaxis de búsqueda  
 Si especifica una cadena de búsqueda que incluye varias palabras, como "palabra1 palabra2", esa cadena es equivalente a escribir "palabra1 Y palabra2", que devuelve solo los temas que contienen todas las palabras individuales en la cadena de búsqueda.  
  
> [!IMPORTANT]
> 1. No se admite la búsqueda de frases. Si se especifica más de una palabra en una cadena de búsqueda, los temas devueltos contendrán todas las palabras que ha especificado pero no necesariamente la frase exacta especificada.  
>    2.  Use los operadores lógicos para especificar la relación entre las palabras en la frase de búsqueda. Puede incluir operadores lógicos, como Y, O, NO y CERCA_DE, para restringir más la búsqueda. Por ejemplo, si busca "declarar CERCA_DE unión", los resultados de la búsqueda incluirán temas que contengan las palabras "declarar" y "unión" cerca la una de la otra. Para obtener más información, vea [Operadores lógicos en expresiones de búsqueda](../ide/logical-operators-in-search-expressions.md).  
  
### <a name="filters"></a>Filtros  
 Puede restringir aún más los resultados de la búsqueda mediante los operadores de búsqueda avanzada. La Ayuda incluye tres categorías que puede usar para filtrar los resultados de una búsqueda de texto completo: Título, Código y Palabra clave. Para obtener más información, vea [Operadores de búsqueda avanzada en expresiones de búsqueda](../ide/advanced-search-operators-in-search-expressions.md).  
  
### <a name="ranking-of-search-results"></a>Clasificación de resultados de la búsqueda  
 El algoritmo de búsqueda aplica ciertos criterios para ayudar a situar los resultados de la búsqueda más arriba o más abajo en la lista de resultados. En general:  
  
1.  El contenido que incluye palabras de búsqueda en el título tiene mejor clasificación que el que no lo hace.  
  
2.  El contenido que incluye palabras de búsqueda muy próximas tiene mejor clasificación que el que no lo hace.  
  
3.  El contenido con una mayor densidad de las palabras de búsqueda tiene mejor clasificación que el contenido con una densidad inferior.  
  
### <a name="words-ignored-in-searches-stop-words"></a>Palabras omitidas en las búsquedas (palabras irrelevantes)  
 Las palabras o números que aparecen más habitualmente, a veces llamadas palabras irrelevantes, se omiten automáticamente durante una búsqueda de texto completo. Por ejemplo, si busca la frase "pasar por", los resultados de la búsqueda mostrarán los temas que contienen la palabra "pasar", pero no "por".  
  
## <a name="see-also"></a>Vea también  
 [Encontrar información](../ide/locate-information.md)   
 [Operadores lógicos en expresiones de búsqueda](../ide/logical-operators-in-search-expressions.md)
