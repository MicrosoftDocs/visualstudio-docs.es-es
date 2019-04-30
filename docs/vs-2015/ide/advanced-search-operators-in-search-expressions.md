---
title: Operadores de búsqueda avanzada en expresiones de búsqueda | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Help Viewer 2.0, searching for keywords
- Help Viewer 2.0, searching code
- Help Viewer 2.0, searching code by programming language
- Help Viewer 2.0, searching titles
- searching code [Help Viewer 2.0]
- searching titles [Help Viewer 2.0]
ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6befa20bcda7f30896fb2b04fadefb0eb5f21f8d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63408405"
---
# <a name="advanced-search-operators-in-search-expressions"></a>operadores de búsqueda avanzada en expresiones de búsqueda
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mediante el uso de operadores de búsqueda avanzada, puede refinar la búsqueda de contenido mediante la creación de expresiones de búsqueda más complicadas de sencillas. Como se muestra en la tabla siguiente, estos operadores restringen el contexto en el que se ejecuta una consulta.  
  
> [!WARNING]
> Debe escribir operadores de búsqueda avanzada con dos puntos finales y ningún espacio antes de los dos puntos para que el motor de búsqueda los reconozca.  
  
|Para buscar|Usar|Ejemplo|Resultado|  
|-------------------|---------|-------------|------------|  
|Un término en el título del tema|title:|title:binaryreader|Temas que contienen "binaryreader" en los títulos.|  
|Un término en un ejemplo de código|code:|code:readdouble|Temas que contienen "readdouble" en un ejemplo de código.|  
|Un término en un ejemplo de un lenguaje de programación específico|code:vb:|code:vb:string|Temas que contienen "string" en un ejemplo de Visual Basic.|  
|Un tema que está asociado a una palabra clave de índice específica|keyword:|keyword:readbyte|Temas que están asociados con la palabra clave de índice "readbyte".|  
  
 Puede usar code: operator para buscar contenido sobre cualquiera de los diversos lenguajes de programación, pero devuelve resultados solo para el contenido que se ha marcado con un lenguaje de programación específico. En la tabla siguiente se muestran los lenguajes de programación que admite este operador:  
  
|Lenguaje de programación|Usar|  
|--------------------------|---------|  
|Visual Basic|code:vb<br /><br /> o<br /><br /> code:visualbasic|  
|C#|code:c#<br /><br /> o<br /><br /> code:csharp|  
|C++|code:cpp<br /><br /> o<br /><br /> code:c++<br /><br /> o<br /><br /> code:cplusplus|  
|F#|code:f#<br /><br /> o<br /><br /> code:fsharp|  
|JavaScript|code:javascript<br /><br /> o<br /><br /> code:js|  
|XAML|code:xaml|  
  
## <a name="see-also"></a>Vea también  
 [Operadores lógicos en expresiones de búsqueda](../ide/logical-operators-in-search-expressions.md)   
 [Sugerencias para la búsqueda de texto completo](../ide/full-text-search-tips.md)
