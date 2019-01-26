---
title: IDebugFunctionPosition2::GetFunctionName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugFunctionPosition2::GetFunctionName
helpviewer_keywords:
- IDebugFunctionPosition2::GetFunctionName
ms.assetid: eb7a348e-a7f5-4f25-be68-80482d5482a8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c942de7697d34e288e0deca28b7f0c2626e62fe
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55007573"
---
# <a name="idebugfunctionposition2getfunctionname"></a>IDebugFunctionPosition2::GetFunctionName
Obtiene el nombre de la función a la que apunta esta posición.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetFunctionName(   
   BSTR* pbstrFunctionName  
);  
```  
  
```csharp  
int GetFunctionName(  
   out string pbstrFunctionName  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pbstrFunctionName`  
 [out] Devuelve el nombre de la función.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)