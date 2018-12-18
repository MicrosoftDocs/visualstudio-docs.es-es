---
title: Directiva T4 CleanUpBehavior | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e5a211f-a3bf-4229-bff0-7d2e45b71c64
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: ee1882b6b63dbb2729070d32fcee7c1e58d280c5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49263408"
---
# <a name="t4-cleanupbehavior-directive"></a>T4 CleanUpBehavior (Directiva)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para eliminar el objeto appDomain después de procesar una plantilla de texto, incluya la línea siguiente:  
  
```  
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>  
```  
  
 Las plantillas de texto se procesan en un objeto appDomain que es independiente del proceso host. En la mayoría de los casos, cuando se ha procesado una plantilla de texto, el objeto appdomain se utiliza de nuevo para procesar la plantilla siguiente. Sin embargo, si especifica CleanupBehavior, el objeto appDomain se elimina y la plantilla siguiente se procesará en un nuevo objeto appDomain.  
  
 Esto reduce el procesamiento de texto, pero puede ser útil para garantizar que se desechan los recursos.  
  
 Esta directiva solo funciona en el host de Visual Studio.



