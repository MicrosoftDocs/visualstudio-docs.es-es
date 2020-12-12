---
title: Usar secuencias de escape en las plantillas de texto
description: Obtenga información sobre cómo puede usar secuencias de escape en las plantillas de texto para generar etiquetas de plantilla de texto y caracteres de control de escape y Comillas solo en el código de C#.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b007a9b5ccf41a27cda7d9833064eb60394c4dc
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361331"
---
# <a name="use-escape-sequences-in-text-templates"></a>Usar secuencias de escape en las plantillas de texto

Puede usar secuencias de escape en las plantillas de texto para generar etiquetas de plantilla de texto y (solo en código C#) para caracteres de control de escape y Comillas.

Para imprimir etiquetas de apertura y cierre para un bloque de código estándar en el archivo de salida, escape de las etiquetas como se indica a continuación:

```
\<# ... \#>
```

Puede hacer lo mismo con otras directivas de plantilla de texto y etiquetas de bloque de código.

Si un bloque de texto incluye cadenas usadas para escapar etiquetas de plantilla de texto, puede usar las siguientes secuencias de escape:

- Si una etiqueta de plantilla de texto está precedida por un número par de caracteres de escape ( \\ ), el analizador de la plantilla incluirá la mitad de los caracteres de escape e incluirá la secuencia como una etiqueta de plantilla de texto. Por ejemplo, si hay cuatro caracteres de escape en la plantilla de texto, habrá dos caracteres " \\ " en el archivo generado.

- Si la etiqueta de la plantilla de texto está precedida por un número impar de caracteres de escape ( \\ ), el analizador de la plantilla incluirá la mitad de los \\ caracteres "" más la propia etiqueta ( \<# or #> ). La etiqueta no se considera una etiqueta de plantilla de texto.

- Si \\ aparece un carácter de escape () en cualquier otra secuencia distinta de la que escapa a un carácter de control o a una comilla (solo en C#), el carácter se generará directamente.

## <a name="see-also"></a>Consulta también

- [Cómo: Generar plantillas desde otras plantillas mediante secuencias de escape](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)
