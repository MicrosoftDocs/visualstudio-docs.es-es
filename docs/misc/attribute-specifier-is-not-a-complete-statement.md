---
title: "El especificador de atributo no es una instrucci&#243;n completa | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32035"
  - "bc32035"
helpviewer_keywords: 
  - "BC32035"
ms.assetid: a0ddd673-4170-4bea-9c22-777d7bf21dfd
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El especificador de atributo no es una instrucci&#243;n completa
El especificador de atributo no es una instrucción completa. Utilice una continuación de línea para aplicar el atributo a la instrucción siguiente.  
  
 Un bloque de atributos aparece solo en una línea de código fuente. Los atributos deben aplicarse al principio de una instrucción de declaración y deben formar parte de esa instrucción.  
  
 **Id. de error:** BC32035  
  
### Para corregir este error  
  
-   Si la instrucción de declaración está en la línea siguiente, agregue un espacio y un carácter de subrayado \(`_`\) detrás del bloque de atributo para combinar las líneas del código fuente.  
  
-   Si no hay ninguna instrucción de declaración asociada al bloque de atributos, facilite una o quite el bloque de atributos.  
  
-   Si el atributo se va a aplicar a todo el ensamblado o al módulo de ensamblado actual, el bloque de atributos permanece en una línea de código fuente independiente. Incluya el nombre de atributo dentro de corchetes angulares \(`< >`\) con `Assembly:` o `Module:` y no agregue un espacio ni un carácter de subrayado detrás del bloque de atributos. Además, asegúrese de que este bloque de atributos se encuentre al principio del archivo de código fuente.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Aplicación de atributos](http://msdn.microsoft.com/es-es/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Cómo: Interrumpir y combinar instrucciones en código](../Topic/How%20to:%20Break%20and%20Combine%20Statements%20in%20Code%20\(Visual%20Basic\).md)