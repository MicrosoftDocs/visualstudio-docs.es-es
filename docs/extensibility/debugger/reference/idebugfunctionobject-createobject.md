---
title: IDebugFunctionObject::CreateObject | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugFunctionObject::CreateObject
helpviewer_keywords:
- IDebugFunctionObject::CreateObject method
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 15b41cc5ff9f60143cdbf006005358cb86eb7f30
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugfunctionobjectcreateobject"></a>IDebugFunctionObject::CreateObject
Crea un objeto mediante un constructor.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT CreateObject(   
   IDebugFunctionObject* pConstructor,  
   DWORD                 dwArgs,  
   IDebugObject*         pArgs[],  
   IDebugObject**        ppObject  
);  
```  
  
```csharp  
int CreateObject(  
   IDebugFunctionObject pConstructor,   
   uint                 dwArgs,   
   IDebugObject[]       pArgs,   
   out IDebugObject     ppObject  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pConstructor`  
 [in] Un [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) objeto que representa el constructor del objeto que se creará.  
  
 `dwArgs`  
 [in] El número de parámetros en el `pArg` matriz. Representa el número de parámetros pasados al constructor.  
  
 `pArg`  
 [in] Una matriz de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objetos que representan los parámetros pasados al constructor.  
  
 `ppObject`  
 [out] Devuelve un `IDebugObject` que representa el objeto recién creado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Llamar a este método para crear un objeto que representa una instancia de una clase (u otro tipo complejo que requiere un constructor) que es un parámetro a la función que se representa mediante el [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfaz.  
  
 Si el parámetro de objeto no requiere un constructor, llame a la [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md) método.  
  
## <a name="see-also"></a>Vea también  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)   
 [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)