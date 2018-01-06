---
title: IDebugMemoryBytes2::ReadAt | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f4c71da3152394442d63c937b77e4f6538fcc1ae
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
Lee una secuencia de bytes, comenzando en una ubicación especificada.  
  
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
 [in] El número de bytes que se va a leer. También especifica la longitud de la `rgbMemory` matriz.  
  
 `rgbMemory`  
 [entrada, salida] Matriz que se rellena con los bytes leídos realmente.  
  
 `pdwRead`  
 [out] Devuelve el número de bytes contiguos leídos realmente.  
  
 `pdwUnreadable`  
 [entrada, salida] Devuelve el número de bytes no se puede leer. Puede ser un valor null si el cliente no está interesado en el número de bytes no se puede leer.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Si se solicitan 100 bytes y los primeros 50 son legibles, los 20 siguientes no son legibles y las 30 restantes son legibles, se devuelve este método:  
  
 *`pdwRead` = 50  
  
 *`pdwUnreadable` = 20  
  
 En este caso, porque `*pdwRead + *pdwUnreadable < dwCount`, el llamador debe realizar una llamada adicional al leer los bytes de 30 restantes de las 100 original solicitado y [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) objeto pasado en el `pStartContext` debe hacer avanzar el parámetro por 70.  
  
## <a name="see-also"></a>Vea también  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)