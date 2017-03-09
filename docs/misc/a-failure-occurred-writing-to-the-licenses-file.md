---
title: "A failure occurred writing to the licenses file | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.fail_writing_licenses_file"
ms.assetid: 7ea1e2ac-fc94-4d53-8ce9-2ae31bcba85d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# A failure occurred writing to the licenses file
El sistema del proyecto no pudo escribir en el archivo transformado.  Como parte de la preparación de licencias, el sistema del proyecto transformará los archivos de texto .licx en archivos binarios de licencias comprensibles para el sistema de licencias de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 Entre los motivos posibles para este error se incluyen la falta de espacio libre en el disco del dispositivo o que se alcance el límite MAX\_PATH para nombres de archivos.  
  
 **Para corregir este error**  
  
-   Mueva el proyecto a una carpeta diferente con un nombre corto de ruta de acceso absoluta o abrevie el nombre del archivo de salida.  
  
     El proceso de compilación no finalizará correctamente si ocurre este error.  
  
## Vea también  
 [How to: License Components and Controls](../Topic/How%20to:%20License%20Components%20and%20Controls.md)