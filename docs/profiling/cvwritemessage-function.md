---
title: CvWriteMessage (función) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvWriteMessageW
- cvmarkers/CvWriteMessageExW
- cvmarkers/CvWriteMessageVA
- cvmarkers/CvWriteMessageExVW
- cvmarkers/CvWriteMessageExA
- cvmarkers/CvWriteMessageA
- cvmarkers/CvWriteMessageExVA
- cvmarkers/CvWriteMessageVW
helpviewer_keywords:
- CvWriteMessageExVA method
- CvWriteMessageW method
- CvWriteMessageVW method
- CvWriteMessageExVW method
- CvWriteMessageExW method
- CvWriteMessageA method
- CvWriteMessageVA method
- CvWriteMessageExA method
ms.assetid: e20ae7be-bfa7-437a-b8c1-fa0f1baa7f83
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 966be7ab50c2e14ae43da7cf68d7ef6168255207
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34749631"
---
# <a name="cvwritemessage-function"></a>Función CvWriteMessage
Escribe un mensaje en el archivo de seguimiento del visualizador de simultaneidad.  
  
## <a name="syntax"></a>Sintaxis  
  
```C  
HRESULT CvWriteMessageW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCWSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteMessageA(  
    PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteMessageVW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCWSTR pMessage,  
    _In_ va_list argList);  
  
HRESULT CvWriteMessageVA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCSTR pMessage,  
    _In_ va_list argList);  
  
HRESULT CvWriteMessageExW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCWSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteMessageExA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteMessageExVW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCWSTR pMessage,  
    _In_ va_list argList);  
  
HRESULT CvWriteMessageExVA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCSTR pMessage,  
    _In_ va_list argList);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `argList`  
 Lista de argumentos.  
  
 `category`  
 Categoría del intervalo  
  
 `level`  
 Nivel de importancia del intervalo.  
  
 `pMarkerSeries`  
 Contexto de la serie de marcador válido. No puede ser nulo.  
  
 `pMessage`  
 Cadena de formato de mensaje. No puede ser nulo.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK cuando el mensaje se ha escrito correctamente. Código de error en caso de que se hayan producido errores. Utilice macros SUCCEEDED/FAILED para comprobar si existe una condición de error.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** *cvmarkers.h*  
  
 **Unicode:** CvWriteMessageW, CvWriteMessageVW, CvWriteMessageExW, CvWriteMessageExVW  
  
 **ANSI:** CvWriteMessageA, CvWriteMessageVA, CvWriteMessageExA, CvWriteMessageExVA  
  
## <a name="see-also"></a>Vea también  
 [Referencia de la biblioteca C++](../profiling/cpp-library-reference.md)