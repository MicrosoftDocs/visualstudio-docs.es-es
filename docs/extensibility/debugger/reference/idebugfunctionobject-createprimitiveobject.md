---
title: IDebugFunctionObject::CreatePrimitiveObject | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugFunctionObject::CreatePrimitiveObject
helpviewer_keywords: IDebugFunctionObject::CreatePrimitiveObject method
ms.assetid: 6e9dc8b6-b4e1-4abf-b6e0-e885910775bc
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5c612c9bc2b535c61322364690f18699218365c9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugfunctionobjectcreateprimitiveobject"></a>IDebugFunctionObject::CreatePrimitiveObject
Crea un objeto de datos primitivo, como un entero simple.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
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
 [in] Un valor de la [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) enumeración que representa el tipo de primitiva a crear.  
  
 `ppObject`  
 [out] Devuelve un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa el objeto recién creado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Llamar a este método para crear un objeto que representa un objeto primitivo que es un parámetro a la función que se representa mediante el [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfaz. Por ejemplo, si la cadena de expresión es "myString(5)", es lo que este método se utiliza para crear un objeto que representa el entero 5.  
  
## <a name="see-also"></a>Vea también  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)