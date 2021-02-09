---
title: 'IDebugProcess2:: Attach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Attach
helpviewer_keywords:
- IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 462b2299a658359e81fc3641e590b95ab183a24e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874183"
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
Adjunta el administrador de depuración de la sesión (SDM) al proceso.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback,
   GUID*                 rgguidSpecificEngines,
   DWORD                 celtSpecificEngines,
   HRESULT*              rghrEngineAttach
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback,
   Guid[]               rgguidSpecificEngines,
   uint                 celtSpecificEngines,
   int[]                rghrEngineAttach
);
```

## <a name="parameters"></a>Parámetros
`pCallback`\
de Un objeto [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) que se usa para la notificación de eventos de depuración.

`rgguidSpecificEngines`\
de Matriz de GUID de los motores de depuración que se va a utilizar para depurar programas que se ejecutan en el proceso. Este parámetro puede ser un valor null. Para obtener información detallada, vea la sección Comentarios de.

`celtSpecificEngines`\
de El número de motores de depuración en la `rgguidSpecificEngines` matriz y el tamaño de la `rghrEngineAttach` matriz.

`rghrEngineAttach`\
[in, out] Matriz de códigos HRESULT devueltos por los motores de depuración. El tamaño de esta matriz se especifica en el `celtSpecificEngines` parámetro. Cada código suele ser `S_OK` o `S_ATTACH_DEFERRED` . Esto último indica que el DE está adjuntado actualmente a ningún programa.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. En la tabla siguiente se muestran otros valores posibles.

|Value|Descripción|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|El proceso especificado ya está asociado al depurador.|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Se ha producido una infracción de seguridad durante el procedimiento de asociación.|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|No se puede adjuntar un proceso de escritorio al depurador.|

## <a name="remarks"></a>Notas
 Al asociar a un proceso, se adjunta el SDM a todos los programas que se ejecutan en ese proceso y que se pueden depurar mediante los motores de depuración (DE) especificados en la `rgguidSpecificEngines` matriz. Establezca el `rgguidSpecificEngines` parámetro en un valor nulo o inclúyalo `GUID_NULL` en la matriz para adjuntar todos los programas del proceso.

 Todos los eventos de depuración que se producen en el proceso se envían al objeto [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) especificado. Este `IDebugEventCallback2` objeto se proporciona cuando el SDM llama a este método.

## <a name="see-also"></a>Vea también
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
