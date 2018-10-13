---
title: CvWriteAlert (función) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cvmarkers/CvWriteAlertVA
- cvmarkers/CvWriteAlertVW
- cvmarkers/CvWriteAlertA
- cvmarkers/CvWriteAlertW
helpviewer_keywords:
- CvWriteAlertVW method
- CvWriteAlertA method
- CvWriteAlertVA method
- CvWriteAlertW method
ms.assetid: 937aa9d6-278a-4df3-bef7-151441df16d5
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 773dc97f82f09ad1b5e1e2a91f59f1cc3b2bcba6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49244067"
---
# <a name="cvwritealert-function"></a>CvWriteAlert (Función)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Escribe una alerta en el archivo de seguimiento del visualizador de simultaneidad.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT CvWriteAlertW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCWSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteAlertA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteAlertVW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCWSTR pMessage,  
    _In_ va_list argList);  
  
HRESULT CvWriteAlertVA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCSTR pMessage,  
    _In_ va_list argList);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `argList`  
 Lista de argumentos.  
  
 `pMarkerSeries`  
 Contexto de la serie de marcador válido. No puede ser nulo.  
  
 `pMessage`  
 Cadena de formato de mensaje. No puede ser nulo.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK cuando el mensaje se ha escrito correctamente. Código de error en caso de que se hayan producido errores. Utilice macros SUCCEEDED/FAILED para comprobar si existe una condición de error.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** cvmarkers.h  
  
 **Unicode:** CvWriteAlertW, CvWriteAlertVW  
  
 **ANSI:** CvWriteAlertA, CvWriteAlertVA  
  
## <a name="see-also"></a>Vea también  
 [Referencia de la biblioteca C++](../profiling/cpp-library-reference.md)



