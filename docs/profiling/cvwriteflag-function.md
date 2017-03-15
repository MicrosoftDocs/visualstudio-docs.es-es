---
title: "CvWriteFlag (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvWriteFlagExVA"
  - "cvmarkers/CvWriteFlagExW"
  - "cvmarkers/CvWriteFlagExVW"
  - "cvmarkers/CvWriteFlagExA"
helpviewer_keywords: 
  - "CvWriteFlagExW (método)"
  - "CvWriteFlagExVA (método)"
  - "CvWriteFlagExA (método)"
  - "CvWriteFlagExVW (método)"
ms.assetid: ee9da1e2-7b34-4cba-81e2-215d25d32e4d
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# CvWriteFlag (Funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Escribe una marca en el archivo de seguimiento del Visualizador de simultaneidad.  
  
## Sintaxis  
  
```  
HRESULT CvWriteFlagExW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCWSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteFlagExA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteFlagExVW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCWSTR pMessage,  
    _In_ va_list argList);  
  
HRESULT CvWriteFlagExVA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCSTR pMessage,  
    _In_ va_list argList);  
```  
  
#### Parámetros  
 `argList`  
 Lista de argumentos.  
  
 `category`  
 Categoría.  
  
 `level`  
 Nivel de importancia.  
  
 `pMarkerSeries`  
 Contexto válido de las series de marcador.  No puede ser NULL.  
  
 `pMessage`  
 Cadena de formato de mensaje.  No puede ser NULL.  
  
## Valor devuelto  
 S\_OK cuando el mensaje se escribe correctamente.  Código de error en caso de que hubiera cualquier error.  Utilizar macros SUCCEEDED\/FAILED para comprobar si hay condición de error.  
  
## Requisitos  
 **Encabezado:** cvmarkers.h  
  
 **Unicode:** CvWriteFlagExW, CvWriteFlagExVW  
  
 **ANSI:**CvWriteFlagExA, CvWriteFlagExVA  
  
## Vea también  
 [Referencia de la biblioteca C\+\+](../profiling/cpp-library-reference.md)