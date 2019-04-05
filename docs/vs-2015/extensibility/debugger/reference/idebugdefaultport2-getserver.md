---
title: IDebugDefaultPort2::GetServer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetServer
helpviewer_keywords:
- IDebugDefaultPort2::GetServer
ms.assetid: cacb4b74-0f39-471c-af38-54b73f5b2868
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2a74a9e846532b119c5b72495c39226effdc94f0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58987684"
---
# <a name="idebugdefaultport2getserver"></a>IDebugDefaultPort2::GetServer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Este método obtiene una interfaz para el servidor que en este puerto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetServer(  
   IDebugCoreServer3** ppServer  
);  
```  
  
```csharp  
int GetServer(  
   out IDebugCoreServer3 ppServer  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppServer`  
 [out] Devuelve un objeto que implementa el [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) interfaz.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) se implementa mediante Visual Studio y representa el servidor que el puerto se encuentra en.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
