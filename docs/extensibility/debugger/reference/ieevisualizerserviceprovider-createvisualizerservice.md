---
title: IEEVisualizerServiceProvider::CreateVisualizerService ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e05677122b7d4e4eb025a9382ede1509374de894
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717906"
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
Este método crea un servicio de visualizador.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT CreateVisualizerService(
   IDebugBinder*              binder,
   IDebugSymbolProvider*      pSymProv,
   IDebugAddress*             pAddress,
   IEEVisualizerDataProvider* dataProvider,
   IEEVisualizerService**     ppService
);
```

```csharp
int CreateVisualizerService(
   IDebugBinder binder,
   IDebugSymbolProvider      pSymProv,
   IDebugAddress             pAddress,
   IEEVisualizerDataProvider dataProvider,
   out IEEVisualizerService  ppService
);
```

## <a name="parameters"></a>Parámetros
`binder`\
[en] El objeto [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) pasado a [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md).

`pSymProv`\
[en] El objeto [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) pasado a `IDebugParsedExpression::EvaluateSync`.

`pAddress`\
[en] El objeto [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) pasado a `IDebugParsedExression::EvaluateSync`.

`dataProvider`\
[en] Objeto que implementa la interfaz [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) (proporcionada por el evaluador de expresiones).

`ppService`\
[fuera] El servicio creado.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Los `binder` `pSymProv`parámetros `pAddress` , , y `IDebugParsedExpression::EvaluateSync` se pasaron al método. `CreateVisualizerService`debe llamarse solo `IDebugParsedExpression::EvaluateSync` como parte de la compatibilidad de un evaluador de expresiones para visualizadores de tipos.

## <a name="see-also"></a>Vea también
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
