---
title: IDebugClassField::EnumNestedEnums | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugClassField::EnumNestedEnums
helpviewer_keywords:
- IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2ea28f2a455d3528f083ba2acb2e9e4ad8989319
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31103034"
---
# <a name="idebugclassfieldenumnestedenums"></a>IDebugClassField::EnumNestedEnums
Crea un enumerador para los enumeradores anidados de esta clase.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT EnumNestedEnums(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumNestedEnums(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppEnum`  
 [out] Devuelve un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que representa la lista de enumeraciones anidadas. Devuelve un valor null si no hay ningún enumeraciones anidadas.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK o devuelva S_FALSE si no hay ningún enumeradores anidados. De lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Cada elemento de la enumeración es un [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) objeto que describe una enumeración anidada.  
  
 Una enumeración declarada dentro de una clase se considera una enumeración anidada. Por ejemplo, dado:  
  
```  
class RootClass {  
   enum NestedEnum { EnumValue = 0 }  
};  
```  
  
 El `EnumNestedEnums` método devolvería un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que contiene un [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) objeto que representa el `NestedEnum` enumeración.  
  
## <a name="see-also"></a>Vea también  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)