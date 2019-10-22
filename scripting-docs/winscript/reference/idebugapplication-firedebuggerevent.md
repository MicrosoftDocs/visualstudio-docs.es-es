---
title: 'Idebugapplication (:: FireDebuggerEvent | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.FireDebuggerEvent
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::FireDebuggerEvent
ms.assetid: fd1f602e-fc15-4158-a6e7-497ff5b4a509
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 00d895ed484e37f0ba38636a409876156ed97287
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575009"
---
# <a name="idebugapplicationfiredebuggerevent"></a>IDebugApplication::FireDebuggerEvent
Desencadena un evento genérico en la interfaz de `IApplicationDebugger` del depurador.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT FireDebuggerEvent(  
   REFGUID    riid,  
   IUnknown*  punk  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `riid`  
 de Un GUID para el objeto.  
  
 `punk`  
 de Objeto de evento que se va a pasar al depurador.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_NOTIMPL`|El método no está implementado actualmente.|  
  
## <a name="remarks"></a>Comentarios  
 La semántica del GUID y el `IUnknown` están definidas por completo en la aplicación o el depurador.  
  
 Este método permite extensiones personalizadas del modelo del depurador. no está implementado actualmente.  
  
 Este método hace que se llame a `IApplicationDebugger::onDebuggerEvent`.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz idebugapplication (](../../winscript/reference/idebugapplication-interface.md)  
 [IApplicationDebugger::onDebuggerEvent](../../winscript/reference/iapplicationdebugger-ondebuggerevent.md)