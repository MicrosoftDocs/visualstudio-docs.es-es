---
title: IDebugApplication::QueryCurrentThreadIsDebuggerThread | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.QueryCurrentThreadIsDebuggerThread
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::QueryCurrentThreadIsDebuggerThread
ms.assetid: e22ad8a4-a8be-423d-80f2-28256a7448ed
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bbd09a19212df3c91bf8222eb78b88f7c0b674fd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationquerycurrentthreadisdebuggerthread"></a>IDebugApplication::QueryCurrentThreadIsDebuggerThread
Determina si el subproceso de ejecución actual es el subproceso del depurador.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT QueryCurrentThreadIsDebuggerThread();  
```  
  
#### <a name="parameters"></a>Parámetros  
 Este método no toma ningún parámetro.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente y el subproceso de ejecución actual es el subproceso del depurador.|  
|`S_FALSE`|El subproceso de ejecución actual no es el subproceso del depurador.|  
  
## <a name="remarks"></a>Comentarios  
 Este método determina si el subproceso de ejecución actual es el subproceso del depurador.  
  
## <a name="see-also"></a>Vea también  
 [IDebugApplication (Interfaz)](../../winscript/reference/idebugapplication-interface.md)