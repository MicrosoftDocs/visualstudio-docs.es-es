---
title: 'Idebugapplication (:: QueryCurrentThreadIsDebuggerThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.QueryCurrentThreadIsDebuggerThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::QueryCurrentThreadIsDebuggerThread
ms.assetid: e22ad8a4-a8be-423d-80f2-28256a7448ed
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f70cde752506919d90bf963d010ebfc7abf5e88
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577212"
---
# <a name="idebugapplicationquerycurrentthreadisdebuggerthread"></a>IDebugApplication::QueryCurrentThreadIsDebuggerThread
Determina si el subproceso que se está ejecutando actualmente es el subproceso del depurador.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT QueryCurrentThreadIsDebuggerThread();  
```  
  
#### <a name="parameters"></a>Parámetros  
 Este método no toma ningún parámetro.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente y el subproceso que se está ejecutando actualmente es el subproceso del depurador.|  
|`S_FALSE`|El subproceso en ejecución actual no es el subproceso del depurador.|  
  
## <a name="remarks"></a>Comentarios  
 Este método determina si el subproceso que se está ejecutando actualmente es el subproceso del depurador.  
  
## <a name="see-also"></a>Vea también  
 [IDebugApplication (Interfaz)](../../winscript/reference/idebugapplication-interface.md)