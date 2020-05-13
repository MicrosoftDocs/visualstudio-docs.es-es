---
title: IDebugField::GetExtendedInfo ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dc414dd57e86149e38d7c85d11252eb93efced51
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728866"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
Este método obtiene información ampliada sobre un campo.

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
[en] Selecciona la información que se va a devolver. Los valores válidos son:

|Value|Descripción|
|-----------|-----------------|
|`guidConstantValue`|El valor como una secuencia de bytes.|
|`guidConstantType`|El tipo como una firma de tipo.|

`prgBuffer`\
[fuera] Devuelve la información extendida.

`pdwLen`\
[adentro, fuera] Devuelve el tamaño de la información extendida, en bytes.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Actualmente, este método devuelve solo el tipo o valor de una constante. El autor de la `prgBuffer` llamada debe liberar `CoTaskMemFree` el búfer devuelto <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> mediante una llamada a la función de COM (C++) o (C-).

## <a name="see-also"></a>Vea también
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
