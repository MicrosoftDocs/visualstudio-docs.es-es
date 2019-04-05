---
title: IDebugPointerObject::SetBytes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9d467b037f4e2affea53a142304507f876630999
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58998191"
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Establece el valor señalado por una serie de bytes consecutivos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 [in] Posición de desplazamiento, en bytes, desde el principio del objeto que apunta.  
  
 `dwCount`  
 [in] El número de bytes para establecer.  
  
 `pBytes`  
 [in] Una matriz de bytes que representa el nuevo valor. Este valor se almacena en el objeto, comenzando en el desplazamiento dado.  
  
 `pdwBytes`  
 [out] Devuelve que el número de bytes establecido realmente.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método se utiliza si el puntero, tal como está representada por este [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) apunta a un tipo primitivo o una matriz de tipos primitivos (es decir, una matriz que puede representarse mediante una sencilla secuencia de bytes). Esto `IDebugPointerObject` objeto no puede ser una referencia nula (debe apuntar a una dirección de memoria).  
  
## <a name="see-also"></a>Vea también  
 [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)   
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
