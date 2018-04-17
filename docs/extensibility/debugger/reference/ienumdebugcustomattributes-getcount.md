---
title: IEnumDebugCustomAttributes::GetCount | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumCustomAttributes::GetCount
helpviewer_keywords:
- IEnumDebugCustomAttributes::GetCount
ms.assetid: fafe826f-4ebf-4572-b2a3-d5dd2916c12f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 223f453f427fe90764262bac55f2591d4fdf5646
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugcustomattributesgetcount"></a>IEnumDebugCustomAttributes::GetCount
Obtiene el número de atributos personalizados de un enumerador.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetCount(   
   ULONG* pcelt  
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
 Este método no forma parte de la interfaz de enumeración de COM habitual que especifica que solamente `Next`, `Clone`, `Skip`, y `Reset` deban implementarse.  
  
## <a name="see-also"></a>Vea también  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)