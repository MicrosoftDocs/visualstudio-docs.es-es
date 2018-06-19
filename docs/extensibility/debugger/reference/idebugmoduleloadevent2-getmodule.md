---
title: IDebugModuleLoadEvent2::GetModule | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugModuleLoadEvent2::GetModule
helpviewer_keywords:
- IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b6188ba6842a922fa0758a21c0f496f50889f8b3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31114536"
---
# <a name="idebugmoduleloadevent2getmodule"></a>IDebugModuleLoadEvent2::GetModule
Obtiene el módulo que se va a cargar o descargar.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetModule(   
   IDebugModule2** pModule,  
   BSTR*           pbstrDebugMessage,  
   BOOL*           pbLoad  
);  
```  
  
```csharp  
int GetModule(   
   out IDebugModule2 pModule,  
   ref string        pbstrDebugMessage,  
   ref int           pbLoad  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pModule`  
 [out] Devuelve un [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) objeto que representa el módulo que se carga o descarga.  
  
 `pbstrDebugMessage`  
 [entrada, salida] Devuelve un mensaje opcional que describe este evento. Si este parámetro es un valor null, no se solicita ningún mensaje.  
  
 `pbLoad`  
 [entrada, salida] Es distinto de cero (`TRUE`) si el módulo se carga y cero (`FALSE`) si está descargando el módulo. Si este parámetro es un valor null, no se solicita ningún estado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)