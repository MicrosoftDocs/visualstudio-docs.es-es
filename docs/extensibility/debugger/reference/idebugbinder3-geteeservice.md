---
title: IDebugBinder3::GetEEService | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetEEService
helpviewer_keywords:
- IDebugBinder3::GetEEService method
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: eaaaf52a0a577d8b802540ca9b4ae11ab9aa1dbd
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/14/2019
ms.locfileid: "65614900"
---
# <a name="idebugbinder3geteeservice"></a>IDebugBinder3::GetEEService
Este método devuelve un servicio solicitado.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetEEService(
   [in] GUID        vendor,
   [in] GUID        language,
   [in] GUID        iid,
   [out] IUnknown** ppService
);
```

```csharp
Int GetEEService(
   Guid       vendor,
   Guid       language,
   Guid       iid,
   out object ppService
);
```

## <a name="parameters"></a>Parámetros
`vendor`\
[in] `GUID` de un proveedor (un valor null es aceptable).

`language`\
[in] `GUID` de un idioma (un valor null es aceptable).

`iid`\
[in] `IID` del servicio que se va a obtener.

`ppService`\
[out] Interfaz para el servicio solicitado.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Pase el `IID` para el [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md) interfaz (`IID_IEEVisualizerServiceProvider`) para ver si el servicio de tipo visualizador está disponible. Si es así, puede obtener el evaluador de expresiones el [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) interfaz para admitir los visualizadores de tipo. Consulte [visualización y ver datos](../../../extensibility/debugger/visualizing-and-viewing-data.md) para obtener más información.

## <a name="see-also"></a>Vea también
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [Visualización de datos](../../../extensibility/debugger/visualizing-and-viewing-data.md)