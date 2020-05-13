---
title: Usar expresiones regulares
ms.date: 09/13/2019
ms.topic: conceptual
f1_keywords:
- vsregularexpressionhelp
- vs.regularexpressionhelp
- vs.wildcardsbuilder
- vs.netregularexpressionhelp
- vs.wildcards
helpviewer_keywords:
- regular expressions [Visual Studio]
- regular expressions
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f1739d6b2376a4f86edd3c0102f7fad79da5d7cd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568625"
---
# <a name="use-regular-expressions-in-visual-studio"></a>Usar expresiones regulares en Visual Studio

Visual Studio usa [expresiones regulares de .NET](/dotnet/standard/base-types/regular-expressions) para buscar y reemplazar texto.

## <a name="regular-expression-examples"></a>Ejemplos de expresiones regulares

La siguiente tabla contiene algunos ejemplos de caracteres de expresión regular, operadores, construcciones y patrones. Para obtener una referencia más completa, consulte el artículo de [lenguaje de expresiones regulares](/dotnet/standard/base-types/regular-expression-language-quick-reference).

|Propósito|Expresión|Ejemplo|
|-------------|----------------|-------------|
|Coincidencia con cualquier carácter (excepto un salto de línea). Para obtener más información, consulte [Cualquier carácter](/dotnet/standard/base-types/character-classes-in-regular-expressions#any-character-).|.|`a.o` coincide con "aro" en "around" y "abo" en "about", pero no con "acro" en "across"|
|Coincidencia con cero o más apariciones de la expresión anterior (coincidencias con tantos caracteres como sea posible). Para obtener más información, consulte el artículo de [coincidencia con cero o más veces](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-).|*|`a*r` coincide con "r" en "rack", "ar" en "ark" y "aar" en "aardvark".|
|Coincidencia con cualquier carácter cero o más veces.|.*|`c.*e` coincide con "cke" en "racket", "comme" en "comment" y "code" en "code"|
|Coincidencia con una o más apariciones de la expresión anterior (coincidencia con tantos caracteres como sea posible). Para obtener más información, consulte el artículo de [coincidencia con una o más veces](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-).|+|`e+d` coincide con "eed" en "feeder" y "ed" en "faded".|
|Buscar cualquier carácter coincidente una o más veces.|.+|`e.+e` coincide con "eede" in "feeder" pero no encuentra ninguna coincidencia en "feed".|
|Coincidencia con cero o más apariciones de la expresión anterior (coincidencia con el menor número de caracteres posible). Para obtener más información, consulte el artículo de [coincidencia con cero o más veces (coincidencia diferida)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-lazy-match-).|*?|`\w*?d` coincide con "fad" y "ed" en "faded", pero no con toda la palabra "faded" debido a la coincidencia diferida.|
|Coincidencia con una o más apariciones de la expresión anterior (coincidencia con el menor número de caracteres posible). Para obtener más información, consulte el artículo de [coincidencia con uno o más veces (coincidencia diferida)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-lazy-match-).|+?|`e\w+?` coincide con "ee" en "asleep" y "ed" en "faded", pero no encuentra ninguna coincidencia en "fade".|
|Delimitación de la cadena coincidente al [principio de una cadena o línea](/dotnet/standard/base-types/anchors-in-regular-expressions#start-of-string-or-line-).|^|`^car` coincide con la palabra "car" solo cuando aparece al principio de una línea|
|Delimitación de la cadena coincidente al [final de una línea](/dotnet/standard/base-types/anchors-in-regular-expressions#end-of-string-or-line-).|\r?$|`car\r?$` coincide con "car" solo cuando aparece al final de una línea.|
|Delimitar la cadena coincidente al final del archivo|$|`car$` coincide con "car" solo cuando aparece al final del archivo.|
|Coincidencia con cualquier carácter único de un conjunto|[abc]|`b[abc]` coincide con "ba", "bb" y "bc"|
|Coincidir con cualquier carácter de un intervalo de caracteres|[a-f]|`be[n-t]` coincide con "bet" en "between", "ben" en "beneath" y "bes" en "beside", pero no encuentra ninguna coincidencia en "below".|
|Capturar y numerar implícitamente la expresión contenida entre paréntesis|()|`([a-z])X\1` coincide con "aXa" y "bXb", pero no con "aXb". "\1" hace referencia al primer grupo de expresión "[a-z]". Para obtener más información, vea [Grupos de captura y patrones de reemplazo](#capture-groups-and-replacement-patterns). |
|Invalidar una coincidencia|(?!abc)|`real(?!ity)` coincide con "real" en "realty" y "really", pero no con "reality". También encuentra el segundo “real” (pero no el primero) en “realityreal”.|
|Coincidencia con cualquier carácter que no está en un conjunto determinado de caracteres. Para obtener más información, consulte [Grupo de caracteres negativos](/dotnet/standard/base-types/character-classes-in-regular-expressions#negative-character-group-).|[^abc]|`be[^n-t]` coincide con "bef" en "before", "beh" en "behind" y "bel" en "below", pero no encuentra ninguna coincidencia en "beneath".|
|Coincidencia con la expresión situada antes o después del símbolo.|&#124;|`(sponge|mud) bath` coincide con "sponge bath" y "mud bath"|
|[Escape del carácter](/dotnet/standard/base-types/character-escapes-in-regular-expressions) que sigue a la barra diagonal inversa.| \\ |`\^` coincide con el carácter ^|
|Especificación del número de apariciones del carácter o grupo precedente. Para obtener más información, consulte el artículo de [coincidencia exacta n veces](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-exactly-n-times-n).|{n}, donde "n" es el número de apariciones|`x(ab){2}x` coincide con "xababx"<br/>`x(ab){2,3}x` coincide con "xababx" y "xabababx", pero no con "xababababx"|
|[Coincidencia con el texto en una clase de caracteres Unicode](/dotnet/standard/base-types/character-classes-in-regular-expressions#unicode-category-or-unicode-block-p). Para obtener más información sobre las clases de caracteres Unicode, consulte el artículo de [propiedades de caracteres Unicode estándar 5.2](http://www.unicode.org/versions/Unicode5.2.0/ch04.pdf).|\p{X}, donde "X" es el número de Unicode.|`\p{Lu}` coincide con "T" y "D" en "Thomas Doe"|
|[Coincidencia con un límite de palabra](/dotnet/standard/base-types/anchors-in-regular-expressions#word-boundary-b).|\b (fuera de una clase de caracteres `\b` especifica un límite de palabras y dentro de una clase de caracteres `\b` un retroceso).|`\bin` coincide con "in" en "inside", pero no encuentra ninguna coincidencia en "pinto".|
|Coincidencia con un salto de línea (es decir, con un retorno de carro seguido de una nueva línea).|\r?\n|`End\r?\nBegin` coincide con "End" y "Begin" solo cuando "End" es la última cadena en una línea y "Begin" es la primera cadena en la línea siguiente|
|Coincidencia con cualquier [carácter de una palabra](/dotnet/standard/base-types/character-classes-in-regular-expressions#word-character-w).|\w|`a\wd` coincide con "add" y "a1d", pero no con "a d"|
|Coincidencia con cualquier [carácter de espacio en blanco](/dotnet/standard/base-types/character-classes-in-regular-expressions#whitespace-character-s).|\s|`Public\sInterface` coincide con la frase "Public Interface"|
|Coincidencia con cualquier [carácter de dígito decimal](/dotnet/standard/base-types/character-classes-in-regular-expressions#decimal-digit-character-d).|\d|`\d` coincide con "4" y "0" en "wd40".|

`\b0[xX]([0-9a-fA-F]+\)\b` es un ejemplo de expresión regular que combina algunos de los operadores y construcciones para que coincida con un número hexadecimal. Esta expresión coincide con "0xc67f", pero no con "0xc67g".

> [!TIP]
> En sistemas operativos Windows, la mayoría de las líneas terminan en "\r\n" (un retorno de carro seguido de una nueva línea). Estos caracteres no se ven, pero están presentes en el editor y se pasan al servicio de expresiones regulares de .NET.

## <a name="capture-groups-and-replacement-patterns"></a>Grupos de captura y patrones de reemplazo

Un grupo de capturas delinea una subexpresión de una expresión regular y captura una subcadena de una cadena de entrada. Puede usar los grupos capturados en la expresión regular (por ejemplo, para buscar una palabra repetida) o en un patrón de reemplazo. Para obtener más información, consulte [Construcciones de agrupamiento en expresiones regulares](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions).

Para crear un grupo de capturas numerado, incluya la subexpresión entre paréntesis en el patrón de expresión regular. Las capturas se numeran automáticamente de izquierda a derecha según la posición de los paréntesis de apertura de la expresión regular. Para acceder al grupo capturado:

- **En la expresión regular**: Use `\number`. Por ejemplo, `\1` en la expresión regular `(\w+)\s\1` hace referencia al primer grupo de capturas `(\w+)`.

- **En un patrón de reemplazo**: Use `$number`. Por ejemplo, la expresión regular agrupada `(\d)([a-z])` define dos grupos: el primero contiene un único dígito decimal y el segundo, un solo carácter comprendido entre **a** y **z**. La expresión encuentra cuatro coincidencias en la cadena siguiente: **1a 2b 3c 4d**. La cadena de reemplazo `z$1` hace referencia al primer grupo (`$1`) y convierte la cadena a **z1 z2 z3 z4**.

La siguiente imagen muestra una expresión regular `(\w+)\s\1` y una cadena de reemplazo `$1`. La expresión regular y el patrón de reemplazo hacen referencia el primer grupo de capturas al que se asigna automáticamente el número 1. Cuando se elige **Reemplazar todo** en el cuadro de diálogo **Reemplazo rápido** de Visual Studio, se quitan las palabras repetidas del texto.

![Reemplazo rápido con un grupo de capturas numerado en Visual Studio](media/numbered-capture-group.png)

> [!TIP]
> Asegúrese de que el botón **Usar expresiones regulares** está seleccionado en el cuadro de diálogo **Reemplazo rápido**.

### <a name="named-capture-groups"></a>Grupos de capturas con nombre

En lugar de depender de la numeración automática de un grupo de capturas, puede asignarle un nombre. La sintaxis de un grupo de capturas con nombre es `(?<name>subexpression)`.

Los grupos de capturas con nombre, al igual que los grupos de capturas con nombre, se puede usar en la expresión regular o en un patrón de reemplazo. Para acceder al grupo de capturas con nombre:

- **En la expresión regular**: Use `\k<name>`. Por ejemplo, `\k<repeated>` en la expresión regular `(?<repeated>\w+)\s\k<repeated>` hace referencia al grupo de capturas que se denomina `repeated` y cuya subexpresión es `\w+`.

- **En un patrón de reemplazo**: Use `${name}`. Por ejemplo: `${repeated}`.

A modo de ejemplo, la siguiente imagen muestra una expresión regular `(?<repeated>\w+)\s\k<repeated>` y una cadena de reemplazo `${repeated}`. La expresión regular y el patrón de reemplazo hacen referencia el primer grupo de capturas llamado `repeated`. Cuando se elige **Reemplazar todo** en el cuadro de diálogo **Reemplazo rápido** de Visual Studio, se quitan las palabras repetidas del texto.

![Reemplazo rápido con un grupo de capturas con nombre en Visual Studio](media/named-capture-group.png)

> [!TIP]
> Asegúrese de que el botón **Usar expresiones regulares** está seleccionado en el cuadro de diálogo **Reemplazo rápido**.

Para obtener más información sobre los grupos de capturas con nombre, consulte [Subexpresiones coincidentes con nombre](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions#named-matched-subexpressions). Para obtener más información sobre las expresiones regulares que se usan en patrones de reemplazo, consulte [Sustituciones en expresiones regulares](/dotnet/standard/base-types/substitutions-in-regular-expressions).

## <a name="see-also"></a>Vea también

- [Lenguaje de expresiones regulares](/dotnet/standard/base-types/regular-expression-language-quick-reference)
- [Buscar y reemplazar texto](../ide/finding-and-replacing-text.md)
