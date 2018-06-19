---
title: IEnumDebugErrorBreakpoints2::Skip | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugErrorBreakpoints2::Skip
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2::Skip
ms.assetid: a5a02b38-4e3a-4f0e-b529-f770c3485c8b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3aea378f589346df2b96a1d667bc16930c5a0744
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31123372"
---
# <a name="ienumdebugerrorbreakpoints2skip"></a>IEnumDebugErrorBreakpoints2::Skip
Omite el número especificado de elementos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
```csharp  
int Skip(  
   uint celt  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `celt`  
 [in] Número de elementos que se van a omitir.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si `celt` es mayor que el número de elementos restantes; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Si `celt` especifica un valor mayor que el número de elementos restantes, la enumeración se establece al final y `S_FALSE` se devuelve.  
  
## <a name="see-also"></a>Vea también  
 [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)