---
title: IDebugArrayObject::GetRank | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugArrayObject::GetRank
helpviewer_keywords:
- IDebugArrayObject::GetRank method
ms.assetid: 9948551a-e334-4ff6-979c-08dab633b9b6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e76e8d3f39ab5f86ba15db7fd00c4b45fc93c9c2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugarrayobjectgetrank"></a>IDebugArrayObject::GetRank
Obtiene el rango de la matriz, es decir, el número de dimensiones.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetRank(   
   DWORD* pdwRank  
);  
```  
  
```csharp  
int GetRank(  
   out uint pdwRank  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pdwRank`  
 [out] Devuelve el rango.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Use la [GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md) método para recuperar el tamaño de cada dimensión del objeto array.  
  
## <a name="see-also"></a>Vea también  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)