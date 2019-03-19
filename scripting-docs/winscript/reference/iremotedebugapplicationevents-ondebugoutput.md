---
title: IRemoteDebugApplicationEvents::OnDebugOutput | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEvents.OnDebugOutput
apilocation:
- jscript.dll
helpviewer_keywords:
- IRemoteDebugApplicationEvents::OnDebugOutput
ms.assetid: db08872e-3d84-4d7f-bf94-a851bf43a333
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c7f4c6572a7b06a8ab0ca78419b0bd6518f0e55
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152673"
---
# <a name="iremotedebugapplicationeventsondebugoutput"></a>IRemoteDebugApplicationEvents::OnDebugOutput
Controla un evento de salida del depurador.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT OnDebugOutput(  
   LPCOLESTR  pstr  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pstr`  
 [in] La cadena de salida de depuración.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método controla el evento de salida del depurador.  
  
## <a name="see-also"></a>Vea también  
 [IRemoteDebugApplicationEvents (Interfaz)](../../winscript/reference/iremotedebugapplicationevents-interface.md)