---
title: Búsqueda de temas (Visor de Ayuda)
description: Obtenga información sobre cómo buscar temas en el Visor de Ayuda de Microsoft. Personalice las búsquedas mediante expresiones comodín, operadores lógicos y operadores de búsqueda avanzada.
ms.date: 11/02/2017
ms.topic: how-to
ms.assetid: 683f1b0c-1551-4bba-91fe-3855f03fdd69
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4ebf3bbd1fe04b13f31de7ebd8c513de670dd480
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944139"
---
# <a name="how-to-search-for-topics"></a>Búsqueda de temas

Puede usar la característica de búsqueda de texto completo para buscar todos los temas que contienen una palabra determinada. También puede refinar y personalizar la búsqueda mediante el uso de expresiones comodín, operadores lógicos y operadores de búsqueda avanzada.

Para abrir la pestaña **Buscar** , elija la pestaña **Buscar** en la ventana del visor de **ayuda** , o bien, si es un usuario de teclado, presione **Ctrl** + **E**.

## <a name="to-perform-a-full-text-search"></a>Para realizar una búsqueda de texto completo

1. En el cuadro de búsqueda, escriba la palabra que quiera buscar.

2. En la consulta de búsqueda, especifique qué operadores de búsqueda lógicos o avanzados se aplicarán a la búsqueda, en caso de que los haya. Para buscar en toda la ayuda disponible, no use operadores.

    > [!NOTE]
    > En el cuadro de diálogo **Opciones del Visor**, puede especificar preferencias adicionales, como el número máximo de resultados de la búsqueda que se mostrarán en todo momento o si se debe incluir contenido en inglés si la configuración regional principal no es inglés.

3. Presione la tecla **ENTRAR**.

     De forma predeterminada, una búsqueda devuelve un máximo de 200 aciertos y los muestra en el área de resultados de la búsqueda. Podría aparecer información adicional sobre la versión para cada resultado, en función del contenido.

4. Para ver un tema, seleccione el título en la lista de resultados.

## <a name="full-text-search-tips"></a>Sugerencias para la búsqueda de texto completo

Puede crear búsquedas más selectivas que devuelvan solo los temas que le interesan si entiende cómo afecta la sintaxis a la consulta. La sintaxis incluye caracteres especiales, palabras reservadas y filtros. En este tema se proporcionan sugerencias, procedimientos e información detallada de la sintaxis para ayudarle a crear mejor sus consultas.

### <a name="general-guidelines"></a>Directrices generales

En la tabla siguiente se incluyen algunas reglas y directrices básicas para realizar consultas de búsqueda en la ayuda.

|Sintaxis|Descripción|
|------------|-----------------|
|Distinción entre mayúsculas y minúsculas|Las búsquedas no distinguen entre mayúsculas y minúsculas. Desarrolle los criterios de búsqueda usando caracteres en mayúsculas o en minúsculas. Por ejemplo, "OLE" y "ole" devuelven los mismos resultados.|
|Combinaciones de caracteres|No es posible buscar una sola letra (a-z) o un solo número (0-9). Si intenta buscar ciertas palabras reservadas, por ejemplo "y", "de" y "con", estas se omitirán. Para obtener más información, vea [Palabras omitidas en las búsquedas](#stopwords) más adelante en este tema.|
|Orden de evaluación|Las consultas de búsqueda se evalúan de izquierda a derecha.|

### <a name="search-syntax"></a>Sintaxis de búsqueda

Si especifica una cadena de búsqueda que incluye varias palabras, como "palabra1 palabra2", esa cadena es equivalente a escribir "palabra1 Y palabra2", que devuelve solo los temas que contienen todas las palabras individuales en la cadena de búsqueda.

> [!IMPORTANT]
> - No se admite la búsqueda de frases. Si se especifica más de una palabra en una cadena de búsqueda, los temas devueltos contendrán todas las palabras que ha especificado pero no necesariamente la frase exacta especificada.
> - Use los operadores lógicos para especificar la relación entre las palabras en la frase de búsqueda. Puede incluir operadores lógicos, como Y, O, NO y CERCA_DE, para restringir más la búsqueda. Por ejemplo, si busca "declarar CERCA_DE unión", los resultados de la búsqueda incluirán temas que contengan las palabras "declarar" y "unión" cerca la una de la otra. Para obtener más información, vea [Operadores lógicos en expresiones de búsqueda](../help-viewer/logical-operators-search-expressions.md).

### <a name="filters"></a>Filtros

Puede restringir aún más los resultados de la búsqueda mediante los operadores de búsqueda avanzada. La Ayuda incluye tres categorías que puede usar para filtrar los resultados de una búsqueda de texto completo: Título, Código y Palabra clave.

### <a name="ranking-of-search-results"></a>Clasificación de resultados de la búsqueda

El algoritmo de búsqueda aplica ciertos criterios para ayudar a situar los resultados de la búsqueda más arriba o más abajo en la lista de resultados. En general:

1. El contenido que incluye palabras de búsqueda en el título tiene mejor clasificación que el que no lo hace.

2. El contenido que incluye palabras de búsqueda muy próximas tiene mejor clasificación que el que no lo hace.

3. El contenido con una mayor densidad de las palabras de búsqueda tiene mejor clasificación que el contenido con una densidad inferior.

### <a name=""></a><a name="stopwords"> Palabras omitidas en las búsquedas (palabras irrelevantes) </a>

Las palabras o números que aparecen más habitualmente, a veces llamadas palabras irrelevantes, se omiten automáticamente durante una búsqueda de texto completo. Por ejemplo, si busca la frase "pasar por", los resultados de la búsqueda mostrarán los temas que contienen la palabra "pasar", pero no "por".

## <a name="see-also"></a>Vea también

- [Operadores lógicos y avanzados](../help-viewer/logical-operators-search-expressions.md)
- [Cómo: buscar temas en el índice](../help-viewer/find-topics-index.md)
- [Búsqueda de temas en la TDC](../help-viewer/find-topics-toc.md)
- [Visor de Ayuda de Microsoft](../help-viewer/overview.md)