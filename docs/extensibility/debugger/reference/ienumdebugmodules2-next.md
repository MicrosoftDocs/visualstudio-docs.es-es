---
title: IEnumDebugModules2::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugModules2::Next
helpviewer_keywords:
- IEnumDebugModules2::Next
ms.assetid: 46b7ccad-b07b-4ec0-b3ce-13981ffab7e8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 45d4e1edd97599bf997eb7e0660e9bf60fe53dff
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54937748"
---
# <a name="ienumdebugmodules2next"></a>IEnumDebugModules2::Next
Devuelve el siguiente conjunto de elementos de la enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT Next(  
   ULONG           celt,  
   IDebugModule2** rgelt,  
   ULONG*          pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint            celt,  
   IDebugModule2[] rgelt,  
   ref uint        pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `celt`  
 [in] El número de elementos que se va a recuperar. También especifica el tamaño máximo de la `rgelt` matriz.  
  
 `rgelt`  
 [in, out] Matriz de [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) elementos que deben rellenarse.  
  
 `pceltFetched`  
 [out] Devuelve el número de elementos realmente devueltos en `rgelt`.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si podrían devolverse un menor que el número solicitado de elementos; de lo contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)