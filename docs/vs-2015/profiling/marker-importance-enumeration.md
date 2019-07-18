---
title: marker_importance (Enumeración) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_importance
helpviewer_keywords:
- Concurrency::diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a4451a7b222b66f0fe5bea2b0e5f2b8499c9033c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68198381"
---
# <a name="markerimportance-enumeration"></a>marker_importance (Enumeración)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Representa el nivel de importancia de un marcador del visualizador de simultaneidad.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
enum marker_importance;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="values"></a>Valores  
  
|nombre|DESCRIPCIÓN|  
|----------|-----------------|  
|`critical_importance`|Especifica que el marcador tiene una importancia crítica.|  
|`high_importance`|Especifica que el marcador tiene una importancia alta.|  
|`low_importance`|Especifica que el marcador tiene una importancia baja.|  
|`normal_importance`|Especifica que el marcador tiene una importancia normal.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** cvmarkersobj.h  
  
 **Espacio de nombres:** Concurrency::diagnostic  
  
## <a name="see-also"></a>Otras referencias  
 [diagnostic (Espacio de nombres)](../profiling/diagnostic-namespace.md)
