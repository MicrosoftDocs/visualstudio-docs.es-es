---
description: Recupera una lista de programas en ejecución de un proceso especificado.
title: 'IDebugProgramProvider2:: GetProviderProcessData | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProcessData
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProcessData
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad388a552a34ebd49819987a20f4876193a96658
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071485"
---
# <a name="idebugprogramprovider2getproviderprocessdata"></a>IDebugProgramProvider2::GetProviderProcessData
Recupera una lista de programas en ejecución de un proceso especificado.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetProviderProcessData(
   PROVIDER_FLAGS         Flags,
   IDebugDefaultPort2*    pPort,
   AD_PROCESS_ID          processId,
   CONST_GUID_ARRAY       EngineFilter,
   PROVIDER_PROCESS_DATA* pProcess
);
```

```csharp
int GetProviderProcessData(
   enum_PROVIDER_FLAGS     Flags,
   IDebugDefaultPort2      pPort,
   AD_PROCESS_ID           ProcessId,
   CONST_GUID_ARRAY        EngineFilter,
   PROVIDER_PROCESS_DATA[] pProcess
);
```

## <a name="parameters"></a>Parámetros
`Flags`\
de Combinación de marcas de la enumeración [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) . Las marcas siguientes son típicas para esta llamada:

|Marca|Descripción|
|----------|-----------------|
|`PFLAG_REMOTE_PORT`|El autor de la llamada se está ejecutando en la máquina remota.|
|`PFLAG_DEBUGGEE`|El autor de la llamada se está depurando actualmente (se devolverá información adicional sobre el cálculo de referencias para cada nodo).|
|`PFLAG_ATTACHED_TO_DEBUGGEE`|El autor de la llamada estaba asociado pero no lo inició el depurador.|
|`PFLAG_GET_PROGRAM_NODES`|El autor de la llamada solicita una lista de nodos de programa que se devolverán.|

`pPort`\
de El puerto en el que se está ejecutando el proceso de llamada.

`processId`\
de Estructura [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) que contiene el identificador del proceso que contiene el programa en cuestión.

`EngineFilter`\
de Matriz de GUID para los motores de depuración asignados para depurar este proceso (se utilizarán para filtrar los programas que se devuelven realmente en función de lo que admitan los motores suministrados; si no se especifica ningún motor, se devolverán todos los programas).

`pProcess`\
enuncia [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) estructura que se rellena con la información solicitada.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Normalmente, un proceso llama a este método para obtener una lista de los programas que se ejecutan en ese proceso. La información devuelta es una lista de objetos [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) .

## <a name="see-also"></a>Consulte también
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
