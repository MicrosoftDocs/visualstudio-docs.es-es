---
title: IDebugModule3::LoadSymbols | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugModule3::LoadSymbols
helpviewer_keywords:
- IDebugModule3::LoadSymbols
ms.assetid: 7548c8c1-cbc6-48aa-a845-19058d4a85bb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b84615f4dd4f27e5c8512c985ac234a17506b0b5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53956873"
---
# <a name="idebugmodule3loadsymbols"></a>IDebugModule3::LoadSymbols
Carga los símbolos del módulo actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT LoadSymbols(  
   void  
);  
```  
  
```csharp  
int LoadSymbols();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Si el método se realiza correctamente, devuelve `S_OK`. Si se produce un error, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método carga los símbolos desde la ruta de acceso de búsqueda actual (que se puede modificar mediante una llamada a la [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md) método).  
  
 Este método es preferible el [ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md) método.  
  
## <a name="see-also"></a>Vea también  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)