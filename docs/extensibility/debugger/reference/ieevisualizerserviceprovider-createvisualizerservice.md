---
description: Este método crea un servicio del visualizador.
title: 'IEEVisualizerServiceProvider:: CreateVisualizerService | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6f8695b578b1a069fd8fe8fa2afdd3a7c21ccd92
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086760"
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
Este método crea un servicio del visualizador.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT CreateVisualizerService(
   IDebugBinder*              binder,
   IDebugSymbolProvider*      pSymProv,
   IDebugAddress*             pAddress,
   IEEVisualizerDataProvider* dataProvider,
   IEEVisualizerService**     ppService
);
```

```csharp
int CreateVisualizerService(
   IDebugBinder binder,
   IDebugSymbolProvider      pSymProv,
   IDebugAddress             pAddress,
   IEEVisualizerDataProvider dataProvider,
   out IEEVisualizerService  ppService
);
```

## <a name="parameters"></a>Parámetros
`binder`\
de El objeto [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) pasado a [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md).

`pSymProv`\
de Objeto [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) pasado a `IDebugParsedExpression::EvaluateSync` .

`pAddress`\
de Objeto [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) pasado a `IDebugParsedExression::EvaluateSync` .

`dataProvider`\
de Objeto que implementa la interfaz [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) (proporcionada por el evaluador de expresiones).

`ppService`\
enuncia El servicio creado.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 `binder` `pSymProv` `pAddress` Se pasaron todos los parámetros, y al `IDebugParsedExpression::EvaluateSync` método. `CreateVisualizerService` solo se debe llamar desde `IDebugParsedExpression::EvaluateSync` como parte de la compatibilidad de un evaluador de expresiones con los visualizadores de tipo.

## <a name="see-also"></a>Consulte también
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
