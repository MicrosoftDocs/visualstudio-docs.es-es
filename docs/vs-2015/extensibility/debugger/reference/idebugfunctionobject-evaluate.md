---
title: 'IDebugFunctionObject:: Evaluate | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::Evaluate
helpviewer_keywords:
- IDebugFunctionObject::Evaluate method
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e19baa193bb015056b9e5abde4c7a274f635c0c8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179424"
---
# <a name="idebugfunctionobjectevaluate"></a>IDebugFunctionObject::Evaluate
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Llama a la función y devuelve el valor resultante como un objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT Evaluate(   
   IDebugObject** ppParams,  
   DWORD          dwParams,  
   DWORD          dwTimeout,  
   IDebugObject** ppResult  
);  
```  
  
```csharp  
int Evaluate(  
   IDebugObject[]   ppParams,   
   IntPtr           dwParams,   
   uint             dwTimeout,   
   out IDebugObject ppResult  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppParams`  
 de Matriz de objetos [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representan los parámetros de entrada. Cada uno de estos parámetros se creó con uno de los `Create` métodos de la interfaz [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .  
  
 `dwParams`  
 de Número de parámetros de la `ppParams` matriz.  
  
 `dwTimeout`  
 de Especifica el tiempo máximo, en milisegundos, que se va a esperar antes de que se devuelva desde este método. Use `INFINITE` para esperar indefinidamente.  
  
 `ppResult`  
 enuncia Devuelve un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa el valor de la función como un objeto.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método configura y ejecuta una llamada a la función representada por el objeto [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .  
  
## <a name="see-also"></a>Consulte también  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
