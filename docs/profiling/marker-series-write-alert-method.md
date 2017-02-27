---
title: "marker_series::write_alert (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkersobj/Concurrency::diagnostic:marker_series::write_alert"
helpviewer_keywords: 
  - "Concurrency::diagnostic:marker_series::write_alert (método)"
ms.assetid: 9d5465c7-f862-47a7-b249-4116605075a6
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# marker_series::write_alert (M&#233;todo)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Escribe una alerta en el archivo de seguimiento del Visualizador de simultaneidad.  
  
## Sintaxis  
  
```  
void write_alert(  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### Parámetros  
 `_Format`  
 Una cadena de formato compuesto que contiene el texto mezclado con cero o más elementos de formato, que se corresponden con los objetos de la lista de argumentos.  
  
## Requisitos  
 **Encabezado:** cvmarkersobj.h  
  
 **Espacio de nombres:** Concurrency::diagnostico  
  
## Vea también  
 [marker\_series \(Clase\)](../profiling/marker-series-class.md)