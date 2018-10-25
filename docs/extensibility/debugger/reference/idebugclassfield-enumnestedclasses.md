---
title: IDebugClassField::EnumNestedClasses | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugClassField::EnumNestedClasses
helpviewer_keywords:
- IDebugClassField::EnumNestedClasses method
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a313e27c3dcbca0136b00bfb789e444174474369
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49937536"
---
# <a name="idebugclassfieldenumnestedclasses"></a>IDebugClassField::EnumNestedClasses
Crea un enumerador para las clases anidadas de esta clase.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT EnumNestedClasses(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumNestedClasses(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppEnum`  
 [out] Devuelve un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que representa la lista de las clases anidadas. Devuelve un valor null si no hay ninguna clase anidada.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK o devuelve S_FALSE si no hay ninguna clase anidada. De lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Cada elemento de la enumeración es un [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) objeto que describe una clase anidada.  
  
 Una clase anidada es una clase definida dentro de otra clase. Por ejemplo:  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 El [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) enumeración contendría un objeto que representa el `NestedClass` clase.  
  
## <a name="see-also"></a>Vea también  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)