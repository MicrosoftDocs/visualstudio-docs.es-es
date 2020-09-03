---
title: 'IDebugFunctionObject:: CreatePrimitiveObject | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreatePrimitiveObject
helpviewer_keywords:
- IDebugFunctionObject::CreatePrimitiveObject method
ms.assetid: 6e9dc8b6-b4e1-4abf-b6e0-e885910775bc
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3531483c113c37587b253bed90a9985541b2e526
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179444"
---
# <a name="idebugfunctionobjectcreateprimitiveobject"></a>IDebugFunctionObject::CreatePrimitiveObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crea un objeto de datos primitivo, como un entero simple.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT CreatePrimitiveObject(   
   OBJECT_TYPE    ot,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int CreatePrimitiveObject(  
   enum_OBJECT_TYPE ot,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ot`  
 de Un valor de la enumeración [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) que representa el tipo de primitivo que se va a crear.  
  
 `ppObject`  
 enuncia Devuelve un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa el objeto recién creado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Observaciones  
 Llame a este método para crear un objeto que represente un objeto primitivo que sea un parámetro de la función representada por la interfaz [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) . Por ejemplo, si la cadena de expresión es "String (5)", este método se utilizaría para crear un objeto que represente el entero 5.  
  
## <a name="see-also"></a>Consulte también  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
