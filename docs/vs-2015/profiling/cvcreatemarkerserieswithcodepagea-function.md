---
title: CvCreateMarkerSeriesWithCodePageA (función) | Microsoft Docs
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
- cvmakers/CvCreateMarkerSeriesWithCodePageA
helpviewer_keywords:
- CvCreateMarkerSeriesWithCodePageA method
ms.assetid: 3d7ed601-2222-4be9-a557-f217db008753
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3716cb41da056590a7978e49f4672d25b1bbdaae
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577363"
---
# <a name="cvcreatemarkerserieswithcodepagea-function"></a>CvCreateMarkerSeriesWithCodePageA (Función)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [CvCreateMarkerSeriesWithCodePageA (función)](https://docs.microsoft.com/visualstudio/profiling/cvcreatemarkerserieswithcodepagea-function).  
  
Crea series de marcadores para un proveedor determinado y una página de códigos especificada. Esta función se puede utilizar para especificar la página de códigos explícitamente para el texto escrito por las funciones ANSI de API de marcador. Establecer la página de códigos puede ser útil en caso de que el seguimiento se capture y luego analice en distintos equipos con configuraciones regionales o idiomas diferentes. De forma predeterminada, se utiliza la página de códigos devuelta por la función GetACP().  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT CvCreateMarkerSeriesWithCodePageA(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ LPCSTR pSeriesName,  
   _In_ UINT nTextCodePage,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pProvider`  
 Objeto de proveedor inicializado anteriormente por CvInitProvider. No puede ser nulo.  
  
 `pSeriesName`  
 Nombre de la serie de marcador. No puede ser nulo, pero se permite una cadena vacía.  
  
 `nTextCodePage`  
 Página de códigos válida.  
  
 `ppMarkerSeries`  
 Dirección de una variable de salida que almacenará el contexto de la serie de marcador. No puede ser nulo.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK cuando la serie de marcador se crea correctamente, o código de error en caso de que se hayan producido errores. Utilice macros SUCCEEDED/FAILED para comprobar si existe una condición de error.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** cvmarkers.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia de la biblioteca C++](../profiling/cpp-library-reference.md)



