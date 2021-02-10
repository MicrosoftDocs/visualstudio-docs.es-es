---
title: CvCreateMarkerSeriesWithCodePageA (función) | Microsoft Docs
description: Consulte la información de referencia de la función del SDK CvCreateMarkerSeriesWithCodePageA (biblioteca de C) del visualizador de simultaneidad.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmakers/CvCreateMarkerSeriesWithCodePageA
helpviewer_keywords:
- CvCreateMarkerSeriesWithCodePageA method
ms.assetid: 3d7ed601-2222-4be9-a557-f217db008753
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 18e3367199154626703b671820d8d19d303630be
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941026"
---
# <a name="cvcreatemarkerserieswithcodepagea-function"></a>Función CvCreateMarkerSeriesWithCodePageA
Crea series de marcadores para un proveedor determinado y una página de códigos especificada. Esta función se puede utilizar para especificar la página de códigos explícitamente para el texto escrito por las funciones ANSI de API de marcador. Establecer la página de códigos puede ser útil en caso de que el seguimiento se capture y luego analice en distintos equipos con configuraciones regionales o idiomas diferentes. De forma predeterminada, se utiliza la página de códigos devuelta por la función GetACP().

## <a name="syntax"></a>Sintaxis

```C
HRESULT CvCreateMarkerSeriesWithCodePageA(
   _In_ PCV_PROVIDER pProvider,
   _In_ LPCSTR pSeriesName,
   _In_ UINT nTextCodePage,
   _Out_ PCV_MARKERSERIES* ppMarkerSeries
);
```

#### <a name="parameters"></a>Parámetros
 `pProvider` Objeto de proveedor inicializado anteriormente por CvInitProvider. No puede ser NULL.

 `pSeriesName` Nombre de la serie de marcador. No puede ser nulo, pero se permite una cadena vacía.

 `nTextCodePage` Página de códigos válida.

 `ppMarkerSeries` Dirección de una variable de salida que almacenará el contexto de la serie de marcador. No puede ser NULL.

## <a name="return-value"></a>Valor devuelto
 S_OK cuando la serie de marcador se crea correctamente, o código de error en caso de que se hayan producido errores. Utilice macros SUCCEEDED/FAILED para comprobar si existe una condición de error.

## <a name="requirements"></a>Requisitos
 **Encabezado:** *cvmarkers.h*

## <a name="see-also"></a>Consulte también
- [Referencia de la biblioteca C++](../profiling/cpp-library-reference.md)