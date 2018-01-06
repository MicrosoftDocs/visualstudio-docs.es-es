---
title: IDebugThread2::EnumFrameInfo | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugThread2::EnumFrameInfo
helpviewer_keywords: IDebugThread2::EnumFrameInfo
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a906cb23432c9b51d80ee6e0ff97cc5d30f2a665
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugthread2enumframeinfo"></a>IDebugThread2::EnumFrameInfo
Recupera una lista de los marcos de pila para este subproceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
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
 [in] Una combinación de indicadores de la [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) enumeración que especifica qué campos de la [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) estructuras son debe rellenarse. Especifique el `FIF_FUNCNAME_FORMAT` marca para dar formato al nombre de función en una sola cadena.  
  
 `nRadix`  
 [in] Base usada para dar formato a la información numérica en el enumerador.  
  
 `ppEnum`  
 [out] Devuelve un [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) objeto que contiene una lista de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) estructuras que describen el marco de pila.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Marcos de subproceso se enumeran en orden, con el marco actual que se enumeran en primer lugar y el marco más antiguo enumerado en último lugar.  
  
## <a name="see-also"></a>Vea también  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)