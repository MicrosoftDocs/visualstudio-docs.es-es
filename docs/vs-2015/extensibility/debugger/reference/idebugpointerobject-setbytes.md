---
title: 'IDebugPointerObject:: SetBytes | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202969"
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Establece el valor al que apunta desde una serie de bytes consecutivos.  
  
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
 de Desplazamiento, en bytes, desde el inicio del objeto al que se señala.  
  
 `dwCount`  
 de Número de bytes que se van a establecer.  
  
 `pBytes`  
 de Matriz de bytes que representa el nuevo valor. Este valor se almacena en el objeto, comenzando en el desplazamiento dado.  
  
 `pdwBytes`  
 enuncia Devuelve el número de bytes establecidos realmente.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Observaciones  
 Este método se usa si el puntero representado por este [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) apunta a un tipo primitivo o a una matriz simple de tipos primitivos (es decir, una matriz que se puede representar mediante una secuencia simple de bytes). Este `IDebugPointerObject` objeto no puede ser una referencia nula (debe apuntar a una dirección en memoria).  
  
## <a name="see-also"></a>Consulte también  
 [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)   
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
