---
title: "marker_series (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkersobj/Concurrency::diagnostic::marker_series"
helpviewer_keywords: 
  - "Concurrency::diagnostic::marker_series (clase)"
ms.assetid: b8445ed0-c512-4f92-b6b4-3d05c044f939
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# marker_series (Clase)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Representa un canal de serie de los eventos generados por un solo proveedor.  
  
## Sintaxis  
  
```  
class marker_series;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[marker\_series::marker\_series \(Constructor\)](../Topic/marker_series::marker_series%20Constructor.md)|Inicializa una nueva instancia de la clase `marker_series`.|  
|[marker\_series::~marker\_series \(Destructor\)](../profiling/marker-series-tilde-marker-series-destructor.md)|Destruye el objeto marker\_series y libera todos los recursos asignados.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[marker\_series::is\_enabled \(Método\)](../Topic/marker_series::is_enabled%20Method.md)|Determina si una sesión ha habilitado el proveedor.|  
|[marker\_series::write\_alert \(Método\)](../profiling/marker-series-write-alert-method.md)|Escribe una alerta en el archivo de seguimiento del Visualizador de simultaneidad.|  
|[marker\_series::write\_flag \(Método\)](../profiling/marker-series-write-flag-method.md)|Escribe una marca en el archivo de seguimiento del Visualizador de simultaneidad.|  
|[marker\_series::write\_message \(Método\)](../profiling/marker-series-write-message-method.md)|Escribe un mensaje en el archivo de seguimiento del Visualizador de simultaneidad.|  
  
## Jerarquía de herencia  
 `marker_series`  
  
## Requisitos  
 **Encabezado:** cvmarkersobj.h  
  
 **Espacio de nombres:** Concurrency::diagnostico  
  
## Vea también  
 [diagnostic \(Espacio de nombres\)](../profiling/diagnostic-namespace.md)