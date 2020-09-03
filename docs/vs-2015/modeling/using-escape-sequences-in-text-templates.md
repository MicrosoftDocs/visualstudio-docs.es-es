---
title: Usar secuencias de escape en las plantillas de texto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
ms.assetid: 36fff542-2f42-460f-a2d5-03fc76817f3b
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8a45aa36ddce57141a7e1e851f7f0766b77015ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659424"
---
# <a name="using-escape-sequences-in-text-templates"></a>Usar secuencias de escape en las plantillas de texto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="see-also"></a>Consulte también
 [Cómo: Generar plantillas desde otras plantillas mediante secuencias de escape](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)
