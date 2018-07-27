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
ms.openlocfilehash: 6541ddecceff6d9e7867dd5feead3457b2248b45
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844123"
---
# <a name="markerimportance-enumeration"></a>Enumeración marker_importance
Representa el nivel de importancia de un marcador del visualizador de simultaneidad.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum marker_importance;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="values"></a>Valores  
  
|nombre|Descripción|  
|----------|-----------------|  
|`critical_importance`|Especifica que el marcador tiene una importancia crítica.|  
|`high_importance`|Especifica que el marcador tiene una importancia alta.|  
|`low_importance`|Especifica que el marcador tiene una importancia baja.|  
|`normal_importance`|Especifica que el marcador tiene una importancia normal.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** *cvmarkersobj.h*  
  
 **Espacio de nombres:** Concurrency::diagnostic  
  
## <a name="see-also"></a>Vea también  
 [espacio de nombres de diagnóstico](../profiling/diagnostic-namespace.md)