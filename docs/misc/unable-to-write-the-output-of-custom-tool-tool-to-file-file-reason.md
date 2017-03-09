---
title: "Unable to write the output of custom tool &#39;tool&#39; to file &#39;file&#39;. &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.cannot_write_gen_output"
ms.assetid: eafcee9e-186b-4019-9042-8d8f9fc0925a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Unable to write the output of custom tool &#39;tool&#39; to file &#39;file&#39;. &lt;reason&gt;
El sistema del proyecto no puede escribir el resultado de la herramienta personalizada en el archivo especificado.  
  
 Siempre que el nombre de archivo de una entrada de la herramienta personalizada permanezca inalterado, el resultado de una herramienta personalizada se escribe en el mismo archivo.  Este error se produce si el resultado generado está bloqueado en el disco.  
  
 **Para corregir este error**  
  
-   Reinicie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y vuelva a ejecutar la herramienta personalizada haciendo clic con el botón secundario en el archivo afectado y seleccionando **Ejecutar herramienta personalizada** en el menú contextual.  
  
     Es probable que el archivo generado no esté actualizado, porque el sistema del proyecto no haya podido actualizarlo.