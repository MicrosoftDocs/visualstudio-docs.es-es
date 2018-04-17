---
title: IDebugProgram2::EnumModules | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::EnumModules
helpviewer_keywords:
- IDebugProgram2::EnumModules
ms.assetid: 876ac9da-3b7c-4156-b79a-8f340e9fcea6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9d95deffb687b0d09367e2944bbaff08f3c9b57c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogram2enummodules"></a>IDebugProgram2::EnumModules
Recupera una lista de los módulos que este programa se ha cargado y se está ejecutando.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT EnumModules(   
   IEnumDebugModules2** ppEnum  
);  
```  
  
```csharp  
int EnumModules(   
   out IEnumDebugModules2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppEnum`  
 [out] Devuelve un [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) objeto que contiene una lista de los módulos.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Un módulo es un archivo DLL o ensamblado y normalmente se muestra en el **módulos** ventana de depuración.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)