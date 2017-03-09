---
title: "Se ha especificado un valor no v&#225;lido para el registro de eventos. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b1b158bd-f13f-4371-a8af-31c0e86ae6be
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Se ha especificado un valor no v&#225;lido para el registro de eventos.
Se ha especificado un valor no válido para el registro de eventos. Normalmente, se genera por caracteres no válidos en el nombre, un nombre de archivo en blanco o un nombre de archivo es demasiado largo.  
  
### Para corregir este error  
  
-   Si el nombre especificado tiene más de ocho caracteres, asegúrese de que no haya ningún conflicto con los nombres de otros registros de eventos. Al determinar si el nombre es único, se evalúan solo los primeros ocho caracteres.  
  
-   Si se proporciona una ruta de acceso, asegúrese de que se analiza correctamente.  
  
-   Compruebe que no hay ningún carácter no válido en el nombre. Los caracteres que no se pueden usar en un nombre de archivo incluyen `<`, `>`, `:`, `"`, `/`, `\` y `|`.  
  
## Vea también  
 [Cómo: Analizar rutas de acceso a archivos](../Topic/How%20to:%20Parse%20File%20Paths%20in%20Visual%20Basic.md)   
 [Cómo: Cambiar el nombre de un archivo](../Topic/How%20to:%20Rename%20a%20File%20in%20Visual%20Basic.md)   
 [How to: Create and Remove Custom Event Logs](http://msdn.microsoft.com/es-es/af9b7da0-80c7-46ac-b7f7-897063ddd503)