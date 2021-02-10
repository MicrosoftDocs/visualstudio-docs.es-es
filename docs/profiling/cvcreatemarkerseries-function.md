---
title: CvCreateMarkerSeries (función) | Microsoft Docs
description: Consulte la información de referencia de la función del SDK CvCreateMarkerSeries (biblioteca de C) del visualizador de simultaneidad.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvCreateMarkerSeriesA
- cvmarkers/CvCreateMarkerSeriesW
helpviewer_keywords:
- CvCreateMarkerSeriesA method
- CvCreateMarkerSeriesW method
ms.assetid: e280530b-137a-43a7-8643-aa514ab86ed7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8915724c39a656917d6565c60ddc7dfbb0737564
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941039"
---
# <a name="cvcreatemarkerseries-function"></a>Función CvCreateMarkerSeries
Crea series de marcadores para un proveedor determinado.

## <a name="syntax"></a>Sintaxis

```C
_Check_return_ HRESULT CvCreateMarkerSeriesW(
    _In_ PCV_PROVIDER  pProvider,
    _In_ LPCWSTR pSeriesName,
    _Out_ PCV_MARKERSERIES* ppMarkerSeries);

_Check_return_ HRESULT CvCreateMarkerSeriesA(
    _In_ PCV_PROVIDER  pProvider,
    _In_ LPCSTR pSeriesName,
    _Out_ PCV_MARKERSERIES* ppMarkerSeries);
```

#### <a name="parameters"></a>Parámetros
 `pProvider` Objeto de proveedor inicializado anteriormente por CvInitProvider. No puede ser NULL.

 `pSeriesName` Nombre de la serie de marcador. No puede ser nulo, pero se permite una cadena vacía.

 `ppMarkerSeries` Dirección de una variable de salida que almacenará el contexto de la serie de marcador. No puede ser NULL.

## <a name="return-value"></a>Valor devuelto
 S_OK cuando la serie de marcador se crea correctamente, o código de error en caso de que se hayan producido errores. Utilice macros SUCCEEDED/FAILED para comprobar si existe una condición de error.

## <a name="requirements"></a>Requisitos
 **Encabezado:** *cvmarkers.h*

 **Unicode:** CvCreateMarkerSeriesW

 **ANSI:** CvCreateMarkerSeriesA

## <a name="see-also"></a>Consulte también
- [Referencia de la biblioteca C++](../profiling/cpp-library-reference.md)