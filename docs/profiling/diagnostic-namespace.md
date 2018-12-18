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
ms.openlocfilehash: d781bbfefa59b2e124cf76c11b8fd7c06cc66dda
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764675"
---
# <a name="diagnostic-namespace"></a>diagnostic (Espacio de nombres)
El espacio de nombres `diagnostics` proporciona funcionalidad para emitir los marcadores del visualizador de simultaneidad.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
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
 **Encabezado:** *cvmarkersobj.h*  
  
 **Espacio de nombres:** Concurrency  
  
## <a name="see-also"></a>Vea también  
 [Espacio de nombres de simultaneidad (Visualizador de simultaneidad)](../profiling/concurrency-namespace-concurrency-visualizer.md)