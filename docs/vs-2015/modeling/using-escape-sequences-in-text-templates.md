---
title: Usar secuencias de Escape en plantillas de texto | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, escape sequences
ms.assetid: 36fff542-2f42-460f-a2d5-03fc76817f3b
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 24e2629001d7c426193059175eab64ea0ab8dacf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47575633"
---
# <a name="using-escape-sequences-in-text-templates"></a>Usar secuencias de escape en las plantillas de texto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [usando secuencias de Escape en plantillas de texto](https://docs.microsoft.com/visualstudio/modeling/using-escape-sequences-in-text-templates).  
  
Puede utilizar secuencias de escape en las plantillas de texto para generar etiquetas de plantilla de texto y (en C# solo código) para los caracteres de escape de control y entre comillas.  
  
 Para imprimir las etiquetas de apertura y cierre de un bloque de código estándar para el archivo de salida, escape las etiquetas como sigue:  
  
```  
\<# ... \#>  
```  
  
 Puede hacer lo mismo con otras etiquetas de bloque de código y directiva de plantilla de texto.  
  
 Si un bloque de texto incluye cadenas utilizadas para las etiquetas de plantilla de texto de escape, se pueden utilizar las secuencias de escape siguientes:  
  
-   Si una etiqueta de plantilla de texto está precedida por un número par de escape (\\) caracteres de la plantilla del analizador se incluyen la mitad de los caracteres de escape y se incluyen la secuencia como una etiqueta de plantilla de texto. Por ejemplo, si hay cuatro caracteres de escape en la plantilla de texto, habrá dos "\\" caracteres en el archivo generado.  
  
-   Si la etiqueta de la plantilla de texto está precedida por un número impar de escape (\\) caracteres, el analizador de plantilla incluirá la mitad de la "\\" caracteres además de la propia etiqueta (\<# o #>). La etiqueta no se considera una etiqueta de plantilla de texto.  
  
-   Si un carácter de escape (\\) carácter aparece en cualquier parte de cualquier secuencia que no sea de escape que aplica un carácter de control o una oferta (solo en C#), el carácter se generarán directamente.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Generar plantillas desde otras plantillas mediante secuencias de escape](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)



