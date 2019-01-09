---
title: IDebugHelper::CreateSimpleConnectionPoint | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugHelper.CreateSimpleConnectionPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugHelper::CreateSimpleConnectionPoint
ms.assetid: 5e4798ce-6f9f-4184-9853-67bf8c8524ab
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b478f425b1aaf284bc7af744f5ac99f9be7fe8c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097076"
---
# <a name="idebughelpercreatesimpleconnectionpoint"></a>IDebugHelper::CreateSimpleConnectionPoint
Devuelve una interfaz de evento que encapsula un determinado `IDispatch` objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT CreateSimpleConnectionPoint(  
   IDispatch*                pdisp  
   ISimpleConnectionPoint**  ppscp  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pdisp`  
 [in] La `IDispatch` objeto que se va a ajustar.  
  
 `ppscp`  
 [out] La interfaz de eventos que se ajusta `pdisp`.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Devuelve una interfaz de eventos que se ajusta el determinado `IDispatch` (consulte [ISimpleConnectionPoint (interfaz)](../../winscript/reference/isimpleconnectionpoint-interface.md)).  
  
## <a name="see-also"></a>Vea también  
 [IDebugHelper (interfaz)](../../winscript/reference/idebughelper-interface.md)   
 [ISimpleConnectionPoint (Interfaz)](../../winscript/reference/isimpleconnectionpoint-interface.md)