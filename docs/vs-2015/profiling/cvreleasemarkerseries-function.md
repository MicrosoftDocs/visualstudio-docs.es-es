---
title: CvReleaseMarkerSeries (función) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmarkers/CvReleaseMarkerSeries
helpviewer_keywords:
- CvReleaseMarkerSeries method
ms.assetid: 3b4711ee-e534-411d-9128-f69cd7932a48
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6bfa9952a834110ef0fea36568ea210b637547aa
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54794140"
---
# <a name="cvreleasemarkerseries-function"></a>CvReleaseMarkerSeries (Función)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Libera la serie de marcadores. No utilice el objeto de la serie de marcadores después de liberar la aplicación; de lo contrario, la aplicación podría bloquearse. Si no se puede liberar la serie de marcadores, se produce una pérdida de memoria.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT CvReleaseMarkerSeries(  
   _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pMarkerSeries`  
 Dirección de la variable de objeto de proveedor. La dirección no puede ser NULL, pero la variable puede tener cualquier valor.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK cuando la serie de marcador se libera correctamente, o código de error en caso de que se hayan producido errores. Utilice macros SUCCEEDED/FAILED para comprobar si existe una condición de error.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** cvmarkers.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia de la biblioteca C++](../profiling/cpp-library-reference.md)
