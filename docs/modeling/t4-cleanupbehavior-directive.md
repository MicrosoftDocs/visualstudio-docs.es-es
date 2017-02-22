---
title: "T4 CleanUpBehavior (Directiva) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9e5a211f-a3bf-4229-bff0-7d2e45b71c64
caps.latest.revision: 2
caps.handback.revision: 2
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# T4 CleanUpBehavior (Directiva)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Para eliminar el objeto appDomain después de procesar una plantilla de texto, incluya la línea siguiente:  
  
```  
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>  
```  
  
 Las plantillas de texto se procesan en un objeto appDomain que es independiente del proceso host.  En la mayoría de los casos, cuando se ha procesado una plantilla de texto, el objeto appdomain se utiliza de nuevo para procesar la plantilla siguiente.  Sin embargo, si especifica CleanupBehavior, el objeto appDomain se elimina y la plantilla siguiente se procesará en un nuevo objeto appDomain.  
  
 Esto reduce el procesamiento de texto, pero puede ser útil para garantizar que se desechan los recursos.  
  
 Esta directiva solo funciona en el host de Visual Studio.