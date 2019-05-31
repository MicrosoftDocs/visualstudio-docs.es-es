---
title: StartTrackingContextWithRoot | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
api_name:
- StartTrackingContextWithRoot
api_location:
- filetracker.dll
api_type:
- COM
helpviewer_keywords:
- StartTrackingContextWithRoot
ms.assetid: f6ef2b76-8035-4a14-8195-aa221c46ef48
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 68e80da01a0ab1ad59bbb5bdb06c92c1a11a8ac1
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59666239"
---
# <a name="starttrackingcontextwithroot"></a>StartTrackingContextWithRoot
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Inicia un contexto de seguimiento con un archivo de respuesta que especifica un marcador raíz.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `intermediateDirectory`  
 El directorio en el que almacenar el registro de seguimiento.  
  
 [in] `taskName`  
 Identifica el contexto de seguimiento. Este nombre se usa para crear el nombre del archivo de registro.  
  
 [in] `rootMarkerResponseFile`  
 El nombre de ruta de acceso de un archivo de respuesta que contiene un marcador raíz. El nombre de raíz se usa para agrupar todo el seguimiento de un contexto conjuntamente.  
  
## <a name="return-value"></a>Valor devuelto  
 Una ([HRESULT]<!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->) con el ([correcto]<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->) conjunto de bits si se creó el contexto de seguimiento.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado**: FileTracker.h  
  
## <a name="see-also"></a>Vea también  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)
