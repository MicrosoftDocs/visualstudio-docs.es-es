---
title: IDebugField::GetExtendedInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0321dfbdc719d8e155bb1ee035032e2862bb90e0
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56679052"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
Este método obtiene información sobre un campo adicional.

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

#### <a name="parameters"></a>Parámetros
 `guidExtendedInfo`

 [in] Selecciona la información que se va a devolver. Los valores válidos son:

|Valor|Descripción|
|-----------|-----------------|
|`guidConstantValue`|El valor como una secuencia de bytes.|
|`guidConstantType`|El tipo como una signatura de tipo.|

 `prgBuffer`

 [out] Devuelve la información extendida.

 `pdwLen`

 [in, out] Devuelve el tamaño de la información extendida, en bytes.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Actualmente, este método devuelve sólo el tipo o valor de una constante. El llamador debe liberar el búfer devuelto en `prgBuffer` por una llamada de COM `CoTaskMemFree` función (C++) o <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (C#).

## <a name="see-also"></a>Vea también
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)