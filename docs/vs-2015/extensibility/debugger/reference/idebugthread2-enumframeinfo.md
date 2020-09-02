---
title: 'IDebugThread2:: EnumFrameInfo | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
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
 de Combinación de marcas de la enumeración [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) que especifica los campos de las estructuras [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) que se van a rellenar. Especifique la `FIF_FUNCNAME_FORMAT` marca para dar formato al nombre de la función en una sola cadena.  
  
 `nRadix`  
 de Base usada para dar formato a la información numérica en el enumerador.  
  
 `ppEnum`  
 enuncia Devuelve un objeto [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) que contiene una lista de estructuras [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) que describe el marco de pila.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Los fotogramas del subproceso se enumeran en orden, con el fotograma actual enumerado primero y el fotograma más antiguo enumerado en último lugar.  
  
## <a name="see-also"></a>Consulte también  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
