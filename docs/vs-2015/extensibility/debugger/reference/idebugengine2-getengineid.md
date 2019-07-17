---
title: IDebugEngine2::GetEngineID | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::GetEngineID
helpviewer_keywords:
- IDebugEngine2::GetEngineID
ms.assetid: 0d5674c8-a9b9-4b72-8211-d2d68695775a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab0bfe52090ab719bbc2fbd442b9b609b5991e84
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68195983"
---
# <a name="idebugengine2getengineid"></a>IDebugEngine2::GetEngineID
Obtiene el GUID del motor de depuración (DE).

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetEngineID(
    GUID* pguidEngine
);
```

```csharp
int GetEngineID(
    out Guid pguidEngine
);
```

#### <a name="parameters"></a>Parámetros
`pguidEngine`

 [out] Devuelve el GUID de la DE.

## <a name="return-value"></a>Valor devuelto
Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
Algunos ejemplos de GUID típicos son `guidScriptEng`, `guidNativeEng`, o `guidSQLEng`. Motores de depuración nuevo creación su propio GUID para la identificación.

## <a name="example"></a>Ejemplo
El ejemplo siguiente muestra cómo implementar este método para una sencilla `CEngine` objeto que implementa el [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) interfaz.

```cpp
HRESULT CEngine::GetEngineId(GUID *pguidEngine) {
    if (pguidEngine) {
        // Set pguidEngine to guidBatEng, as defined in the Batdbg.idl file.
        // Other languages would require their own guidDifferentEngine to be
        //defined in the Batdbg.idl file.
        *pguidEngine = guidBatEng;
        return NOERROR; // This is typically S_OK.
    } else {
        return E_INVALIDARG;
    }
}
```

## <a name="see-also"></a>Vea también
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
