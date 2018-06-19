---
title: IDebugDefaultPort2::GetServer | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDefaultPort2::GetServer
helpviewer_keywords:
- IDebugDefaultPort2::GetServer
ms.assetid: cacb4b74-0f39-471c-af38-54b73f5b2868
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 61e4ea81da1e8f31cabd7c2dae6ca5dc3251eef8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31106686"
---
# <a name="idebugdefaultport2getserver"></a>IDebugDefaultPort2::GetServer
Este método obtiene una interfaz para el servidor en este puerto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetServer(  
   IDebugCoreServer3** ppServer  
);  
```  
  
```csharp  
int GetServer(  
   out IDebugCoreServer3 ppServer  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppServer`  
 [out] Devuelve un objeto que implementa el [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) interfaz.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) es implementada por Visual Studio y representa el servidor que el puerto se encuentra en.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)