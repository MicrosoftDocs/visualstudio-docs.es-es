---
title: Solucionar problemas de análisis de código | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
caps.latest.revision: 7
author: erickson-doug
ms.author: gewarren
manager: douge
ms.openlocfilehash: b8d17fcaec0034d2803f769cc5595416f5d56de8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573980"
---
# <a name="troubleshooting-code-analysis-issues"></a>Solucionar problemas de análisis de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [solución de problemas de análisis de código](https://docs.microsoft.com/visualstudio/code-quality/troubleshooting-code-analysis-issues).  
  
Este tema contiene información para solucionar los siguientes problemas de análisis de código de Visual Studio.  
  
-   [Los cambios en un conjunto de reglas de Visual Studio 2010 no se reflejan en las versiones anteriores de Visual Studio](#ChildRuleSetChangesInPreviousVersions)  
  
##  <a name="ChildRuleSetChangesInPreviousVersions"></a> Los cambios en un conjunto de reglas de Visual Studio 2010 no se reflejan en las versiones anteriores de Visual Studio  
 Cuando se crea un conjunto de reglas en [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] que contiene un conjunto de reglas secundario, es posible que no se pueda aplicar un cambio en dicho conjunto de reglas secundario en ejecuciones de análisis de código desde equipos que utilizan una versión anterior de Visual Studio. Para resolver este problema, debe forzar una reescritura del conjunto de reglas primario, que es el conjunto de reglas que contiene el conjunto de reglas secundario.  
  
1.  Abra el conjunto de reglas primario establecido en [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].  
  
2.  Realice un cambio, como agregar o eliminar una regla y, después, guarde el conjunto de reglas.  
  
3.  Vuelva a abrir el conjunto de reglas, invierta el cambio y guarde de nuevo el conjunto de reglas.  
  
## <a name="see-also"></a>Vea también  
 [Analizar la calidad de la aplicación](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)   
 [Analizar la calidad del código administrado](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Usar conjuntos de reglas para agrupar reglas de análisis de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)



