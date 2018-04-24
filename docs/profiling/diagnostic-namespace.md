---
title: diagnostic (espacio de nombres) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic
helpviewer_keywords:
- Concurrency::diagnostic namespace
ms.assetid: ad786b19-7c4c-46ee-bfb6-c4752b373a09
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 29164c08b03bd23980aad381a1a832b2857309a6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="diagnostic-namespace"></a>diagnostic (Espacio de nombres)
El espacio de nombres `diagnostics` proporciona funcionalidad para emitir los marcadores del visualizador de simultaneidad.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
namespace diagnostic;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="classes"></a>Clases  
  
|nombre|Description|  
|----------|-----------------|  
|[Clase marker_series](../profiling/marker-series-class.md)|Representa un canal de la serie de eventos generados por un único proveedor.|  
|[Clase span](../profiling/span-class.md)|Define una fase de la aplicación.|  
  
### <a name="enumerations"></a>Enumeraciones  
  
|nombre|Description|  
|----------|-----------------|  
|[Enumeración marker_importance](../profiling/marker-importance-enumeration.md)|Representa el nivel de importancia de un marcador del visualizador de simultaneidad.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** cvmarkersobj.h  
  
 **Espacio de nombres:** Concurrency  
  
## <a name="see-also"></a>Vea también  
 [Espacio de nombres de simultaneidad (visualizador de simultaneidad)](../profiling/concurrency-namespace-concurrency-visualizer.md)