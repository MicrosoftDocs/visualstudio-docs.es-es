---
description: Muestra el cuadro de diálogo especificado que permite al usuario seleccionar un puerto.
title: IDebugPortPicker::D isplayPortPicker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a49c1379d2bb3946f75eddd9d80bdccdb370d3ab
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072317"
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
Muestra el cuadro de diálogo especificado que permite al usuario seleccionar un puerto.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT DisplayPortPicker(
   HWND hwndParentDialog,
   BSTR* pbstrPortId
);
```

```csharp
public int DisplayPortPicker(
   int hwndParentDialog,
   out string pbstrPortId
);
```

## <a name="parameters"></a>Parámetros
`hwndParentDialog`\
de Identificador del cuadro de diálogo primario.

`pbstrPortId`\
enuncia Cadena de identificador de puerto.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. Un valor devuelto de `S_FALSE` (o un valor devuelto de `S_OK` con el `BSTR` establecido en `NULL` ) indica que el usuario hizo clic en **Cancelar**.

## <a name="see-also"></a>Consulte también
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
