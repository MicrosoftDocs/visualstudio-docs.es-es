---
title: 'Idebugasyncoperation (:: Start | Microsoft Docs'
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
ms.openlocfilehash: 485eb34ebe200e7f7898d9338effed37cbf2aa10
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573248"
---
# <a name="idebugasyncoperationstart"></a>IDebugAsyncOperation::Start
Hace que se inicie la operación asincrónica.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Start(  
   IDebugAsyncOperationCallBack*  padocb  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `padocb`  
 La interfaz de devolución de llamada que recibe los eventos de estado de esta operación.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_UNEXPECTED`|Una operación ya está pendiente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método hace que se llame a `IDebugSyncOperation::Execute` de forma asincrónica en el subproceso Obtenido de `IDebugSyncOperation::GetTargetThread`. Solo se debe llamar a este método desde dentro del subproceso del depurador; de lo contrario, no se devolverá hasta que se complete la operación.  
  
## <a name="see-also"></a>Vea también  
 [Idebugasyncoperation (:: Abort](../../winscript/reference/idebugasyncoperation-abort.md)    
 @No__t_1 de la [interfaz idebugasyncoperation (](../../winscript/reference/idebugasyncoperation-interface.md)  
 [Idebugsyncoperation (:: execute](../../winscript/reference/idebugsyncoperation-execute.md)    
 [IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)