---
title: IEnumDebugPrograms2::Skip | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugPrograms2::Skip
helpviewer_keywords: IEnumDebugPrograms2::Skip
ms.assetid: b283858b-b375-4760-bfec-ab37de89958d
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c8c648abbffe82844549cf06813d196cc9cfe67c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugprograms2skip"></a>IEnumDebugPrograms2::Skip
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
 [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)