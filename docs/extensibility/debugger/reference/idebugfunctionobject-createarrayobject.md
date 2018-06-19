---
title: IDebugFunctionObject::CreateArrayObject | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 39695d37012f90d7e61c04f64ee1c05f11482373
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31112140"
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
Crea un objeto de matriz. Esta matriz puede contener a cualquier tipo primitivo o valores de la instancia del objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT CreateArrayObject(   
   OBJECT_TYPE    ot,  
   IDebugField*   pClassField,  
   DWORD          dwRank,  
   DWORD          dwDims[],  
   DWORD          dwLowBounds[],  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int CreateArrayObject(  
   enum_OBJECT_TYPE ot,   
   IDebugField      pClassField,   
   uint             dwRank,   
   uint[]           dwDims,   
   uint[]           dwLowBounds,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ot`  
 [in] Especifica un valor de la [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) enumeración que indica el tipo del nuevo objeto de matriz.  
  
 `pClassField`  
 [in] Un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto que representa la clase de un objeto, si crea una matriz de objetos en valores de instancia. Si crea una matriz de objetos simples, este parámetro es un valor null.  
  
 `dwRank`  
 [in] El rango o el número de dimensiones de la matriz.  
  
 `dwDims`  
 [in] Los tamaños de cada dimensión de la matriz.  
  
 `dwLowBounds`  
 [in] El origen de cada dimensión (normalmente 0 o 1).  
  
 `ppObject`  
 [out] Devuelve un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objeto que representa la matriz recién creada. Esto es realmente una [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) objeto.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Llamar a este método para crear un objeto que representa un parámetro de matriz a la función que se representa mediante el [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfaz.  
  
## <a name="see-also"></a>Vea también  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)