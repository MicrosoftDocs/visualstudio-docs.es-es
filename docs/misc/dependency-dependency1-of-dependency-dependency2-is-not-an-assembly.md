---
title: "La dependencia &#39;dependencia1&#39; de la dependencia &#39;dependencia2&#39; no es un ensamblado | Microsoft Docs"
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
  - "vs.tasklisterror.notcomplusassembly2"
ms.assetid: e3b96601-458e-40de-81ea-ddcae9b42996
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# La dependencia &#39;dependencia1&#39; de la dependencia &#39;dependencia2&#39; no es un ensamblado
El sistema del proyecto ha determinado que una dependencia concreta \(dependencia1\) de un ensamblado \(dependencia2\) no es un ensamblado .NET.  
  
 **Para corregir este error**  
  
-   Reinstale [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \(si el ensamblado venía incluido con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o .NET Framework\).  
  
     o bien  
  
-   Reinstale el control de terceros adecuado.  
  
     Este error no impedirá que se compile el proyecto. Sin embargo, podría producirse un error en tiempo de ejecución.  
  
## Vea también  
 [Solucionar problemas de referencias rotas](../ide/troubleshooting-broken-references.md)   
 [NO ESTÁ EN LA COMPILACIÓN: Cómo: agregar o quitar referencias mediante el cuadro de diálogo Agregar referencia](http://msdn.microsoft.com/es-es/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Assemblies in the Common Language Runtime](http://msdn.microsoft.com/es-es/33a0bc6a-6bb3-44c7-ada7-4a046e8c0945)