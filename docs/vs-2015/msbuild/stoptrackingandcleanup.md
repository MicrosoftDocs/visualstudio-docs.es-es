---
title: StopTrackingAndCleanup | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
api_name:
- StopTrackingAndCleanup
api_location:
- filetracker.dll
api_type:
- COM
helpviewer_keywords:
- StopTrackingAndCleanup
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 39471ea7f88849151e9f6c0c6cc65bdd913d7af2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574777"
---
# <a name="stoptrackingandcleanup"></a>StopTrackingAndCleanup
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [StopTrackingAndCleanup](https://docs.microsoft.com/visualstudio/msbuild/stoptrackingandcleanup).  
  
  
Detiene todo el seguimiento y libera la memoria que ha usado la sesión de seguimiento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT WINAPI StopTrackingAndCleanup(void);  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un valor [HRESULT] (<!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->) con la [correcto] (<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->) conjunto de bits si se detuvo el seguimiento.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** FileTracker.h  
  
## <a name="see-also"></a>Vea también  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)



