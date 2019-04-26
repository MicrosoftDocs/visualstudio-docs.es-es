---
title: Operadores lógicos y avanzados en expresiones de búsqueda (Visor de Ayuda)
ms.date: 11/02/2017
ms.topic: reference
helpviewer_keywords:
- Help Viewer, logical operators in search
- logical operators in search [Help Viewer]
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc27a5206b7939cd55fc95878d2cc8968ae8bf39
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62974402"
---
# <a name="logical-and-advanced-operators-in-search-expressions"></a>Operadores lógicos y avanzados en expresiones de búsqueda

Puede usar operadores lógicos y operadores de búsqueda avanzados para refinar la búsqueda del contenido de Ayuda en el **Visor de Ayuda**.

## <a name="logical-operators"></a>Operadores lógicos

Los operadores lógicos especifican cómo se deben combinar varios términos de búsqueda en una consulta de búsqueda. En la siguiente tabla se muestran los operadores lógicos AND, OR, NOT y NEAR.

|Para buscar|Usar|Ejemplo|Resultado|
|-------------------|---------|-------------|------------|
|Ambos términos en el mismo artículo|AND|dib AND paleta|Temas que contienen "dib" y "paleta".|
|Cualquier término en un artículo|O|trama OR vector|Temas que contienen "trama" o "vector".|
|El primer término sin el segundo término en el mismo artículo|NOT|"sistema operativo" NOT DOS|Temas que contienen "sistema operativo", pero no "DOS".|
|Ambos términos, próximos entre sí en un artículo|CERCA_DE|usuario NEAR kernel|Temas que contienen "usuario" cerca de "kernel".|

> [!IMPORTANT]
> Debe escribir los operadores lógicos con todas las letras en mayúsculas para que el motor de búsqueda los reconozca.

## <a name="advanced-operators"></a>Operadores avanzados

Los operadores de búsqueda avanzada refinan la búsqueda de contenido. Para ello, especifican en qué parte de un artículo se debe buscar el término de búsqueda. En esta tabla se describen los cuatro operadores de búsqueda avanzada que hay disponibles.

|Para buscar|Usar|Ejemplo|Resultado|
|-------------------|---------|-------------|------------|
|Un término en el título del artículo|`title:`|`title:binaryreader`|Temas que contienen "binaryreader" en sus títulos.|
|Un término en un ejemplo de código|`code:`|`code:readdouble`|Temas que contienen "readdouble" en un ejemplo de código.|
|Un término en un ejemplo de un lenguaje de programación específico|`code:vb:`|`code:vb:string`|Temas que contienen "string" en un ejemplo de código de Visual Basic.|
|Un artículo que está asociado a una palabra clave de índice específica|`keyword:`|`keyword:readbyte`|Temas que están asociados con la palabra clave de índice "readbyte".|

> [!IMPORTANT]
> Debe escribir operadores de búsqueda avanzada con dos puntos finales y ningún espacio antes de los dos puntos para que el motor de búsqueda los reconozca.

### <a name="programming-languages-for-code-examples"></a>Lenguajes de programación para ejemplos de código

Puede usar el operador `code:` para buscar contenido sobre cualquiera de los distintos lenguajes de programación. Para devolver ejemplos de un lenguaje de programación específico, use uno de los valores de lenguaje de programación siguientes:

|Lenguaje de programación|Sintaxis del operador de búsqueda|
| - |---------|
|Visual Basic|`code:vb`<br/>`code:visualbasic`|
|C#|`code:c#`<br/>`code:csharp`|
|C++|`code:cpp`<br/>`code:c++`<br/>`code:cplusplus`|
|F#|`code:f#`<br/>`code:fsharp`|
|JavaScript|`code:javascript`<br/>`code:js`|
|XAML|`code:xaml`|

> [!NOTE]
> El operador `code:` solamente busca contenido que esté marcado con una etiqueta de lenguaje de programación, en lugar de contenido marcado genéricamente como código.

## <a name="see-also"></a>Vea también

- [Cómo: Buscar temas](../help-viewer/find-topics.md)
- [Visor de Ayuda de Microsoft](../help-viewer/overview.md)
