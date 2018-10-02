---
title: IDebugEngine2::SetRegistryRoot | Documentos de Microsoft
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
- IDebugEngine2::SetRegistryRoot
helpviewer_keywords:
- IDebugEngine2::SetRegistryRoot
ms.assetid: d0d81202-8a4a-4bc3-b297-30a047c5ec60
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5bb1eef7f2cc3b43e5771f96094db58a20490677
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47575935"
---
# <a name="idebugengine2setregistryroot"></a>IDebugEngine2::SetRegistryRoot
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugEngine2::SetRegistryRoot](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugengine2-setregistryroot).  
  
Establece la raíz del registro para el motor de depuración (DE).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT SetRegistryRoot(   
   LPCOLESTR pszRegistryRoot  
);  
```  
  
```csharp  
int SetRegistryRoot(   
   string pszRegistryRoot  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pszRegistryRoot`  
 [in] La raíz del registro para usar.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método permite [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] para especificar una raíz alternativa del registro que la DE debe usar para obtener la configuración del registro; por ejemplo, "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp".  
  
## <a name="see-also"></a>Vea también  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)

