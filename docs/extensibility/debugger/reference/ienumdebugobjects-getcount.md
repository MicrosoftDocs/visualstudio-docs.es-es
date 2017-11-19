---
title: IEnumDebugObjects::GetCount | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugObjects::GetCount
helpviewer_keywords: IEnumDebugObjects::GetCount method
ms.assetid: 9cbc5db4-03ae-479f-a664-13cad66ad210
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 464eca2473518cdc700e0035289a6b601f6fc5d5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugobjectsgetcount"></a>IEnumDebugObjects::GetCount
Este método devuelve el número de elementos de la enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetCount(  
   [out] ULONG* pcelt  
);  
```  
  
```csharp  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pcelt`  
 [out] Devuelve el número de elementos de la enumeración.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método no forma parte de la interfaz de enumeración de COM habitual que especifica que deban implementarse solo siguiente, clon, Skip y restablecimiento.  
  
## <a name="see-also"></a>Vea también  
 [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)