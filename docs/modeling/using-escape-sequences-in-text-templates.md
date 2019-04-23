---
title: Usar secuencias de escape en las plantillas de texto
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c88c9c8769051724855d292bfefb56f69cb8dee
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60053174"
---
# <a name="using-escape-sequences-in-text-templates"></a>Usar secuencias de escape en las plantillas de texto
Puede utilizar secuencias de escape en las plantillas de texto para generar etiquetas de plantilla de texto y (en C# solo código) para los caracteres de escape de control y entre comillas.

 Para imprimir las etiquetas de apertura y cierre de un bloque de código estándar para el archivo de salida, escape las etiquetas como sigue:

```
\<# ... \#>
```

 Puede hacer lo mismo con otras etiquetas de bloque de código y directiva de plantilla de texto.

 Si un bloque de texto incluye cadenas utilizadas para las etiquetas de plantilla de texto de escape, se pueden utilizar las secuencias de escape siguientes:

- Si una etiqueta de plantilla de texto está precedida por un número par de escape (\\) caracteres de la plantilla del analizador se incluyen la mitad de los caracteres de escape y se incluyen la secuencia como una etiqueta de plantilla de texto. Por ejemplo, si hay cuatro caracteres de escape en la plantilla de texto, habrá dos "\\" caracteres en el archivo generado.

- Si la etiqueta de la plantilla de texto está precedida por un número impar de escape (\\) caracteres, el analizador de plantilla incluirá la mitad de la "\\" caracteres además de la propia etiqueta (\<# o #>). La etiqueta no se considera una etiqueta de plantilla de texto.

- Si un carácter de escape (\\) carácter aparece en cualquier parte de cualquier secuencia que no sea de escape que aplica un carácter de control o una oferta (solo en C#), el carácter se generarán directamente.

## <a name="see-also"></a>Vea también

- [Cómo: Generar plantillas desde otras plantillas mediante secuencias de escape](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)