---
title: "Resources &#39;file1&#39; and &#39;file2&#39; have the same manifest resource name &#39;name&#39; | Microsoft Docs"
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
  - "vs.tasklisterror.resource_naming_conflict"
ms.assetid: 50d656ad-8557-4240-95b0-3f44b9c21da6
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Resources &#39;file1&#39; and &#39;file2&#39; have the same manifest resource name &#39;name&#39;
El sistema del proyecto ha calculado nombres de recursos de ensamblado idénticos para dos archivos que tengan la propiedad `BuildAction` establecida en `EmbeddedResource` y una referencia cultural neutra.  El proceso de compilación no finalizará correctamente si ocurre este error.  Para obtener más información sobre la propiedad `BuildAction`, vea [File Properties](http://msdn.microsoft.com/es-es/013c4aed-08d6-4dce-a124-ca807ca08959).  
  
 Debido a que [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] no tiene noción de espacios de nombres basados en carpetas, los nombres de archivos de recursos:  
  
-   Proj1\\FolderA\\MyProj.bmp  
  
-   Proj1\\FolderB\\MyProj.bmp  
  
 producirán el nombre de manifiesto del ensamblado Proj1.MyProj.bmp para ambos archivos.  
  
 **Para corregir este error**  
  
-   Para resolver este error, cambie el nombre de los archivos de recursos afectados \(*archivo1* y *archivo2*\).  
  
## Vea también  
 [NIB: Resource File Naming Conventions](http://msdn.microsoft.com/es-es/7b1a2cdf-6196-4034-8fc7-51a271842cc2)