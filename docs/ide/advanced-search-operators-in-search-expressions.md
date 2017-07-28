---
title: "Operadores de búsqueda avanzada en expresiones de búsqueda | Microsoft Docs"
ms.custom: 
ms.date: 06/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Help Viewer 2.0, searching for keywords
- Help Viewer 2.0, searching code
- Help Viewer 2.0, searching code by programming language
- Help Viewer 2.0, searching titles
- searching code [Help Viewer 2.0]
- searching titles [Help Viewer 2.0]
ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e
caps.latest.revision: 9
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 07ff2413503209d6ade252ac89dbfbe2589e7e85
ms.openlocfilehash: 7ad9c78134c337445a3e9180ad27234b7bcb07cc
ms.contentlocale: es-es
ms.lasthandoff: 06/02/2017

---
# <a name="advanced-search-operators-in-search-expressions"></a>operadores de búsqueda avanzada en expresiones de búsqueda
Con los operadores de búsqueda avanzada en el Visor de Ayuda puede restringir la búsqueda de contenido mediante la creación de expresiones de búsqueda más complejas a partir de expresiones más sencillas. Como se muestra en la tabla siguiente, estos operadores restringen el contexto en el que se ejecuta una consulta.  

> [!WARNING]
>  Debe escribir operadores de búsqueda avanzada con dos puntos finales y ningún espacio antes de los dos puntos para que el motor de búsqueda los reconozca.  

|Para buscar|Uso|Ejemplo|Resultado|  
|-------------------|---------|-------------|------------|  
|Un término en el título del tema|title:|title:binaryreader|Temas que contienen "binaryreader" en sus títulos.|  
|Un término en un ejemplo de código|code:|code:readdouble|Temas que contienen "readdouble" en un ejemplo de código.|  
|Un término en un ejemplo de un lenguaje de programación específico|code:vb:|code:vb:string|Temas que contienen "string" en un ejemplo de Visual Basic.|  
|Un tema que está asociado a una palabra clave de índice específica|keyword:|keyword:readbyte|Temas que están asociados con la palabra clave de índice "readbyte".|  

 Puede usar code: operator para buscar contenido sobre cualquiera de los diversos lenguajes de programación, pero devuelve resultados solo para el contenido que se ha marcado con un lenguaje de programación específico. En la tabla siguiente se muestran los lenguajes de programación que admite este operador:  

|Lenguaje de programación|Uso|  
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

