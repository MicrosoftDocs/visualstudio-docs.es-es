---
title: IDebugMemoryContext2::Subtract | Documentos de Microsoft
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
- IDebugMemoryContext2::Subtract
helpviewer_keywords:
- Subtract method
- IDebugMemoryContext2::Subtract method
ms.assetid: 63df14c7-8d7e-47c1-afa7-5a1ab5d8eaba
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3265e8845340b2a02dbd5bf30c05b9e4c4d2400b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47567311"
---
# <a name="idebugmemorycontext2subtract"></a>IDebugMemoryContext2::Subtract
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugMemoryContext2::Subtract](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugmemorycontext2-subtract).  
  
Resta el valor especificado desde el contexto actual y devuelve un nuevo contexto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT Subtract(   
   UINT64                 dwCount,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```csharp  
int Subtract(  
   ulong                    dwCount,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwCount`  
 [in] El número de bytes de memoria para reducir.  
  
 `ppMemCxt`  
 [out] Devuelve un nuevo [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) objeto.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Un contexto de la memoria es una dirección, por lo que si se resta un valor desde una dirección genera una nueva dirección que requiere una nueva interfaz de contexto.  
  
 Este método siempre debe generar un nuevo contexto, incluso si la dirección resultante está fuera del espacio de memoria asociado con este contexto. La única excepción a esto es si no se puede asignar ninguna memoria para el nuevo contexto o si `ppMemCxt` es un valor null (que es un error).  
  
## <a name="see-also"></a>Vea también  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)

