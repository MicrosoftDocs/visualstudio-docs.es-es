---
title: CvCreateDefaultMarkerSeriesOfDefaultProvider (función) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cvmarkers/CvCreateDefaultMarkerSeriesOfDefaultProvider
helpviewer_keywords:
- CvCreateDefaultMarkerSeriesOfDefaultProvider method
ms.assetid: 24eb80f8-8fca-4c47-93b5-bb1eb8ffdffd
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4910a66481be1f00a0fd57e1a66c0756f11c6589
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47576262"
---
# <a name="cvcreatedefaultmarkerseriesofdefaultprovider-function"></a>CvCreateDefaultMarkerSeriesOfDefaultProvider (Función)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [CvCreateDefaultMarkerSeriesOfDefaultProvider (función)](https://docs.microsoft.com/visualstudio/profiling/cvcreatedefaultmarkerseriesofdefaultprovider-function).  
  
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



