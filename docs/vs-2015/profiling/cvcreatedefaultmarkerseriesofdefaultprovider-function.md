---
title: CvCreateDefaultMarkerSeriesOfDefaultProvider (función) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmarkers/CvCreateDefaultMarkerSeriesOfDefaultProvider
helpviewer_keywords:
- CvCreateDefaultMarkerSeriesOfDefaultProvider method
ms.assetid: 24eb80f8-8fca-4c47-93b5-bb1eb8ffdffd
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fb0ab16dcd7e42a496317f4e7589bafdbdaf83dc
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54770900"
---
# <a name="cvcreatedefaultmarkerseriesofdefaultprovider-function"></a>CvCreateDefaultMarkerSeriesOfDefaultProvider (Función)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Crea la serie de marcadores predeterminados de un proveedor predeterminado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
