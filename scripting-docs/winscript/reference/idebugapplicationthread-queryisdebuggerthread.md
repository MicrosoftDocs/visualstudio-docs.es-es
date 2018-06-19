---
title: IDebugApplicationThread::QueryIsDebuggerThread | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationThread.QueryIsDebuggerThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationThread::QueryIsDebuggerThread
ms.assetid: 78a9cfbf-7c62-4aab-82a2-35037e2f9d46
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c3ad00fafa602b7a2f55b0412ae16c82cc2f5bf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725845"
---
# <a name="idebugapplicationthreadqueryisdebuggerthread"></a>IDebugApplicationThread::QueryIsDebuggerThread
Determina si este subproceso es el subproceso del depurador.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT QueryIsDebuggerThread();  
```  
  
#### <a name="parameters"></a>Parámetros  
 Este método no toma ningún parámetro.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente y se trata el subproceso del depurador.|  
|`S_FALSE`|Esto no es el subproceso del depurador.|  
  
## <a name="remarks"></a>Comentarios  
 Este método determina si este subproceso es el subproceso del depurador.  
  
## <a name="see-also"></a>Vea también  
 [IDebugApplicationThread (Interfaz)](../../winscript/reference/idebugapplicationthread-interface.md)