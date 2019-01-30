---
title: marker_importance (Enumeración) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_importance
helpviewer_keywords:
- Concurrency::diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3d4049a3792fcc529352baef3e4649c6157aa7f0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992157"
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
  
 **Espacio de nombres**: Concurrency::diagnostic  
  
## <a name="see-also"></a>Vea también  
 [espacio de nombres de diagnóstico](../profiling/diagnostic-namespace.md)