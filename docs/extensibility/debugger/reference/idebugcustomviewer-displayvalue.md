---
description: Se llama a este método para mostrar el valor especificado.
title: IDebugCustomViewer::D isplayValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer::DisplayValue
helpviewer_keywords:
- IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 11a93ba7a3367a9ff61debfe338c349549ee429d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077582"
---
# <a name="idebugcustomviewerdisplayvalue"></a>IDebugCustomViewer::DisplayValue
Se llama a este método para mostrar el valor especificado.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT DisplayValue(
   HWND             hwnd,
   DWORD            dwID,
   IUnknown *       pHostServices,
   IDebugProperty3* pDebugProperty);
);
```

```csharp
int DisplayValue(
   IntPtr          hwnd,
   uint            dwID,
   object          pHostServices,
   IDebugProperty3 pDebugProperty
);
```

## <a name="parameters"></a>Parámetros
`hwnd`\
de Ventana primaria

`dwID`\
de IDENTIFICADOR de los visores personalizados que admiten más de un tipo.

`pHostServices`\
[in] Reservado. Siempre se establece en NULL.

`pDebugProperty`\
de Interfaz que se puede utilizar para recuperar el valor que se va a mostrar.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve el código de error.

## <a name="remarks"></a>Observaciones
 La presentación es "modal" en que este método creará la ventana necesaria, mostrará el valor, esperará la entrada y cerrará la ventana antes de volver al llamador. Esto significa que el método debe controlar todos los aspectos de la visualización del valor de la propiedad, desde la creación de una ventana para la salida hasta la espera de la entrada del usuario, para destruir la ventana.

 Para admitir el cambio del valor en el objeto [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) determinado, puede usar el método [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) , si el valor se puede expresar como una cadena. De lo contrario, es necesario crear una interfaz personalizada, exclusiva para el evaluador de expresiones `DisplayValue` que implementa este método, en el mismo objeto que implementa la `IDebugProperty3` interfaz. Esta interfaz personalizada proporcionaría métodos para cambiar los datos de un tamaño o complejidad arbitrarios.

## <a name="see-also"></a>Consulte también
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)
