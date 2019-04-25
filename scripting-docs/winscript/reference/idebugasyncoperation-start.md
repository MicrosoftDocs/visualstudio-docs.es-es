---
title: IDebugAsyncOperation::Start | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.Start
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::Start
ms.assetid: a7272364-28e0-48ae-8405-b8bce8a6b9fd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b3e02869abab65878412f96b77d5782b9717a1b6
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155711"
---
# <a name="idebugasyncoperationstart"></a>IDebugAsyncOperation::Start
Hace que la operación asincrónica empezar.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Start(  
   IDebugAsyncOperationCallBack*  padocb  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `padocb`  
 La interfaz de devolución de llamada que recibe eventos de estado de esta operación.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_UNEXPECTED`|Una operación ya está pendiente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método provoca que `IDebugSyncOperation::Execute` llamada de forma asincrónica en el subproceso obtenido `IDebugSyncOperation::GetTargetThread`. Este método debe llamarse únicamente desde dentro del subproceso del depurador; en caso contrario, no devolverá hasta que se complete la operación.  
  
## <a name="see-also"></a>Vea también  
 [IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)   
 [IDebugAsyncOperation (interfaz)](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)   
 [IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)