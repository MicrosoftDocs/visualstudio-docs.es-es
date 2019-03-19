---
title: IDebugAsyncOperation::Abort | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.Abort
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::Abort
ms.assetid: 232541c6-81b8-4eb7-96a7-a8e5fe087b31
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: be696f852f7038316141415494920c43580738c9
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155451"
---
# <a name="idebugasyncoperationabort"></a>IDebugAsyncOperation::Abort
Cancela una operación.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Abort();  
```  
  
#### <a name="parameters"></a>Parámetros  
 Este método no toma ningún parámetro.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|S_OK|El método se realizó correctamente.|  
|E_NOTIMPL|No se puede cancelar las operaciones.|  
  
## <a name="remarks"></a>Comentarios  
 Normalmente, este método se llama desde dentro del subproceso del depurador para cancelar una operación que no responde. Este método provoca que el `InProgressAbort` método en el `IDebugSyncOperation` objeto que se llama.  
  
## <a name="see-also"></a>Vea también  
 [IDebugAsyncOperation (interfaz)](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)   
 [IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)