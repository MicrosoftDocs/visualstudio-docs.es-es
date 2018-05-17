---
title: marker_importance (Enumeración) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_importance
helpviewer_keywords:
- Concurrency::diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9f4c87cfa1504c997cefdc68416dac9923fa10b4
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/11/2018
---
# <a name="markerimportance-enumeration"></a>marker_importance (Enumeración)
Representa el nivel de importancia de un marcador del visualizador de simultaneidad.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum marker_importance;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="values"></a>Valores  
  
|nombre|Description|  
|----------|-----------------|  
|`critical_importance`|Especifica que el marcador tiene una importancia crítica.|  
|`high_importance`|Especifica que el marcador tiene una importancia alta.|  
|`low_importance`|Especifica que el marcador tiene una importancia baja.|  
|`normal_importance`|Especifica que el marcador tiene una importancia normal.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** cvmarkersobj.h  
  
 **Espacio de nombres:** Concurrency::diagnostic  
  
## <a name="see-also"></a>Vea también  
 [diagnostic (Espacio de nombres)](../profiling/diagnostic-namespace.md)