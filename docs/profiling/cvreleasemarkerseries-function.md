---
title: CvReleaseMarkerSeries (función) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvReleaseMarkerSeries
helpviewer_keywords:
- CvReleaseMarkerSeries method
ms.assetid: 3b4711ee-e534-411d-9128-f69cd7932a48
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 84db5dac77fbbc51c9f1c0e24173dcc8ca1d68c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85332190"
---
# <a name="cvreleasemarkerseries-function"></a>Función CvReleaseMarkerSeries
Libera la serie de marcadores. No utilice el objeto de la serie de marcadores después de liberar la aplicación; de lo contrario, la aplicación podría bloquearse. Si no se puede liberar la serie de marcadores, se produce una pérdida de memoria.

## <a name="syntax"></a>Sintaxis

```C
HRESULT CvReleaseMarkerSeries(
   _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries
);
```

#### <a name="parameters"></a>Parámetros
 `pMarkerSeries` Dirección de la variable de objeto de proveedor. La dirección no puede ser NULL, pero la variable puede tener cualquier valor.

## <a name="return-value"></a>Valor devuelto
 S_OK cuando la serie de marcador se libera correctamente, o código de error en caso de que se hayan producido errores. Utilice macros SUCCEEDED/FAILED para comprobar si existe una condición de error.

## <a name="requirements"></a>Requisitos
 **Encabezado:** *cvmarkers.h*

## <a name="see-also"></a>Vea también
- [Referencia de la biblioteca C++](../profiling/cpp-library-reference.md)