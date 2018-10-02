---
title: IDebugSymbolProvider::GetNamespacesUsedAtAddress | Documentos de Microsoft
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
- IDebugSymbolProvider::GetNamespacesUsedAtAddress
helpviewer_keywords:
- IDebugSymbolProvider::GetNamespacesUsedAtAddress method
ms.assetid: 392de54b-9af0-4567-953b-1b41acd1e05c
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a0240bb2d01f0c031e48b9cf60fda0ff85935ea7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577134"
---
# <a name="idebugsymbolprovidergetnamespacesusedataddress"></a>IDebugSymbolProvider::GetNamespacesUsedAtAddress
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugSymbolProvider::GetNamespacesUsedAtAddress](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress).  
  
Este método crea un enumerador para los espacios de nombres asociado a la dirección de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetNamespacesUsedAtAddress(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int GetNamespacesUsedAtAddress(  
   IDebugAddress        pAddress,  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pAddress`  
 [in] La dirección de depuración.  
  
 `ppEnum`  
 [out] Devuelve un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) enumerador para los espacios de nombres.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Puede haber anidada de varios espacios de nombres asociados con una dirección de depuración determinado, por ejemplo, los espacios de nombres o varios `using` instrucciones.  
  
## <a name="see-also"></a>Vea también  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)

