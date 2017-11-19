---
title: IApplicationDebugger::onDebuggerEvent | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IApplicationDebugger.onDebuggerEvent
apilocation: scrobj.dll
helpviewer_keywords: IApplicationDebugger::onDebuggerEvent
ms.assetid: 82a5faaa-1222-4bf1-8569-10439dbdf16d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 754c56b8474a5e21a05c1399540391197c373118
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iapplicationdebuggerondebuggerevent"></a>IApplicationDebugger::onDebuggerEvent
Controla un evento de aplicación personalizada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT onDebuggerEvent(  
   REFIID     riid,  
   IUnknown*  punk  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `riid`  
 [in] El identificador de interfaz para el objeto.  
  
 `punk`  
 [in] El objeto de evento, que implementa la interfaz definida por `riid`.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_NOTIMPL`|El método no está implementado actualmente.|  
  
## <a name="remarks"></a>Comentarios  
 La semántica de la `IUnknown` es totalmente aplicación/depurador definido.  
  
 Este método permite que las extensiones personalizadas del modelo de depurador; no está implementada actualmente.  
  
 Se llama a este método cuando `IDebugApplication::FireDebuggerEvent` se llama.  
  
## <a name="see-also"></a>Vea también  
 [IApplicationDebugger (interfaz)](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)