---
description: Recupera el número de cadenas de valor que se van a mostrar para la propiedad o el campo especificados.
title: 'IEEVisualizerService:: GetValueDisplayStringCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IEEVisualizerService::GetValueDisplayStringCount
- GetValueDisplayStringCount
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f48ff7d513b211396c0eec28f5670bbe648f01b4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080247"
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
