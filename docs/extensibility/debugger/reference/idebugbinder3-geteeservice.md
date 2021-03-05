---
description: Este método devuelve un servicio solicitado.
title: 'IDebugBinder3:: GetEEService | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetEEService
helpviewer_keywords:
- IDebugBinder3::GetEEService method
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5ecd439ba1af40a54512c3ef15efb4728c8c54a1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167677"
---
# <a name="idebugbinder3geteeservice"></a>IDebugBinder3::GetEEService
Este método devuelve un servicio solicitado.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetEEService(
   [in] GUID        vendor,
   [in] GUID        language,
   [in] GUID        iid,
   [out] IUnknown** ppService
);
```

```csharp
Int GetEEService(
   Guid       vendor,
   Guid       language,
   Guid       iid,
   out object ppService
);
```

## <a name="parameters"></a>Parámetros
`vendor`\
[in] `GUID` de un proveedor (es aceptable un valor nulo).

`language`\
[in] `GUID` de un lenguaje (es aceptable un valor null).

`iid`\
[in] `IID` del servicio que se va a obtener.

`ppService`\
enuncia Interfaz para el servicio solicitado.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Pase `IID` para la interfaz [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md) ( `IID_IEEVisualizerServiceProvider` ) para ver si el servicio del visualizador de tipos está disponible. En ese caso, el evaluador de expresiones puede obtener la interfaz [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) para admitir los visualizadores de tipos. Vea [visualizar y ver datos](../../../extensibility/debugger/visualizing-and-viewing-data.md) para obtener más información.

## <a name="see-also"></a>Consulte también
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [Visualización de datos](../../../extensibility/debugger/visualizing-and-viewing-data.md)
