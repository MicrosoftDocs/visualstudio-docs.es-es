---
title: IDebugMemoryBytes2::WriteAt | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b432f24b5d2e357f8ae5c20cb079ce4a415e083c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49827404"
---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Escribe el número especificado de bytes de memoria, empezando en la dirección especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT WriteAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory  
);  
```  
  
```csharp  
int WriteAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pStartContext`  
 [in] El [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) objeto que especifica dónde se inicia la escritura de bytes.  
  
 `dwCount`  
 [in] El número de bytes que se escriben.  
  
 `rgbMemory`  
 [in] Para escribir los bytes. Esta matriz se supone que es al menos `dwCount` bytes de tamaño.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` si no todos los bytes se podría escribir o devuelve un código de error (normalmente `E_FAIL`).  
  
## <a name="remarks"></a>Comentarios  
 Si la dirección inicial no está dentro de la ventana memoria representada por este [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) objeto, se produce ninguna escritura y un código de error `E_FAIL` se devuelve, incluso si se superpone la cantidad para escribir en el espacio de memoria.  
  
## <a name="see-also"></a>Vea también  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)

