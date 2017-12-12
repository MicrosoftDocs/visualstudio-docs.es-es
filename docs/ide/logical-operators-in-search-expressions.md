---
title: "Operadores lógicos y avanzados en expresiones de búsqueda | Microsoft Docs"
ms.custom: 
ms.date: 11/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-help-viewer
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Help Viewer, logical operators in search
- logical operators in search [Help Viewer]
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3378a554a9e576bde011a70916c48597218bb512
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="logical-and-advanced-operators-in-search-expressions"></a>Operadores lógicos y avanzados en expresiones de búsqueda
Puede usar operadores lógicos y operadores de búsqueda avanzada para refinar la búsqueda del contenido de Ayuda en el Visor de Ayuda.

## <a name="logical-operators"></a>Operadores lógicos
Los operadores lógicos especifican cómo se deben combinar varios términos de búsqueda en una consulta de búsqueda. En la siguiente tabla se muestran los operadores lógicos AND, OR, NOT y NEAR.
  
|Para buscar|Uso|Ejemplo|Resultado|  
|-------------------|---------|-------------|------------|  
|Ambos términos en el mismo artículo|AND|dib AND paleta|Temas que contienen "dib" y "paleta".|  
|Cualquier término en un artículo|O|trama OR vector|Temas que contienen "trama" o "vector".|  
|El primer término sin el segundo término en el mismo artículo|NOT|"sistema operativo" NOT DOS|Temas que contienen "sistema operativo", pero no "DOS".|  
|Ambos términos, próximos entre sí en un artículo|CERCA_DE|usuario NEAR kernel|Temas que contienen "usuario" cerca de "kernel".|  
  
> [!IMPORTANT]
> Debe escribir los operadores lógicos con todas las letras en mayúsculas para que el motor de búsqueda los reconozca.

## <a name="advanced-operators"></a>Operadores avanzados
Los operadores de búsqueda avanzada refinan la búsqueda de contenido. Para ello, especifican en qué parte de un artículo se debe buscar el término de búsqueda. En la tabla siguiente se describen los cuatro operadores de búsqueda avanzada disponibles.

|Para buscar|Uso|Ejemplo|Resultado|  
|-------------------|---------|-------------|------------|  
|Un término en el título del artículo|title:|title:binaryreader|Temas que contienen "binaryreader" en sus títulos.|  
|Un término en un ejemplo de código|code:|code:readdouble|Temas que contienen "readdouble" en un ejemplo de código.|  
|Un término en un ejemplo de un lenguaje de programación específico|code:vb:|code:vb:string|Temas que contienen "string" en un ejemplo de código de Visual Basic.|  
|Un artículo que está asociado a una palabra clave de índice específica|keyword:|keyword:readbyte|Temas que están asociados con la palabra clave de índice "readbyte".|  

> [!IMPORTANT]
> Debe escribir operadores de búsqueda avanzada con dos puntos finales y ningún espacio antes de los dos puntos para que el motor de búsqueda los reconozca.    

### <a name="programming-languages-for-code-examples"></a>Lenguajes de programación para ejemplos de código
Puede usar el operador **code:** para encontrar contenido sobre cualquiera de los distintos lenguajes de programación. Para devolver ejemplos de un lenguaje de programación específico, use uno de los valores de lenguaje de programación siguientes:  

|Lenguaje de programación|Sintaxis del operador de búsqueda|  
|--------------------|---------|  
|Visual Basic|code:vb<br/>code:visualbasic|  
|C#|code:c#<br/>code:csharp|  
|C++|code:cpp<br/>code:c++<br/>code:cplusplus|  
|F#|code:f#<br/>code:fsharp|  
|JavaScript|code:javascript<br/>code:js|  
|XAML|code:xaml|

> [!NOTE]
> El operador **code:** solamente busca contenido que está marcado con una etiqueta de lenguaje de programación, en lugar de contenido que normalmente está marcado como código. 
  
## <a name="see"></a>Vea 
[Búsqueda por temas](how-to-search-for-topics.md)  
[Visor de Ayuda de Microsoft](microsoft-help-viewer.md)