---
title: Usar secuencias de escape en las plantillas de texto
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4e03f5eafc00b8431725ed06da10371a93692fb5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662918"
---
# <a name="use-escape-sequences-in-text-templates"></a>Usar secuencias de escape en las plantillas de texto

Puede usar secuencias de escape en las plantillas de texto para generar etiquetas de plantilla de C# texto y (solo en código) para caracteres de control de escape y Comillas.

Para imprimir etiquetas de apertura y cierre para un bloque de código estándar en el archivo de salida, escape de las etiquetas como se indica a continuación:

```
\<# ... \#>
```

Puede hacer lo mismo con otras directivas de plantilla de texto y etiquetas de bloque de código.

Si un bloque de texto incluye cadenas usadas para escapar etiquetas de plantilla de texto, puede usar las siguientes secuencias de escape:

- Si una etiqueta de plantilla de texto va precedida por un número par de caracteres de escape (\\), el analizador de la plantilla incluirá la mitad de los caracteres de escape e incluirá la secuencia como una etiqueta de plantilla de texto. Por ejemplo, si hay cuatro caracteres de escape en la plantilla de texto, habrá dos caracteres "\\" en el archivo generado.

- Si la etiqueta de la plantilla de texto está precedida por un número impar de caracteres de escape (\\), el analizador de la plantilla incluirá la mitad de los caracteres "\\" más la propia etiqueta (\< # o # >). La etiqueta no se considera una etiqueta de plantilla de texto.

- Si aparece un carácter de escape (\\) en cualquier otra secuencia distinta de la que escapa a un carácter de control o a una comilla (solo en C# ), el carácter se generará directamente.

## <a name="see-also"></a>Vea también

- [Cómo: Generar plantillas desde otras plantillas mediante secuencias de escape](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)