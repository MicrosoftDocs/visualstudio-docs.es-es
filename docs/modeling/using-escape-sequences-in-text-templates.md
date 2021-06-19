---
title: Usar secuencias de escape en las plantillas de texto
description: Obtenga información sobre cómo puede usar secuencias de escape en plantillas de texto para generar etiquetas de plantilla de texto y para escapar caracteres de control y comillas solo en código de C#.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2a3cdabd38f2bf4ef38a31807fabed3ac837b26b
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388456"
---
# <a name="use-escape-sequences-in-text-templates"></a>Uso de secuencias de escape en plantillas de texto

Puede usar secuencias de escape en plantillas de texto para generar etiquetas de plantilla de texto y (solo en código de C#) para caracteres de control de escape y comillas.

Para imprimir las etiquetas de apertura y cierre de un bloque de código estándar en el archivo de salida, etiquete las etiquetas como se muestra a continuación:

```
\<# ... \#>
```

Puede hacer lo mismo con otra directiva de plantilla de texto y etiquetas de bloque de código.

Si un bloque de texto incluye cadenas que se usan para escapar etiquetas de plantilla de texto, puede usar las siguientes secuencias de escape:

- Si una etiqueta de plantilla de texto va precedida de un número par de caracteres de escape ( ), el analizador de plantillas incluirá la mitad de los caracteres de escape e incluirá la secuencia como una etiqueta de \\ plantilla de texto. Por ejemplo, si hay cuatro caracteres de escape en la plantilla de texto, habrá dos caracteres \\ "" en el archivo generado.

- Si la etiqueta de plantilla de texto va precedida de un número impar de caracteres de escape ( ), el analizador de plantillas incluirá la mitad de los caracteres " " más la \\ \\ propia etiqueta ( \<# or #> ). La etiqueta no se considera una etiqueta de plantilla de texto.

- Si aparece un carácter de escape ( ) en cualquier otra secuencia que no sea donde se escape un carácter de control o una comilla (solo en C#), el carácter se mostrará \\ directamente.

## <a name="see-also"></a>Vea también

- [Cómo: Generar plantillas desde otras plantillas mediante secuencias de escape](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)
