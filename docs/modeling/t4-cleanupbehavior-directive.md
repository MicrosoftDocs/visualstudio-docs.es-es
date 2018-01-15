---
title: T4 CleanUpBehavior (directiva) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f773f04799ec1ec975626699f37089c3c5b59b2d
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2018
---
# <a name="t4-cleanupbehavior-directive"></a>T4 CleanUpBehavior (Directiva)
Para eliminar el objeto appDomain después de procesar una plantilla de texto, incluya la línea siguiente:  
  
```  
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>  
```  
  
 Las plantillas de texto se procesan en un objeto appDomain que es independiente del proceso host. En la mayoría de los casos, cuando se ha procesado una plantilla de texto, el objeto appdomain se utiliza de nuevo para procesar la plantilla siguiente. Sin embargo, si especifica CleanupBehavior, el objeto appDomain se elimina y la plantilla siguiente se procesará en un nuevo objeto appDomain.  
  
 Esto reduce el procesamiento de texto, pero puede ser útil para garantizar que se desechan los recursos.  
  
 Esta directiva solo funciona en el host de Visual Studio.