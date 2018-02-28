---
title: IDebugAsyncOperation::Start | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugAsyncOperation.Start
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::Start
ms.assetid: a7272364-28e0-48ae-8405-b8bce8a6b9fd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd39053e86dce95fa52ba8576814962d13d8b050
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebugasyncoperationstart"></a>IDebugAsyncOperation::Start
Hace que la operación asincrónica empezar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
 Este método provoca `IDebugSyncOperation::Execute` para llamar de manera asincrónica en el subproceso que se obtienen de `IDebugSyncOperation::GetTargetThread`. Este método debe llamarse únicamente desde dentro del subproceso del depurador; en caso contrario, no devolverá hasta que se complete la operación.  
  
## <a name="see-also"></a>Vea también  
 [IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)   
 [IDebugAsyncOperation (interfaz)](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)   
 [IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)