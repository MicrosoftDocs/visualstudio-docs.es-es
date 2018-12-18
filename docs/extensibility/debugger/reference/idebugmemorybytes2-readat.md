---
title: IDebugMemoryBytes2::ReadAt | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3e3989ef8c79e4304e3bda3e99418da1973e6e0a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49912953"
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
Lee una secuencia de bytes, empezando en una ubicación determinada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT ReadAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory,  
   DWORD*                pdwRead,  
   DWORD*                pdwUnreadable  
);  
```  
  
```csharp  
int ReadAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory,  
   out uint             pdwRead,  
   ref uint             pdwUnreadable  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pStartContext`  
 [in] El [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) objeto que especifica dónde empezar a leer los bytes.  
  
 `dwCount`  
 [in] El número de bytes que se leen. También especifica la longitud de la `rgbMemory` matriz.  
  
 `rgbMemory`  
 [in, out] Matriz que se rellena con los bytes leídos realmente.  
  
 `pdwRead`  
 [out] Devuelve el número de bytes contiguos leídos realmente.  
  
 `pdwUnreadable`  
 [in, out] Devuelve el número de bytes no se puede leer. Puede ser un valor null si el cliente no está interesado en el número de bytes no se puede leer.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Si se solicitan 100 bytes y los 50 primeros son legibles, los 20 siguientes no son legibles y el 30 restantes son legibles, se devuelve este método:  
  
 *`pdwRead` = 50  
  
 *`pdwUnreadable` = 20  
  
 En este caso, porque `*pdwRead + *pdwUnreadable < dwCount`, el llamador debe realizar una llamada adicional al leer los bytes restantes 30 de las 100 original solicitado y [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) objeto pasado en el `pStartContext` parámetro debe ser avanzado por 70.  
  
## <a name="see-also"></a>Vea también  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)