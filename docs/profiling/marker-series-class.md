---
title: marker_series (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cvmarkersobj/Concurrency::diagnostic::marker_series
helpviewer_keywords: Concurrency::diagnostic::marker_series class
ms.assetid: b8445ed0-c512-4f92-b6b4-3d05c044f939
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b326e88e18e3a7c5515cc11bfda7e5c35ae4a063
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="markerseries-class"></a>marker_series (Clase)
Representa un canal en serie de eventos generados por un único proveedor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class marker_series;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[marker_series::marker_series (Constructor)](../profiling/marker-series-marker-series-constructor.md)|Inicializa una nueva instancia de la clase `marker_series`.|  
|[marker_series::~marker_series (Destructor)](../profiling/marker-series-tilde-marker-series-destructor.md)|Destruye el objeto marker_series y libera todos los recursos asignados.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[marker_series::is_enabled (Método)](../profiling/marker-series-is-enabled-method.md)|Determina si alguna sesión habilitó el proveedor.|  
|[marker_series::write_alert (Método)](../profiling/marker-series-write-alert-method.md)|Escribe una alerta en el archivo de seguimiento del visualizador de simultaneidad.|  
|[marker_series::write_flag (Método)](../profiling/marker-series-write-flag-method.md)|Escribe una marca en el archivo de seguimiento del visualizador de simultaneidad.|  
|[marker_series::write_message (Método)](../profiling/marker-series-write-message-method.md)|Escribe un mensaje en el archivo de seguimiento del visualizador de simultaneidad.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `marker_series`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** cvmarkersobj.h  
  
 **Espacio de nombres:** Concurrency::diagnostic  
  
## <a name="see-also"></a>Vea también  
 [diagnostic (Espacio de nombres)](../profiling/diagnostic-namespace.md)