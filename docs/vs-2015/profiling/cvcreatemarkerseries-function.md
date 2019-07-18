---
title: CvCreateMarkerSeries (función) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmarkers/CvCreateMarkerSeriesA
- cvmarkers/CvCreateMarkerSeriesW
helpviewer_keywords:
- CvCreateMarkerSeriesA method
- CvCreateMarkerSeriesW method
ms.assetid: e280530b-137a-43a7-8643-aa514ab86ed7
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6dc4af6ef3b2ffc89ec0e69a6dd63923f5c55ffe
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68155541"
---
# <a name="cvcreatemarkerseries-function"></a>CvCreateMarkerSeries (Función)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Crea series de marcadores para un proveedor determinado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
 `pProvider`  
 Objeto de proveedor inicializado anteriormente por CvInitProvider. No puede ser nulo.  
  
 `pSeriesName`  
 Nombre de la serie de marcador. No puede ser nulo, pero se permite una cadena vacía.  
  
 `ppMarkerSeries`  
 Dirección de una variable de salida que almacenará el contexto de la serie de marcador. No puede ser nulo.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK cuando la serie de marcador se crea correctamente, o código de error en caso de que se hayan producido errores. Utilice macros SUCCEEDED/FAILED para comprobar si existe una condición de error.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** cvmarkers.h  
  
 **Unicode:** CvCreateMarkerSeriesW  
  
 **ANSI:** CvCreateMarkerSeriesA  
  
## <a name="see-also"></a>Otras referencias  
 [Referencia de la biblioteca C++](../profiling/cpp-library-reference.md)
