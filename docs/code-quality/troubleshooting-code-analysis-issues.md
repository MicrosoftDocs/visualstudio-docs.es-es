---
title: "Solucionar problemas de an&#225;lisis de c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
caps.latest.revision: 5
caps.handback.revision: 5
author: "erickson-doug"
ms.author: "douge"
manager: "douge"
---
# Solucionar problemas de an&#225;lisis de c&#243;digo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tema contiene información sobre solución de problemas para los siguientes problemas de análisis de código de Visual Studio.  
  
-   [Los cambios en un conjunto de reglas de Visual Studio 2010 no se reflejan en versiones anteriores de Visual Studio](#ChildRuleSetChangesInPreviousVersions)  
  
##  <a name="ChildRuleSetChangesInPreviousVersions"></a> Los cambios en un conjunto de reglas de Visual Studio 2010 no se reflejan en versiones anteriores de Visual Studio  
 Cuando crea un conjunto de reglas que contiene un conjunto de reglas secundario en [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)], es posible que un cambio en el conjunto de reglas secundario no se aplique en las ejecuciones de análisis de código en aquellos equipos que utilizan una versión anterior de Visual Studio.  Para solucionar este problema, debe forzar una reescritura del conjunto de reglas primario, que es el conjunto de reglas que contiene el conjunto de reglas secundario.  
  
1.  Abra el conjunto de reglas primario en [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)].  
  
2.  Realice un cambio, como agregar o quitar una regla y, a continuación, guarde el conjunto de reglas.  
  
3.  Vuelva a abrir el conjunto de reglas, invierta el cambio y, a continuación, guarde el conjunto de reglas de nuevo.  
  
## Vea también  
 [Analizar la calidad de la aplicación](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)   
 [Analizar la calidad del código administrado](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Utilizar conjuntos de reglas para agrupar reglas de análisis de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)