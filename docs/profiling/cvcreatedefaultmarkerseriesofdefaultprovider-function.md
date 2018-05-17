---
title: CvCreateDefaultMarkerSeriesOfDefaultProvider (función) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvCreateDefaultMarkerSeriesOfDefaultProvider
helpviewer_keywords:
- CvCreateDefaultMarkerSeriesOfDefaultProvider method
ms.assetid: 24eb80f8-8fca-4c47-93b5-bb1eb8ffdffd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6198cfc874eb8a547b77bfabe8b3fb3473fa92ef
ms.sourcegitcommit: eefffa7ebe339d1297cdc12f51a813e7849d7e95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/14/2018
---
# <a name="cvcreatedefaultmarkerseriesofdefaultprovider-function"></a>CvCreateDefaultMarkerSeriesOfDefaultProvider (Función)
Crea la serie de marcadores predeterminados de un proveedor predeterminado.  
  
## <a name="syntax"></a>Sintaxis  
  
```C  
HRESULT CvCreateDefaultMarkerSeriesOfDefaultProvider(  
   _Out_ PCV_PROVIDER* ppProvider,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppProvider`  
 Dirección de la variable de objeto de proveedor. La dirección no puede ser NULL, pero la variable puede tener cualquier valor.  
  
 `ppMarkerSeries`  
 Dirección de la variable de objeto de serie de marcador. La dirección no puede ser NULL, pero la variable puede tener cualquier valor.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK cuando la serie de proveedor y marcador se crea correctamente, o código de error en caso de que se hayan producido errores. Utilice macros SUCCEEDED/FAILED para comprobar si existe una condición de error.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** cvmarkers.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia de la biblioteca C++](../profiling/cpp-library-reference.md)