---
title: IDebugClassField::GetEnclosingClass | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6cd73955835f8aff0047995a690da03e5ab0305d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
Obtiene la clase que contiene esta clase.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetEnclosingClass(   
   IDebugClassField** ppClassField  
);  
```  
  
```csharp  
int GetEnclosingClass(  
   out IDebugClassField ppClassField  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppClassField`  
 [out] Devuelve un [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) clase de objeto que representa el envolvente. Devuelve un valor null si no hay ninguna clase envolvente.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Si la clase representada por este [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) objeto es una clase anidada, la `ppClassField` parámetro devuelve un `IDebugClassField` clase de objeto que representa el envolvente. Por ejemplo, dada esta definición de clase:  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 Llamar a la `GetEnclosingClass` método en el `IDebugClassField` objeto que representa el `NestedClass` clase devuelve una `IDebugClassField` objeto que representa la clase `RootClass`.  
  
## <a name="see-also"></a>Vea también  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)