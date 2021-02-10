---
title: CvCreateDefaultMarkerSeriesOfDefaultProvider (función) | Microsoft Docs
description: Consulte la información de referencia de la función del SDK CvCreateDefaultMarkerSeriesOfDefaultProvider (biblioteca de C) del visualizador de simultaneidad.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvCreateDefaultMarkerSeriesOfDefaultProvider
helpviewer_keywords:
- CvCreateDefaultMarkerSeriesOfDefaultProvider method
ms.assetid: 24eb80f8-8fca-4c47-93b5-bb1eb8ffdffd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 32d7730d36f7e99a2557e764c2adb92862515e24
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941052"
---
# <a name="cvcreatedefaultmarkerseriesofdefaultprovider-function"></a>Función CvCreateDefaultMarkerSeriesOfDefaultProvider
Crea la serie de marcadores predeterminados de un proveedor predeterminado.

## <a name="syntax"></a>Sintaxis

```C
HRESULT CvCreateDefaultMarkerSeriesOfDefaultProvider(
   _Out_ PCV_PROVIDER* ppProvider,
   _Out_ PCV_MARKERSERIES* ppMarkerSeries
);
```

#### <a name="parameters"></a>Parámetros
 `ppProvider` Dirección de la variable de objeto de proveedor. La dirección no puede ser NULL, pero la variable puede tener cualquier valor.

 `ppMarkerSeries` Dirección de la variable de objeto de serie de marcador. La dirección no puede ser NULL, pero la variable puede tener cualquier valor.

## <a name="return-value"></a>Valor devuelto
 S_OK cuando la serie de proveedor y marcador se crea correctamente, o código de error en caso de que se hayan producido errores. Utilice macros SUCCEEDED/FAILED para comprobar si existe una condición de error.

## <a name="requirements"></a>Requisitos
 **Encabezado:** *cvmarkers.h*

## <a name="see-also"></a>Consulte también
- [Referencia de la biblioteca C++](../profiling/cpp-library-reference.md)