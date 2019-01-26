---
title: IDebugCoreServer3::GetServerFriendlyName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer3::GetServerFriendlyName
helpviewer_keywords:
- IDebugCoreServer3::GetServerFriendlyName
ms.assetid: 7035b904-b3d7-4d9b-98d9-65714b8a8b9f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e74ccfaf6486a10440208a56de70564304533c87
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55028538"
---
# <a name="idebugcoreserver3getserverfriendlyname"></a>IDebugCoreServer3::GetServerFriendlyName
Recupera un nombre descriptivo para el servidor.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetServerFriendlyName(  
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetServerFriendlyName(  
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pbstrName`  
 [out] Devuelve un nombre descriptivo para el servidor.  
  
> [!NOTE]
>  El llamador es responsable de liberar la cadena.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve el código de error.  
  
## <a name="remarks"></a>Comentarios  
 Para los servidores iniciado por el usuario, el nombre devuelto por este método es el nombre completo del servidor. Para los servidores iniciado automáticamente, el nombre es de la máquina que el servidor se ejecuta en.  
  
 Para un nombre orientado a la máquina, llame a la [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md) método.  
  
## <a name="see-also"></a>Vea también  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)