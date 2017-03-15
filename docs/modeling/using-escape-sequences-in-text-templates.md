---
title: "Using Escape Sequences in Text Templates | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, escape sequences"
ms.assetid: 36fff542-2f42-460f-a2d5-03fc76817f3b
caps.latest.revision: 29
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 29
---
# Using Escape Sequences in Text Templates
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede utilizar secuencias de escape en las plantillas de texto para generar etiquetas de plantilla de texto y \(en código de C\# solamente\) para aplicar secuencias de escape a caracteres de control y comillas.  
  
 Para imprimir las etiquetas de apertura y cierre de un bloque de código estándar en el archivo de salida, aplique secuencias de escape a las etiquetas de la manera siguiente:  
  
```  
\<# ... \#>  
```  
  
 Puede hacer lo mismo con otras etiquetas de bloque de código y directiva de plantilla de texto.  
  
 Si un bloque de texto incluye cadenas que se utilizan para aplicar secuencias de escape a las etiquetas de plantilla de texto, debe usar las siguientes secuencias de escape:  
  
-   Si un número par de caracteres de escape \(\\\) precede a una etiqueta de plantilla de texto, el analizador de la plantilla incluirá la mitad de los caracteres de escape e incluirá la secuencia como una etiqueta de plantilla de texto.  Por ejemplo, si hay cuatro caracteres de escape en la plantilla de texto, habrá dos caracteres "\\" en el archivo generado.  
  
-   Si un número impar de caracteres de escape \(\\\) precede a la etiqueta de plantilla de texto, el analizador de la plantilla incluirá la mitad de los caracteres "\\" más la propia etiqueta \(\<\# o \#\>\).  La etiqueta no se considera como etiqueta de plantilla de texto.  
  
-   Si aparece un carácter de escape \(\\\) en cualquier otra parte de una secuencia distinta de una secuencia de escape que se aplica a caracteres de control o comillas \(solamente en C\#\), el carácter se incluye directamente en la salida.  
  
## Vea también  
 [How to: Generate Templates from Templates By Using Escape Sequences](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)