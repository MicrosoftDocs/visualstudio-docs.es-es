---
title: IDebugApplicationThread::SetStateString | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplicationThread.SetStateString
apilocation: pdm.dll
helpviewer_keywords: IDebugApplicationThread::SetStateString
ms.assetid: a59001d5-ea00-4fd0-bb20-0b592d9c795d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2eafe5477759dbad109e5ae6294b477d56f9ee14
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthreadsetstatestring"></a>IDebugApplicationThread::SetStateString
Establece la descripción del estado de los subprocesos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT SetStateString(  
   LPCOLESTR  pstrState  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pstrState`  
 [in] La descripción del estado de subproceso.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método establece la descripción del estado de subproceso.  
  
## <a name="see-also"></a>Vea también  
 [IDebugApplicationThread (Interfaz)](../../winscript/reference/idebugapplicationthread-interface.md)