---
title: IRemoteDebugApplicationThread::SetNextStatement | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.SetNextStatement
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::SetNextStatement
ms.assetid: 356766da-f7b7-4e8d-b4f3-2ab8da0609b8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c4b19322a15e92adcf2609c479af6b21e2078bd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62788146"
---
# <a name="iremotedebugapplicationthreadsetnextstatement"></a>IRemoteDebugApplicationThread::SetNextStatement
Ejecución de fuerzas lo antes posible en el contexto de código dado, continúe en el contexto del marco especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT SetNextStatement(  
   IDebugStackFrame*   pStackFrame,  
   IDebugCodeContext*  pCodeContext  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pStackFrame`  
 [in] El objeto de marco de pila. Este argumento puede ser NULL, lo que implica que se debe usar el marco de pila actual.  
  
 `pCodeContext`  
 [in] El contexto del código. Este argumento puede ser NULL, lo que implica que se debe usar el contexto de código actual.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método obliga a que continúe lo antes posible para el contexto de código especificado por la ejecución `pCodeContext`, en el contexto del marco especificado por `pStackFrame`. Puede ser cualquiera de estos argumentos `NULL`, que representa el contexto o el marco actual.  
  
## <a name="see-also"></a>Vea también  
 [IRemoteDebugApplicationThread (Interfaz)](../../winscript/reference/iremotedebugapplicationthread-interface.md)