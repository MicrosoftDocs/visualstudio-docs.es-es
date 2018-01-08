---
title: T4 CleanUpBehavior (directiva) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e5a211f-a3bf-4229-bff0-7d2e45b71c64
caps.latest.revision: "2"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 8b56d7be76e9cf43434f2f7d4c5fc2fa9a3222b9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="t4-cleanupbehavior-directive"></a>T4 CleanUpBehavior (Directiva)
Para eliminar el objeto appDomain después de procesar una plantilla de texto, incluya la línea siguiente:  
  
```  
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>  
```  
  
 Las plantillas de texto se procesan en un objeto appDomain que es independiente del proceso host. En la mayoría de los casos, cuando se ha procesado una plantilla de texto, el objeto appdomain se utiliza de nuevo para procesar la plantilla siguiente. Sin embargo, si especifica CleanupBehavior, el objeto appDomain se elimina y la plantilla siguiente se procesará en un nuevo objeto appDomain.  
  
 Esto reduce el procesamiento de texto, pero puede ser útil para garantizar que se desechan los recursos.  
  
 Esta directiva solo funciona en el host de Visual Studio.