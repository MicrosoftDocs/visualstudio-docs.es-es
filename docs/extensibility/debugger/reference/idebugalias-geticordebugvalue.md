---
title: IDebugAlias::GetICorDebugValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 941417adad62b7a09abc1515800a9200baf0bfcb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53939047"
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
Recupera una interfaz de código administrado que representa el valor asociado a este alias.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```csharp  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppUnk`  
 [out] `IUnknown` interfaz que representa el valor asociado a este alias. Esta interfaz se puede consultar el `ICorDebugValue` interfaz.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método solo se aplica a valores administrados (el `ICorDebugValue` está disponible en una interfaz el [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] y se define en el [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] SDK en el archivo cordebug.idl).  
  
## <a name="see-also"></a>Vea también  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)