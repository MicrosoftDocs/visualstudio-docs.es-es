---
title: "marker_importance (Enumeraci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkersobj/Concurrency::diagnostic::marker_importance"
helpviewer_keywords: 
  - "Concurrency::diagnostic::marker_importance (enumeración)"
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# marker_importance (Enumeraci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Representa el nivel de importancia de un marcador del visualizador de simultaneidad.  
  
## Sintaxis  
  
```  
enum marker_importance;  
```  
  
## Miembros  
  
### Valores  
  
|Name|Descripción|  
|----------|-----------------|  
|`critical_importance`|Especifica que el marcador tiene una importancia crítica.|  
|`high_importance`|Especifica que el marcador tiene una importancia elevada.|  
|`low_importance`|Especifica que el marcador tiene poca importancia.|  
|`normal_importance`|Especifica que el marcador tiene una importancia normal.|  
  
## Requisitos  
 **Encabezado:** cvmarkersobj.h  
  
 **Espacio de nombres:** Concurrency::diagnostico  
  
## Vea también  
 [diagnostic \(Espacio de nombres\)](../profiling/diagnostic-namespace.md)