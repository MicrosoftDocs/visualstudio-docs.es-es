---
title: marker_series::marker_series (Constructor) | Microsoft Docs
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
- cvmarkersobj/Concurrency::diagnostic::marker_series::marker_series
helpviewer_keywords:
- Concurrency::diagnostic::marker_series constructor
ms.assetid: 042c7d23-f1d8-4e09-9e76-a21c30243790
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2aafa01d18255e5ea36aed0451a0bb041b5db1f2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578620"
---
# <a name="markerseriesmarkerseries-constructor"></a>marker_series::marker_series (Constructor)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Constructor marker_series:: marker_series](https://docs.microsoft.com/visualstudio/profiling/marker-series-marker-series-constructor).  
  
Inicializa una nueva instancia de la clase `marker_series`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
marker_series();  
marker_series(  
   _In_ LPCTSTR _SeriesName  
);  
marker_series(  
   _In_ const GUID* _ProviderGuid  
);  
marker_series(  
   _In_ const GUID* _ProviderGuid,  
   _In_ LPCTSTR _SeriesName  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `_SeriesName`  
 Nombre de la serie que se va a crear.  
  
 `_ProviderGuid`  
 El GUID del proveedor de la serie.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** cvmarkersobj.h  
  
 **Espacio de nombres:** Concurrency::diagnostic  
  
## <a name="see-also"></a>Vea también  
 [Clase marker_series](../profiling/marker-series-class.md)



