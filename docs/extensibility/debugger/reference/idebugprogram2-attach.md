---
title: 'IDebugProgram2:: Attach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Attach
helpviewer_keywords:
- IDebugProgram2::Attach
ms.assetid: de069fbf-a565-4905-b102-f5658c55aacd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f42aa8ff646a62f7314887df4b38c648e2d84b31
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931453"
---
# <a name="idebugprogram2attach"></a>IDebugProgram2::Attach
Se asocia al programa.

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
de Objeto [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) que se va a usar para la notificación de eventos de depuración.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. En la tabla siguiente se muestran algunos códigos de error posibles.

|Value|Descripción|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|El programa especificado ya está asociado al depurador.|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Se ha producido una infracción de seguridad durante el procedimiento de asociación.|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|No se puede adjuntar un programa de escritorio al depurador.|

## <a name="remarks"></a>Notas
 Un motor DE depuración (DE) nunca llama a este método para asociar a un programa. Si el DE se ejecuta en el espacio de direcciones del programa, se llama al método [alattach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) . Si el DE se ejecuta en el espacio de direcciones del administrador de depuración de la sesión (SDM), se llama al método [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) .

## <a name="see-also"></a>Vea también
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md)
