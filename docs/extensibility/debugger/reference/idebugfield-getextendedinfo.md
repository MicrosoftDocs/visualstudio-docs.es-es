---
description: Este método obtiene información extendida sobre un campo.
title: 'IDebugField:: GetExtendedInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 98d522222d57a0828ebcefe446262033d2d8dfc1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151967"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
Este método obtiene información extendida sobre un campo.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetExtendedInfo( 
   REFGUID guidExtendedInfo,
   BYTE**  prgBuffer,
   DWORD*  pdwLen
);
```

```csharp
int GetExtendedInfo(
   ref Guid guidExtendedInfo,
   IntPtr[] prgBuffer,
   ref uint pdwLen
);
```

## <a name="parameters"></a>Parámetros
`guidExtendedInfo`\
de Selecciona la información que se va a devolver. Los valores válidos son:

|Value|Descripción|
|-----------|-----------------|
|`guidConstantValue`|Valor como una secuencia de bytes.|
|`guidConstantType`|El tipo como una signatura de tipo.|

`prgBuffer`\
enuncia Devuelve la información extendida.

`pdwLen`\
[in, out] Devuelve el tamaño de la información extendida, en bytes.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Actualmente, este método devuelve solo el tipo o el valor de una constante. El llamador debe liberar el búfer devuelto en `prgBuffer` al llamar a la función de com `CoTaskMemFree` (C++) o <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (C#).

## <a name="see-also"></a>Consulte también
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
