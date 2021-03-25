---
description: Obtiene el número de visores personalizados que pueden estar disponibles para esta propiedad.
title: 'IDebugProperty3:: GetCustomViewerCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetCustomViewerCount
helpviewer_keywords:
- IDebugProperty3::GetCustomViewerCount
ms.assetid: dc5bb3e4-dc85-46e4-98fa-c6be8583b985
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a7b74c1ae5a29b785de42295af3260f17655986c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064688"
---
# <a name="idebugproperty3getcustomviewercount"></a>IDebugProperty3::GetCustomViewerCount
Obtiene el número de visores personalizados que pueden estar disponibles para esta propiedad.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetCustomViewerCount(
    ULONG* pcelt
);
```

```csharp
int GetCustomViewerCount(
    out uint pcelt
);
```

## <a name="parameters"></a>Parámetros
`pcelt`\
enuncia El número de visores personalizados disponibles para esta propiedad.

## <a name="return-value"></a>Valor devuelto
Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
Para admitir los visualizadores de tipos, este método reenvía la llamada al método [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) . Si el evaluador de expresiones también admite visores personalizados para el tipo de esta propiedad, este método agrega el número de visores personalizados al valor devuelto.

Para obtener información detallada sobre las diferencias entre los visualizadores de tipos y los visores personalizados, vea [visualizador de tipos y visor personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md).

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra cómo implementar este método para un objeto **CProperty** que expone la interfaz [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) .

```cpp
STDMETHODIMP CProperty::GetCustomViewerCount(ULONG* pcelt)
{
    if (pcelt == NULL)
    {
        return E_POINTER;
    }

    if (GetVisualizerService())
    {
        return m_pIEEVisualizerService->GetCustomViewerCount(pcelt);
    }
    else
    {
        return E_NOTIMPL;
    }
}
```

## <a name="see-also"></a>Consulte también
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)
- [Visualizador de tipo y visor personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
