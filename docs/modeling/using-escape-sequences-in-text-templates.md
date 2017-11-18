---
title: Usar secuencias de Escape en las plantillas de texto | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: text templates, escape sequences
ms.assetid: 36fff542-2f42-460f-a2d5-03fc76817f3b
caps.latest.revision: "29"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: fdf062c9b33dd4a160f54bba83991a3cdda7f0d1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="using-escape-sequences-in-text-templates"></a>Usar secuencias de escape en las plantillas de texto
Puede utilizar secuencias de escape en las plantillas de texto para generar etiquetas de plantilla de texto y (en código C# solamente) para los caracteres de escape de control y comillas.  
  
 Para imprimir etiquetas de apertura y cierre de un bloque de código estándar para el archivo de salida, escape las etiquetas como se indica a continuación:  
  
```  
\<# ... \#>  
```  
  
 Puede hacer lo mismo con otras etiquetas de bloque de código y directiva de plantilla de texto.  
  
 Si un bloque de texto incluye cadenas usadas para escapar etiquetas de plantilla de texto, puede usar las secuencias de escape siguientes:  
  
-   Si una etiqueta de plantilla de texto está precedida por un número par de escape (\\) caracteres de la plantilla de analizador incluirá la mitad de los caracteres de escape e incluyen la secuencia como una etiqueta de plantilla de texto. Por ejemplo, si hay cuatro caracteres de escape en la plantilla de texto, habrá dos "\\" caracteres en el archivo generado.  
  
-   Si la etiqueta de la plantilla de texto está precedida por un número impar de escape (\\) caracteres, el analizador de la plantilla incluirá la mitad de la "\\" caracteres además de la etiqueta en Sí (\<# o #>). La etiqueta no se considera una etiqueta de plantilla de texto.  
  
-   Si un escape (\\) caracteres aparece en cualquier lugar en cualquier orden que no sea de escape que aplica un carácter de control o una comilla (solo en C#), el carácter se obtendrán como resultado directamente.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Generar plantillas desde otras plantillas mediante secuencias de escape](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)