---
title: IDebugClassField::GetEnclosingClass | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9e6b2cfae694d0d95f70b2251efc66764df1b539
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62922783"
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
