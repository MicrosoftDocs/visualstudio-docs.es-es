---
description: Recupera el número de cadenas de valor que se van a mostrar para la propiedad o el campo especificados.
title: 'IEEVisualizerService:: GetValueDisplayStringCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IEEVisualizerService::GetValueDisplayStringCount
- GetValueDisplayStringCount
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b77e2537e7581bb15f6458b4515d407fcfa1f827
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222853"
---
# <a name="ieevisualizerservicegetvaluedisplaystringcount"></a>IEEVisualizerService::GetValueDisplayStringCount
Recupera el número de cadenas de valor que se van a mostrar para la propiedad o el campo especificados.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetValueDisplayStringCount (
   DWORD         displayKind,
   IDebugField * propertyOrField,
   ULONG *       pcelt
);
```

```csharp
int GetValueDisplayStringCount (
   uint        displayKind,
   IDebugField propertyOrField,
   out ulong   pcelt
);
```

## <a name="parameters"></a>Parámetros
`displayKind`\
de Valor de la enumeración [DisplayKind](../../../extensibility/debugger/reference/displaykind.md) .

`propertyOrField`\
de Una interfaz [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que representa una propiedad o un campo.

`pcelt`\
enuncia Devuelve el número de cadenas de valor que se van a mostrar.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Consulte también
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
