---
title: IDebugClassField::GetEnclosingClass | Documentos de Microsoft
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
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 69c9359fe8d9f337a09e0ab3fae4f92b0fc4c264
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49924753"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtiene la clase que contiene esta clase.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 [out] Devuelve un [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) la clase de objeto que representa el envolvente. Devuelve un valor null si no hay ninguna clase envolvente.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Si la clase representada por este [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) objeto es una clase anidada, la `ppClassField` parámetro devuelve un `IDebugClassField` clase de objeto que representa el envolvente. Por ejemplo, dada esta definición de clase:  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 Una llamada a la `GetEnclosingClass` método en el `IDebugClassField` objeto que representa el `NestedClass` clase devuelve una `IDebugClassField` objeto que representa la clase `RootClass`.  
  
## <a name="see-also"></a>Vea también  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)

