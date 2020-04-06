---
title: IDebugCustomViewer::DisplayValue ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer::DisplayValue
helpviewer_keywords:
- IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 32e444d0d6a30484f708d3001b95e7a71856edd5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732441"
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
[en] Ventana principal

`dwID`\
[en] ID para visores personalizados que admiten más de un tipo.

`pHostServices`\
[in] Reservado. Siempre establecido en null.

`pDebugProperty`\
[en] Interfaz que se puede utilizar para recuperar el valor que se va a mostrar.

## <a name="return-value"></a>Valor devuelto
 Si se `S_OK`realiza correctamente, devuelve ; de lo contrario devuelve código de error.

## <a name="remarks"></a>Observaciones
 La visualización es "modal" en que este método creará la ventana necesaria, mostrará el valor, esperar la entrada y cerrar la ventana, todo antes de volver al autor de la llamada. Esto significa que el método debe controlar todos los aspectos de la visualización del valor de la propiedad, desde la creación de una ventana para la salida, a la espera de la entrada del usuario, a la destrucción de la ventana.

 Para admitir el cambio del valor en el objeto [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) especificado, puede usar el método [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) ,si el valor se puede expresar como una cadena. De lo contrario, es necesario crear una interfaz personalizada `DisplayValue` (exclusiva del evaluador de `IDebugProperty3` expresiones que implementa este método) en el mismo objeto que implementa la interfaz. Esta interfaz personalizada proporcionaría métodos para cambiar los datos de un tamaño o complejidad arbitrarios.

## <a name="see-also"></a>Vea también
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)
