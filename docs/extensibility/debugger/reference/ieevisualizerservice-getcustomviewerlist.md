---
title: 'IEEVisualizerService:: GetCustomViewerList | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerService::GetCustomViewerList
helpviewer_keywords:
- IEEVisualizerService::GetCustomViewerList method
ms.assetid: 249d26ca-914f-43af-a400-8162477223f4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2ba63a1f27e043ca114a3b954adfe403b60283ca
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907811"
---
# <a name="ieevisualizerservicegetcustomviewerlist"></a>IEEVisualizerService::GetCustomViewerList
Este método devuelve una lista de visualizadores de tipos que este servicio conoce.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetCustomViewerList(
   ULONG                celtSkip,
   ULONG                celtRequested,
   DEBUG_CUSTOM_VIEWER* rgViewers,
   ULONG*               pceltFetched
);
```

```csharp
int GetCustomViewerList(
   uint                  celtSkip,
   uint                  celtRequested,
   DEBUG_CUSTOM_VIEWER[] rgViewers,
   out uint              pceltFetched
);
```

## <a name="parameters"></a>Parámetros
`celtSkip`\
de Número de visualizadores que se van a omitir.

`celRequested`\
de Número de visualizadores que se van a recuperar (también especifica el tamaño de la `rgViewers` matriz).

`rgViewers`\
[in, out] Matriz de estructuras de [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) que se van a rellenar.

`pceltFetched`\
enuncia Número de visualizadores realmente recuperados.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Notas
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) pasa la solicitud a este método como parte de su compatibilidad con los visualizadores de tipos. Si el evaluador de expresiones también proporciona visores personalizados para el mismo tipo, puede anexar a la lista las estructuras [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) rellenadas correctamente para esos visores personalizados. Asegúrese de que [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) refleja esos visores adicionales.

 Vea [visualizador de tipos y visor personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) para obtener más información sobre las diferencias entre los visualizadores y los visores.

## <a name="see-also"></a>Vea también
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)
- [Visualizador de tipo y visor personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
