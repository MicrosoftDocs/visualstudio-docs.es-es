---
title: "Solucionar problemas de análisis de código | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6e552570eb48b9210b366ebbfe157fe656ab3fe0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="troubleshooting-code-analysis-issues"></a>Solucionar problemas de análisis de código
Este tema contiene información para solucionar problemas de los siguientes problemas de análisis de código de Visual Studio.  
  
-   [Cambios en un Visual Studio 2010 regla conjunto no se reflejan en las versiones anteriores de Visual Studio](#ChildRuleSetChangesInPreviousVersions)  
  
##  <a name="ChildRuleSetChangesInPreviousVersions"></a>Cambios en un Visual Studio 2010 regla conjunto no se reflejan en las versiones anteriores de Visual Studio  
 Cuando se crea un conjunto de reglas en [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] que contiene un conjunto de reglas secundarios, un cambio en el conjunto de reglas secundarios podría no aplicarse en series de análisis de código en equipos que usan una versión anterior de Visual Studio. Para resolver este problema, debe forzar una reescritura del conjunto de reglas primario, que es el conjunto de reglas que contiene el conjunto de reglas secundarios.  
  
1.  Abra la regla de elemento primario establecida en [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)].  
  
2.  Realiza un cambio, como agregar o quitar una regla y, a continuación, guarde el conjunto de reglas.  
  
3.  Vuelva a abrir el conjunto de reglas, revertir el cambio y, a continuación, guarde el nuevo conjunto de reglas.  
  
## <a name="see-also"></a>Vea también  
 [Analizar la calidad de la aplicación](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)   
 [Analizar la calidad del código administrado](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Usar conjuntos de reglas para agrupar reglas de análisis de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)