---
title: Directiva T4 CleanUpBehavior | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 9e5a211f-a3bf-4229-bff0-7d2e45b71c64
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f964f37b347d588b1f7e590d918018c50e9f41c0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199833"
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
