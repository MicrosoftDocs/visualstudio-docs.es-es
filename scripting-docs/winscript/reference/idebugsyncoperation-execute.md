---
title: IDebugSyncOperation::Execute | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSyncOperation.Execute
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugSyncOperation::Execute
ms.assetid: a45b8c7d-c51a-4098-877f-fbec2f1f6947
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d8c10973bddef45321b9942afef05a696010433f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090225"
---
# <a name="idebugsyncoperationexecute"></a>IDebugSyncOperation::Execute
Sincrónicamente realiza la operación y devuelve.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Execute(  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppunkResult`  
 [out] El parámetro del objeto devuelto por la operación.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_ABORT`|Se anuló la operación mediante una llamada a la `IDebugSyncOperation::InProgressAbort` método.|  
  
## <a name="remarks"></a>Comentarios  
 El Administrador de procesos de depuración en el subproceso de destino llama a la `Execute` método sincrónicamente.  
  
## <a name="see-also"></a>Vea también  
 [IDebugSyncOperation (Interfaz)](../../winscript/reference/idebugsyncoperation-interface.md)