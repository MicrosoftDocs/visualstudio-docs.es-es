---
redirect_url: /visualstudio/ide/logical-operators-in-search-expressions
ms.openlocfilehash: fe896af873197c95a4b226396e0b6333fdc40cfa
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
título: "Operadores de búsqueda avanzada en expresiones de búsqueda | Microsoft Docs" ms.custom: "" ms.date: "02/06/2017" ms.reviewer: "" ms.suite: "" ms.technology: 
  - "vs-help-viewer" ms.tgt_pltfrm: "" ms.topic: "article" helpviewer_keywords: 
  - "Visor de Ayuda, búsqueda de palabras clave"
  - "Visor de Ayuda, búsqueda de código"
  - "Visor de Ayuda, búsqueda de código por lenguaje de programación"
  - "Visor de Ayuda, búsqueda de títulos"
  - "búsqueda de código [Visor de Ayuda]"
  - "búsqueda de títulos [Visor de Ayuda]" ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e caps.latest.revision: 9 author: "gewarren" ms.author: "gewarren" manager: ghogen
---
# <a name="advanced-search-operators-in-search-expressions"></a>Operadores de búsqueda avanzada en expresiones de búsqueda
Con los operadores de búsqueda avanzada en el Visor de Ayuda, puede restringir la búsqueda de contenido si especifica en qué parte de un tema buscar el término de búsqueda. En esta tabla se describen los cuatro operadores de búsqueda avanzada que hay disponibles.

|Para buscar|Uso|Ejemplo|Resultado|  
|-------------------|---------|-------------|------------|  
|Un término en el título del tema|title:|title:binaryreader|Temas que contienen "binaryreader" en sus títulos.|  
|Un término en un ejemplo de código|code:|code:readdouble|Temas que contienen "readdouble" en un ejemplo de código.|  
|Un término en un ejemplo de un lenguaje de programación específico|code:vb:|code:vb:string|Temas que contienen "string" en un ejemplo de código de Visual Basic.|  
|Un tema que está asociado a una palabra clave de índice específica|keyword:|keyword:readbyte|Temas que están asociados con la palabra clave de índice "readbyte".|  

> [!WARNING]
>  Debe escribir operadores de búsqueda avanzada con dos puntos finales y ningún espacio antes de los dos puntos para que el motor de búsqueda los reconozca.    

## <a name="programming-languages-for-code-examples"></a>Lenguajes de programación para ejemplos de código
Puede usar el operador code: para buscar contenido sobre cualquiera de los diversos lenguajes de programación, pero solo devuelve resultados para el contenido que se ha marcado con una etiqueta de lenguaje de programación. Para devolver los ejemplos para un lenguaje de programación específico, use uno de estos valores de lenguaje de programación:  

|Lenguaje de programación|Sintaxis del operador de búsqueda|  
|--------------------|---------|  
|Visual Basic|code:vb<br/>code:visualbasic|  
|C#|code:c#<br/>code:csharp|  
|C++|code:cpp<br/>code:c++<br/>code:cplusplus|  
|F#|code:f#<br/>code:fsharp|  
|JavaScript|code:javascript<br/>code:js|  
|XAML|code:xaml|
