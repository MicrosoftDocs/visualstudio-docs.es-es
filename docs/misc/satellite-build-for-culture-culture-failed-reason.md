---
title: "Satellite build for culture &#39;culture&#39; failed. &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.satellite_build_failed"
ms.assetid: c97c589f-cf4d-4f6b-941a-7526a1091fce
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Satellite build for culture &#39;culture&#39; failed. &lt;reason&gt;
No se puso compilar un ensamblado satélite para una referencia cultural específica.  Esto provocará un error en el proceso de compilación.  
  
 Este error puede aparecer por dos motivos:  
  
1.  ALINK.EXE no está instalado en el sistema.  
  
2.  ALINK.EXE ha fallado pero no ha devuelto ninguna información de error extendido.  
  
 **Para corregir este error**  
  
-   Vuelva a instalar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o solo [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
-   Si el \<motivo\> que se indica es "No se puede iniciar el vinculador de ensamblado.  El archivo ya existe", vacíe la carpeta Temp en la que se generaron los archivos \(por ejemplo, C:\\Documents and Settings\\\<usuario\>Local Settings\\Temp\).  
  
## Vea también  
 [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)