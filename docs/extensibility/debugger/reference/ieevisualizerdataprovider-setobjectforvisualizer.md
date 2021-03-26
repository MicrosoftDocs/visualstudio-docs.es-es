---
description: Este método cambia el objeto que representa el visualizador.
title: 'IEEVisualizerDataProvider:: SetObjectForVisualizer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2e0a59c10293d5d8cc13d46b625a7b43136cb71b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091804"
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
Este método cambia el objeto que representa el visualizador.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT SetObjectForVisualizer(
   IDebugObject*  pNewObject,
   BSTR*          error,
   IDebugObject** pException
);
```

```csharp
int SetObjectForVisualizer(
   IDebugObject     pNewObject,
   out string       error,
   out IDebugObject pException
);
```

## <a name="parameters"></a>Parámetros
`pNewObject`\
de Objeto que se va a establecer.

`error`\
enuncia Si se produjo un error al establecer el objeto, esta cadena contiene el mensaje de error.

`pException`\
enuncia Si se produjo un error, este objeto contiene la información de la excepción.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Depende del implementador determinar cómo se devuelve la información de error. Sin embargo, es posible que algunos autores de llamadas solo tengan que ver si se devolvió un objeto de excepción para saber que se ha producido un error, por lo que este método siempre debería devolver un objeto de excepción si se produjo un error. También se debe proporcionar la cadena de error en caso de que el autor de la llamada quiera usarla.

## <a name="see-also"></a>Consulte también
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
