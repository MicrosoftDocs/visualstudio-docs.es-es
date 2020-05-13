---
title: IDebugProgramProvider2::GetProviderProcessData ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProcessData
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProcessData
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4e958900307f5f7915f58679709c88f80c2abfc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721856"
---
# <a name="idebugprogramprovider2getproviderprocessdata"></a>IDebugProgramProvider2::GetProviderProcessData
Recupera una lista de programas en ejecución de un proceso especificado.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetProviderProcessData(
   PROVIDER_FLAGS         Flags,
   IDebugDefaultPort2*    pPort,
   AD_PROCESS_ID          processId,
   CONST_GUID_ARRAY       EngineFilter,
   PROVIDER_PROCESS_DATA* pProcess
);
```

```csharp
int GetProviderProcessData(
   enum_PROVIDER_FLAGS     Flags,
   IDebugDefaultPort2      pPort,
   AD_PROCESS_ID           ProcessId,
   CONST_GUID_ARRAY        EngineFilter,
   PROVIDER_PROCESS_DATA[] pProcess
);
```

## <a name="parameters"></a>Parámetros
`Flags`\
[en] Una combinación de indicadores de la [enumeración PROVIDER_FLAGS.](../../../extensibility/debugger/reference/provider-flags.md) Los siguientes indicadores son típicos para esta llamada:

|Marca|Descripción|
|----------|-----------------|
|`PFLAG_REMOTE_PORT`|El autor de la llamada se está ejecutando en un equipo remoto.|
|`PFLAG_DEBUGGEE`|El autor de la llamada se está depurando actualmente (se devolverá información adicional sobre el cálculo de referencias para cada nodo).|
|`PFLAG_ATTACHED_TO_DEBUGGEE`|El autor de la llamada estaba asociado al depurador, pero no lo inició.|
|`PFLAG_GET_PROGRAM_NODES`|El autor de la llamada pide que se devuelva una lista de nodos del programa.|

`pPort`\
[en] El puerto en el que se ejecuta el proceso de llamada.

`processId`\
[en] Una [estructura AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) que contiene el ID del proceso que contiene el programa en cuestión.

`EngineFilter`\
[en] Una matriz de GUID para motores de depuración asignados para depurar este proceso (estos se utilizarán para filtrar los programas que realmente se devuelven en función de lo que admiten los motores suministrados; si no se especifica ningún motor, se devolverán todos los programas).

`pProcess`\
[fuera] Una [estructura PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) que se rellena con la información solicitada.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Este método normalmente es llamado por un proceso para obtener una lista de programas que se ejecutan en ese proceso. La información devuelta es una lista de [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objetos.

## <a name="see-also"></a>Vea también
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
