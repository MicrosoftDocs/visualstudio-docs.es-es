---
title: IDebugProgram2::Attach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Attach
helpviewer_keywords:
- IDebugProgram2::Attach
ms.assetid: de069fbf-a565-4905-b102-f5658c55aacd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca0d696067cecc042a0fa6eb071a92f18ac229fc
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311404"
---
# <a name="idebugprogram2attach"></a>IDebugProgram2::Attach
Se une al programa.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback
);
```

## <a name="parameters"></a>Parámetros
`pCallback`\
[in] Un [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) objeto que se usará para la notificación de eventos de depuración.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. En la tabla siguiente se muestra algunos posibles códigos de error.

|Valor|Descripción|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|El programa especificado ya está asociado al depurador.|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Se ha producido una infracción de seguridad durante el procedimiento de conexión.|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|No se puede adjuntar un programa de escritorio al depurador.|

## <a name="remarks"></a>Comentarios
 Un motor de depuración (DE) nunca llama a este método para asociar a un programa. Si la DE se ejecuta en el espacio de direcciones del programa, el [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) se llama al método. Si el espacio de direcciones de las ejecuciones DE en el Administrador de depuración de sesión (SDM) el [adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md) se llama al método.

## <a name="see-also"></a>Vea también
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Asociar](../../../extensibility/debugger/reference/idebugengine2-attach.md)