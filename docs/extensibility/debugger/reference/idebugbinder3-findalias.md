---
title: IDebugBinder3::FindAlias | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e68038f6e00c2a04f4c96f5f9d93fc4919d2fd09
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102127"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
Este método busca un alias, le asignado un nombre. Realiza una búsqueda en todos los alias en el programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT FindAlias(  
   LPCOLESTR     pcstrName,  
   IDebugAlias** ppAlias  
);  
```  
  
```csharp  
int FindAlias(  
   string          pcstrName,  
   out IDebugAlias ppAlias  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pcstrName`  
 [in] Nombre de alias para buscar.  
  
 `ppAlias`  
 [out] (Si existe) se encontró un alias representado por la [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) interfaz.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` (si no se encuentra el alias) o un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método inicializa el objeto de destino en null antes de llamar a; a continuación, comprueba que un valor null posteriormente determinar si se permite o no se encontró el alias.  
  
## <a name="see-also"></a>Vea también  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)