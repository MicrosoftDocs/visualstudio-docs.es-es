---
title: "Resources processor error/warning: &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.resx_generator_task"
ms.assetid: eb9a1bd0-7e63-4a2b-ad37-54f6e67d9b5a
caps.latest.revision: 7
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Resources processor error/warning: &lt;reason&gt;
Se muestra un mensaje de error o advertencia si una herramienta devuelve un error o advertencia al procesar un archivo .resx.  Como parte del proceso de compilación, el sistema del proyecto transformará los archivos .resx en archivos binarios comprensibles para el administrador de recursos de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Esta transformación se realiza mediante herramientas en proceso.  
  
 La causa más probable del error o advertencia es un archivo .resx dañado.  Un archivo .resx puede dañarse si se ha editado fuera de Visual Studio o en Visual Studio mediante un editor de texto.  
  
 Estos archivos normalmente los administran los Diseñadores de Windows Forms y formularios Web Forms.  
  
### Para corregir este error  
  
1.  Corrija el formato del archivo .resx.  
  
     Un error significa que no se ha generado el archivo binario y fallará el proceso de compilación.  Las advertencias se proporcionan con fines informativos solamente.  
  
## Vea también  
 [Resources in .Resx File Format](http://msdn.microsoft.com/es-es/0c476133-87e4-47e8-b0ef-4b88f4ef3dc5)