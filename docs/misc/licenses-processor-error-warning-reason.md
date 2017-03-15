---
title: "Licenses processor error/warning: &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.licx_generator_task"
ms.assetid: 85750198-7bd3-4936-b1eb-954dcc3ff573
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Licenses processor error/warning: &lt;reason&gt;
Se muestra un mensaje de error o advertencia si una herramienta devuelve un error o advertencia al procesar un archivo .licx.  Como parte del proceso de compilación, el sistema del proyecto transformará el archivo Licenses.licx \(si existe\) en un archivo binario comprensible para el administrador de licencias [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Esta transformación se realiza mediante herramientas en proceso.  
  
 La causa más probable del error o advertencia es un archivo .licx dañado.  Un archivo .licx puede dañarse si se ha editado fuera de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mediante un editor de texto.  
  
 Estos archivos normalmente los administran los Diseñadores de Windows Forms y formularios Web Forms.  
  
### Para corregir este error  
  
1.  Corrija el formato del archivo .licx.  
  
     Un error significa que no se ha generado el archivo binario y fallará el proceso de compilación.  Las advertencias se proporcionan con fines informativos solamente.  
  
## Vea también  
 [File Types and File Extensions in Visual Basic and Visual C\#](http://msdn.microsoft.com/es-es/f793852c-da06-4d52-a826-65f635844772)