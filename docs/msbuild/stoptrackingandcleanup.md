---
title: StopTrackingAndCleanup | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StopTrackingAndCleanup
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StopTrackingAndCleanup
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ecf9f27acf0cebbf6a0e1d00da961f1733a66f4d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990469"
---
# <a name="stoptrackingandcleanup"></a>StopTrackingAndCleanup
Detiene todo el seguimiento y libera la memoria que ha usado la sesión de seguimiento.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp 
HRESULT WINAPI StopTrackingAndCleanup(void);  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un elemento **HRESULT** con el conjunto de bits **SUCCEEDED** si el seguimiento se ha detenido.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado**: *FileTracker.h*  
  
## <a name="see-also"></a>Vea también  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)