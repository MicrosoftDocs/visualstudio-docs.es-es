---
title: 'Iapplicationdebugger (:: onDebuggerEvent | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.onDebuggerEvent
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::onDebuggerEvent
ms.assetid: 82a5faaa-1222-4bf1-8569-10439dbdf16d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f8edb2a3c39d639b5b6722707d7b6c0b57a5c19
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577860"
---
# <a name="iapplicationdebuggerondebuggerevent"></a>IApplicationDebugger::onDebuggerEvent
Controla un evento de aplicación personalizado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT onDebuggerEvent(  
   REFIID     riid,  
   IUnknown*  punk  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `riid`  
 de Identificador de interfaz para el objeto.  
  
 `punk`  
 de Objeto de evento, que implementa la interfaz definida por `riid`.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_NOTIMPL`|El método no está implementado actualmente.|  
  
## <a name="remarks"></a>Comentarios  
 La semántica del `IUnknown` es totalmente Application/Debugger defined.  
  
 Este método permite extensiones personalizadas del modelo del depurador. no está implementado actualmente.  
  
 Se llama a este método cuando se llama a `IDebugApplication::FireDebuggerEvent`.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz iapplicationdebugger (](../../winscript/reference/iapplicationdebugger-interface.md)  
 [IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)