---
title: IDebugMemoryBytes2::WriteAt | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 14d5aa4fa026f27f6b083d656cd5df3f8b7d7f41
ms.contentlocale: es-es
ms.lasthandoff: 09/06/2017

---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
Escribe el número especificado de bytes de memoria, comenzando en la dirección especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
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
 [in] El número de bytes que se va a escribir.  
  
 `rgbMemory`  
 [in] Los bytes que se va a escribir. Esta matriz se supone que es al menos `dwCount` bytes de tamaño.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` si no todos los bytes se podría escribir o devuelve un código de error (normalmente `E_FAIL`).  
  
## <a name="remarks"></a>Comentarios  
 Si la dirección inicial no está dentro de la ventana memoria representada por este [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) de objeto, se produce ninguna escritura y un código de error `E_FAIL` se devuelve, incluso si se superpone a la cantidad para escribir en el espacio de memoria.  
  
## <a name="see-also"></a>Vea también  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
