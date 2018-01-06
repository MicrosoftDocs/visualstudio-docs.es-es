---
title: IDebugBinder3::GetAllAliases | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBinder3::GetAllAliases
helpviewer_keywords: IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 57f644cb0f5cb550e093ccc2691fed91e9f5f4b8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
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