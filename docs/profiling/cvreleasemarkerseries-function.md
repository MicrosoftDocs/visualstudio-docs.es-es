---
title: "CvReleaseMarkerSeries (Funci&#243;n) | Microsoft Docs"
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
  - "cvmarkers/CvReleaseMarkerSeries"
helpviewer_keywords: 
  - "CvReleaseMarkerSeries (método)"
ms.assetid: 3b4711ee-e534-411d-9128-f69cd7932a48
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CvReleaseMarkerSeries (Funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Libera la serie del marcador.  No utilice el objeto de serie de marcador de la ejecución después de liberarlo, de otra forma, la aplicación podría bloquearse.  Un error al liberar la serie del marcador provoca una pérdida de memoria.  
  
## Sintaxis  
  
```  
HRESULT CvReleaseMarkerSeries(  
   _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries  
);  
```  
  
#### Parámetros  
 `pMarkerSeries`  
 Dirección de la variable de objeto de proveedor.  La dirección no puede ser NULL, la variable puede tener cualquier valor.  
  
## Valor devuelto  
 S\_OK cuando la ejecución del marcador se libera correctamente o lanza código de error en caso de que hubiera cualquier error.  Utilizar macros SUCCEEDED\/FAILED para comprobar si hay condición de error.  
  
## Requisitos  
 **Encabezado:** cvmarkers.h  
  
## Vea también  
 [Referencia de la biblioteca C\+\+](../profiling/cpp-library-reference.md)