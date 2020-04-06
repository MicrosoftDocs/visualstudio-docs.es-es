---
title: IDebugProcess2::Attach ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Attach
helpviewer_keywords:
- IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fb6ea896285c784021402400597ba168f6ccf716
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724194"
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
Asocia el administrador de depuración de sesión (SDM) al proceso.

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

## <a name="parameters"></a>Parámetros
`pCallback`\
[en] Un [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) objeto que se utiliza para la notificación de eventos de depuración.

`rgguidSpecificEngines`\
[en] Matriz de GUID de motores de depuración que se utilizarán para depurar programas que se ejecutan en el proceso. Este parámetro puede ser un valor nulo. Para obtener información detallada, vea la sección Comentarios de.

`celtSpecificEngines`\
[en] El número de motores `rgguidSpecificEngines` de depuración de `rghrEngineAttach` la matriz y el tamaño de la matriz.

`rghrEngineAttach`\
[adentro, fuera] Matriz de códigos HRESULT devueltos por los motores de depuración. El tamaño de esta matriz `celtSpecificEngines` se especifica en el parámetro. Cada código suele `S_OK` ser `S_ATTACH_DEFERRED`. Este último indica que el DE está actualmente unido a ningún programa.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. En la tabla siguiente se muestran otros valores posibles.

|Value|Descripción|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|El proceso especificado ya está asociado al depurador.|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Se ha producido una infracción de seguridad durante el procedimiento de asociación.|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|No se puede asociar un proceso de escritorio al depurador.|

## <a name="remarks"></a>Observaciones
 La asociación a un proceso asocia el SDM a todos los programas que se ejecutan en `rgguidSpecificEngines` ese proceso que pueden ser depurados por los motores de depuración (DE) especificados en la matriz. Establezca `rgguidSpecificEngines` el parámetro en un `GUID_NULL` valor nulo o incluya en la matriz que se va a adjuntar a todos los programas del proceso.

 Todos los eventos de depuración que se producen en el proceso se envían al objeto [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) especificado. Este `IDebugEventCallback2` objeto se proporciona cuando el SDM llama a este método.

## <a name="see-also"></a>Vea también
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
