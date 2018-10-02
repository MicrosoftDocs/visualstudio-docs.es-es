---
title: IDebugDefaultPort2::GetPortNotify | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0a0cd508f0eab1d4ffc0feea32de128c411bef6c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47576706"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugDefaultPort2::GetPortNotify](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdefaultport2-getportnotify).  
  
Este método obtiene una [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) interfaz para este puerto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetPortNotify(  
   IDebugPortNotify2** ppPortNotify  
);  
```  
  
```csharp  
int GetPortNotify(  
   out IDebugPortNotify2 ppPortNotify  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppPortNotify`  
 [out] Un [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) objeto.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Normalmente, el `QueryInterface` se llama al método en el objeto que implementa el [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfaz para obtener un [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) interfaz. Sin embargo, hay circunstancias en que se implementará la interfaz deseada en un objeto diferente. Este método se oculta en esas circunstancias y devuelve el `IDebugPortNotify2` interfaz desde el objeto más adecuado.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)

