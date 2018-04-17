---
title: IDebugBinder3::GetAllAliases | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBinder3::GetAllAliases
helpviewer_keywords:
- IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6da1b26b41c80d0417da16f478ef3f6672edd12a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
Este método recupera una lista de alias del programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetAllAliases(  
   UINT          uRequest,  
   IDebugAlias** ppAliases,  
   UINT*         puFetched  
);  
```  
  
```csharp  
int GetAllAliases(  
   uint          uRequest,   
   IDebugAlias[] ppAliases,   
   out uint      puFetched  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `uRequest`  
 [in] El número máximo de alias para devolver (especifica la longitud de la matriz pasada en `ppAliases`).  
  
 `ppAliases`  
 [entrada, salida] Matriz para rellenarla con el alias (si se trata de un valor null y `uRequest` es 0, se devolverá el número de alias que pueden devolverse por `puFetched`).  
  
 `puFetched`  
 [out] Devuelve el número de alias obtenido.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)