---
title: IDebugEngine3::SetJustMyCodeState | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fda672cc9d6861520b9da3a894b94d51f4100683
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
Este método indica al motor de depuración acerca de la información de estado de JustMyCode.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT SetJustMyCodeState(  
   BOOL           fUpdate,  
   DWORD          dwModules,  
   JMC_CODE_SPEC* rgJMCSpec  
);  
```  
  
```csharp  
int SetJustMyCodeState(  
   int             fUpdate,   
   uint            dwModules,   
   JMC_CODE_SPEC[] rgJMCSpec  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `fUpdate`  
 [in] Es distinto de cero (`TRUE`) para actualizar la información actual, cero (`FALSE`) para restablecer toda la información (se omite todo lo establecido anteriormente).  
  
 `dwModules`  
 [in] Número de estructuras de información en `rgJMCSpec.`  
  
 `rgJMCSpec`  
 [in] Matriz de [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) las estructuras deben utilizar.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve el código de error.  
  
## <a name="remarks"></a>Comentarios  
 JustMyCode es el concepto de depuración solo el código que pertenece a un usuario y Omitir todo el código intermedio como el código del sistema, incluso si el código fuente está disponible para ese código del sistema.  
  
## <a name="see-also"></a>Vea también  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)   
 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)