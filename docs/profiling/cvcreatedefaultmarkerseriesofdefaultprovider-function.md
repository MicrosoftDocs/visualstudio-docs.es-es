---
title: "CvCreateDefaultMarkerSeriesOfDefaultProvider (Funci&#243;n) | Microsoft Docs"
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
  - "cvmarkers/CvCreateDefaultMarkerSeriesOfDefaultProvider"
helpviewer_keywords: 
  - "CvCreateDefaultMarkerSeriesOfDefaultProvider (método)"
ms.assetid: 24eb80f8-8fca-4c47-93b5-bb1eb8ffdffd
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CvCreateDefaultMarkerSeriesOfDefaultProvider (Funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Crea una serie predeterminada de marcadores para un proveedor predeterminado.  
  
## Sintaxis  
  
```  
HRESULT CvCreateDefaultMarkerSeriesOfDefaultProvider(  
   _Out_ PCV_PROVIDER* ppProvider,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### Parámetros  
 `ppProvider`  
 Dirección de la variable de objeto de proveedor.  La dirección no puede ser NULL, la variable puede tener cualquier valor.  
  
 `ppMarkerSeries`  
 Dirección de la variable del objeto de serie del marcador.  La dirección no puede ser NULL, la variable puede tener cualquier valor.  
  
## Valor devuelto  
 S\_OK cuando las ejecuciones del proveedor y el marcador se crean correctamente o un código de error en caso de que se presente alguno.  Utilizar macros SUCCEEDED\/FAILED para comprobar si hay condición de error.  
  
## Requisitos  
 **Encabezado:** cvmarkers.h  
  
## Vea también  
 [Referencia de la biblioteca C\+\+](../profiling/cpp-library-reference.md)