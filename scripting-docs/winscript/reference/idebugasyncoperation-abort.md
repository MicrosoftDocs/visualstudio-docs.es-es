---
title: 'Idebugasyncoperation (:: ABORT | Microsoft Docs'
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
ms.openlocfilehash: b9ca6c5e1498229c84dc28a13cda2cce77b58a4f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573301"
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
|E_NOTIMPL|Las operaciones no se pueden cancelar.|  
  
## <a name="remarks"></a>Comentarios  
 Normalmente, se llama a este método desde el subproceso del depurador para cancelar una operación que no responde. Este método hace que se llame al método `InProgressAbort` del objeto `IDebugSyncOperation`.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz idebugasyncoperation (](../../winscript/reference/idebugasyncoperation-interface.md)  
 [Idebugasyncoperation (:: Start](../../winscript/reference/idebugasyncoperation-start.md)    
 [IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)