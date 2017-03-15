---
title: "No se han podido copiar los resultados compilados en el Web | Microsoft Docs"
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
  - "vs.tasklisterror.cantcopyoutputstoweb"
ms.assetid: 59cf714b-cf7d-4df9-81ae-d3254969d5bc
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# No se han podido copiar los resultados compilados en el Web
El sistema del proyecto no pudo copiar uno o más archivos de salida de compilación \(por ejemplo, la DLL de compilación, el archivo PDB o los ensamblados satélite\) en el servidor web.  
  
 Este error indica que uno o más archivos de salida de compilación no se copiaron en el servidor web.  
  
 Este error suele producirse si un archivo de salida de la compilación está bloqueado o es de solo lectura en el servidor. Si un archivo está bloqueado en el servidor, indica que [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] en tiempo de ejecución no copió correctamente los ensamblados, los satélites o los símbolos de depuración que están actualmente en el servidor.  
  
 También es posible que el servidor no tenga espacio en disco suficiente o que problemas de red impidan que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cargue los archivos en la Web.  
  
### Para corregir este error  
  
1.  Compruebe el espacio en disco.  
  
2.  Si un archivo está bloqueado, reinicie el servidor web para liberar el bloqueo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] en los archivos afectados.  
  
## Vea también  
 [PDB Files](http://msdn.microsoft.com/es-es/1761c84e-8c2c-4632-9649-b5f99964ed3f)