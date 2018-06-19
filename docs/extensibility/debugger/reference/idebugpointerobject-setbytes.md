---
title: IDebugPointerObject::SetBytes | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a8234117d7965c4f2e471855d39ed0c3cee1f88c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31114299"
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
Establece el valor al que apunta de una serie de bytes consecutivos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT SetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```csharp  
int SetBytes(  
   uint     dwStart,   
   uint     dwCount,   
   byte[]   pBytes,   
   out uint pdwBytes  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwStart`  
 [in] Un desplazamiento, en bytes, desde el principio del objeto indicado.  
  
 `dwCount`  
 [in] El número de bytes que se va a establecer.  
  
 `pBytes`  
 [in] Una matriz de bytes que representa el nuevo valor. Este valor se almacena en el objeto, empezando en el desplazamiento dado.  
  
 `pdwBytes`  
 [out] Devuelve que el número de bytes establecido realmente.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método se utiliza si el puntero tal como está representado por este [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) apunta a un tipo primitivo o una matriz de tipos primitivos (es decir, una matriz que puede representarse mediante una secuencia de bytes simple) simple. Esto `IDebugPointerObject` objeto no puede ser una referencia nula (debe apuntar a una dirección de memoria).  
  
## <a name="see-also"></a>Vea también  
 [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)   
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)