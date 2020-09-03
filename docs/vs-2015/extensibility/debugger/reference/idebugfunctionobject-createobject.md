---
title: 'IDebugFunctionObject:: CreateObject | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObject
helpviewer_keywords:
- IDebugFunctionObject::CreateObject method
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 08483d5f015af7088eb5968a5bf6358ce5065579
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179469"
---
# <a name="idebugfunctionobjectcreateobject"></a>IDebugFunctionObject::CreateObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crea un objeto utilizando un constructor.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 de Objeto [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) que representa el constructor del objeto que se va a crear.  
  
 `dwArgs`  
 de Número de parámetros de la `pArg` matriz. Representa el número de parámetros pasados al constructor.  
  
 `pArg`  
 de Matriz de objetos [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representan los parámetros pasados al constructor.  
  
 `ppObject`  
 enuncia Devuelve un `IDebugObject` que representa el objeto recién creado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Llame a este método para crear un objeto que represente una instancia de una clase (u otro tipo complejo que requiera un constructor) que sea un parámetro de la función representada por la interfaz [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .  
  
 Si el parámetro de objeto no requiere un constructor, llame al método [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md) .  
  
## <a name="see-also"></a>Consulte también  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)   
 [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)
