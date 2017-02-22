---
title: "CvWriteAlert (Funci&#243;n) | Microsoft Docs"
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
  - "cvmarkers/CvWriteAlertVA"
  - "cvmarkers/CvWriteAlertVW"
  - "cvmarkers/CvWriteAlertA"
  - "cvmarkers/CvWriteAlertW"
helpviewer_keywords: 
  - "CvWriteAlertVW (método)"
  - "CvWriteAlertA (método)"
  - "CvWriteAlertVA (método)"
  - "CvWriteAlertW (método)"
ms.assetid: 937aa9d6-278a-4df3-bef7-151441df16d5
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CvWriteAlert (Funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Escribe una alerta en el archivo de seguimiento del Visualizador de simultaneidad.  
  
## Sintaxis  
  
```  
HRESULT CvWriteAlertW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCWSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteAlertA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteAlertVW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCWSTR pMessage,  
    _In_ va_list argList);  
  
HRESULT CvWriteAlertVA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCSTR pMessage,  
    _In_ va_list argList);  
```  
  
#### Parámetros  
 `argList`  
 Lista de argumentos.  
  
 `pMarkerSeries`  
 Contexto válido de las series de marcador.  No puede ser NULL.  
  
 `pMessage`  
 Cadena de formato de mensaje.  No puede ser NULL.  
  
## Valor devuelto  
 S\_OK cuando el mensaje se escribe correctamente.  Código de error en caso de que hubiera cualquier error.  Utilizar macros SUCCEEDED\/FAILED para comprobar si hay condición de error.  
  
## Requisitos  
 **Encabezado:** cvmarkers.h  
  
 **Unicode:** CvWriteAlertW, CvWriteAlertVW  
  
 **ANSI:** CvWriteAlertA, CvWriteAlertVA  
  
## Vea también  
 [Referencia de la biblioteca C\+\+](../profiling/cpp-library-reference.md)