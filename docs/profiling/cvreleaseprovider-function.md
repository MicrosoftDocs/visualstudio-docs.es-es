---
title: "CvReleaseProvider (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvReleaseProvider"
helpviewer_keywords: 
  - "CvReleaseProvider (método)"
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# CvReleaseProvider (Funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Libera el proveedor del marcador.  Liberar el proveedor de marcador no afectará a la ejecución del marcador creado con anterioridad en este proveedor.  Las ejecuciones de marcador tienen que liberarse por separado por la llamada a CvReleaseMarkerSeries.  Un error al liberar el proveedor causa una pérdida de memoria.  
  
## Sintaxis  
  
```  
HRESULT CvReleaseProvider(  
   _In_ PCV_PROVIDER pProvider  
);  
```  
  
#### Parámetros  
 `pProvider`  
 Contexto del proveedor  No puede ser NULL.  
  
## Valor devuelto  
 S\_OK cuando el proveedor se libera correctamente o un código de error en caso de que hubiera cualquier error.  Utilizar macros SUCCEEDED\/FAILED para comprobar si hay condición de error.  
  
## Requisitos  
 **Encabezado:** cvmarkers.h  
  
## Vea también  
 [Referencia de la biblioteca C\+\+](../profiling/cpp-library-reference.md)