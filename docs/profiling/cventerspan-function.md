---
title: CvEnterSpan (Función) | Microsoft Docs
description: Consulte la información de referencia de la función del SDK CvEnterSpan del visualizador de simultaneidad (biblioteca de C).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvEnterSpanVA
- cvmarkers/CvEnterSpanW
- cvmarkers/CvEnterSpanExW
- cvmarkers/CvEnterSpanA
- cvmarkers/CvEnterSpanExVW
- cvmarkers/CvEnterSpanExA
- cvmarkers/CvEnterSpanVW
helpviewer_keywords:
- CvEnterSpanVW method
- CvEnterSpanVA method
- CvEnterSpanExA method
- CvEnterSpanW method
- CvEnterSpanA method
- CvEnterSpanExVW method
- CvEnterSpanExW method
ms.assetid: 91689e9c-6733-44b9-b36a-8b9b2eef7d1d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 345ed3c73f5d79a549ac24e5eb3137f83101cdda
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912494"
---
# <a name="cventerspan-function"></a>Función CvEnterSpan
Marca el principio de un nuevo intervalo.

## <a name="syntax"></a>Sintaxis

```C
HRESULT CvEnterSpanW(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _Out_ PCV_SPAN* ppSpan,
    _In_ PCWSTR pMessage,
    ...
    );

HRESULT CvEnterSpanA(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _Out_ PCV_SPAN* ppSpan,
    _In_ PCSTR pMessage,
    ...
    );

HRESULT CvEnterSpanVW(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _Out_ PCV_SPAN* ppSpan,
    _In_ PCWSTR pMessage,
    _In_ va_list argList
    );

HRESULT CvEnterSpanVA(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _Out_ PCV_SPAN* ppSpan,
    _In_ PCSTR pMessage,
    _In_ va_list argList
    );

HRESULT CvEnterSpanExW(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ CV_IMPORTANCE level,
    _In_ int category,
    _Out_ PCV_SPAN* ppSpan,
    _In_ PCWSTR pMessage,
    ...
    );

HRESULT CvEnterSpanExA(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ CV_IMPORTANCE level,
    _In_ int category,
    _Out_ PCV_SPAN* ppSpan,
    _In_ PCSTR pMessage,
    ...
    );

HRESULT CvEnterSpanExVW(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ CV_IMPORTANCE level,
    _In_ int category,
    _Out_ PCV_SPAN* ppSpan,
    _In_ PCWSTR pMessage,
    _In_ va_list argList);

HRESULT CvEnterSpanExVA(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ CV_IMPORTANCE level,
    _In_ int category,
    _Out_ PCV_SPAN* ppSpan,
    _In_ PCSTR pMessage,
    _In_ va_list argList);

```

#### <a name="parameters"></a>Parámetros
 `argList` Lista de argumentos.

 `category` Categoría del intervalo.

 `level` Nivel de importancia del intervalo.

 `pMarkerSeries` Contexto de la serie de marcador válido. No puede ser NULL.

 `pMessage` Cadena de formato de mensaje. No puede ser NULL.

 `ppSpan` Dirección de la variable que contendrá el objeto de intervalo resultante. La dirección no puede ser NULL, pero la variable puede tener cualquier valor.

## <a name="return-value"></a>Valor devuelto
 S_OK cuando el mensaje se ha escrito correctamente. Código de error en caso de que se hayan producido errores. Utilice macros SUCCEEDED/FAILED para comprobar si existe una condición de error.

## <a name="requirements"></a>Requisitos
 **Encabezado:** *cvmarkers.h*

 **Unicode:** CvEnterSpanW, CvEnterSpanVW, CvEnterSpanExW, CvEnterSpanExVW

 **ANSI:** CvEnterSpanA, CvEnterSpanVA, CvEnterSpanExA, CvEnterSpanExVW

## <a name="see-also"></a>Consulte también
- [Referencia de la biblioteca C++](../profiling/cpp-library-reference.md)