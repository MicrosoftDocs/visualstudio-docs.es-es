---
title: IDebugProcess2::Attach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Attach
helpviewer_keywords:
- IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f700a6f6ff06fb37660419c46a394a0449d976bf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62871294"
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
El Administrador de depuración de la sesión (SDM) se asocia al proceso.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback,
   GUID*                 rgguidSpecificEngines,
   DWORD                 celtSpecificEngines,
   HRESULT*              rghrEngineAttach
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback,
   Guid[]               rgguidSpecificEngines,
   uint                 celtSpecificEngines,
   int[]                rghrEngineAttach
);
```

#### <a name="parameters"></a>Parámetros
 `pCallback`

 [in] Un [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) objeto que se usa para la notificación de eventos de depuración.

 `rgguidSpecificEngines`

 [in] Una matriz de GUID de motores de depuración que se va a usar para depurar programas que se ejecutan en el proceso. Este parámetro puede ser un valor null. Para obtener más información, vea la sección Comentarios.

 `celtSpecificEngines`

 [in] El número de depuración motores en el `rgguidSpecificEngines` matriz y el tamaño de la `rghrEngineAttach` matriz.

 `rghrEngineAttach`

 [in, out] Una matriz de códigos HRESULT devuelto por los motores de depuración. El tamaño de esta matriz se especifica en el `celtSpecificEngines` parámetro. Cada código es normalmente `S_OK` o `S_ATTACH_DEFERRED`. Estos últimos indican que la DE actualmente está conectada a ningún programa.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. En la tabla siguiente se muestra otros posibles valores.

|Valor|Descripción|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|El proceso especificado ya está asociado al depurador.|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Se ha producido una infracción de seguridad durante el procedimiento de conexión.|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|No se puede adjuntar un proceso de escritorio al depurador.|

## <a name="remarks"></a>Comentarios
 Adjuntar a un proceso adjunta el SDM en todos los programas que se ejecutan en el proceso que se puede depurar los motores de depuración (DE) especificado en el `rgguidSpecificEngines` matriz. Establecer el `rgguidSpecificEngines` parámetro a un valor null de valor o incluir `GUID_NULL` en la matriz para adjuntar a todos los programas en el proceso.

 Todos los eventos de depuración que se producen en el proceso se envían a la determinada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) objeto. Esto `IDebugEventCallback2` se proporciona un objeto cuando el SDM llama a este método.

## <a name="see-also"></a>Vea también
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)