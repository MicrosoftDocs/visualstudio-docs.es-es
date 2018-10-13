---
title: IDebugFunctionObject::CreateArrayObject | Microsoft Docs
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
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eab7fb87d6bdccfcf5896a21c870c963a0fa0332
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49248123"
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crea un objeto de matriz. Esta matriz puede contener a cualquier tipo primitivo o valores de la instancia del objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 [in] Un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto que representa la clase de un objeto, si los valores de instancia a crear una matriz de objetos. Si crea una matriz de objetos primitivos, este parámetro es un valor null.  
  
 `dwRank`  
 [in] El rango o el número de dimensiones de la matriz.  
  
 `dwDims`  
 [in] Los tamaños de cada dimensión de la matriz.  
  
 `dwLowBounds`  
 [in] El origen de cada dimensión (normalmente 0 o 1).  
  
 `ppObject`  
 [out] Devuelve un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objeto que representa la matriz recién creada. Esto es realmente un [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) objeto.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Llame a este método para crear un objeto que representa un parámetro de matriz a la función representada por el [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfaz.  
  
## <a name="see-also"></a>Vea también  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)

