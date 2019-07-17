---
title: IDebugThread2::EnumFrameInfo | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugThread2::EnumFrameInfo
helpviewer_keywords:
- IDebugThread2::EnumFrameInfo
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: efda31daae198befbda35803ef71e1d0322e9bbd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68153081"
---
# <a name="idebugthread2enumframeinfo"></a>IDebugThread2::EnumFrameInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera una lista de los marcos de pila para este subproceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT EnumFrameInfo (   
   FRAMEINFO_FLAGS        dwFieldSpec,  
   UINT                   nRadix,  
   IEnumDebugFrameInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumFrameInfo (   
   enum_FRAMEINFO_FLAGS     dwFieldSpec,  
   uint                     nRadix,  
   out IEnumDebugFrameInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwFieldSpec`  
 [in] Una combinación de marcas de la [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) enumeración que especifica qué campos de la [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) estructuras son para rellenarlo. Especifique el `FIF_FUNCNAME_FORMAT` marca para dar formato al nombre de función en una sola cadena.  
  
 `nRadix`  
 [in] Base usada para dar formato a la información numérica en el enumerador.  
  
 `ppEnum`  
 [out] Devuelve un [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) objeto que contiene una lista de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) estructuras que describen el marco de pila.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Los marcos del subproceso se enumeran en orden, con el fotograma actual enumerado en primer lugar y el más antiguo enumerado por última vez.  
  
## <a name="see-also"></a>Vea también  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
