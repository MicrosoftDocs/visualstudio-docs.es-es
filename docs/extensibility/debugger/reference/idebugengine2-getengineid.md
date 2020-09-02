---
title: 'IDebugEngine2:: GetEngineID | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::GetEngineID
helpviewer_keywords:
- IDebugEngine2::GetEngineID
ms.assetid: 0d5674c8-a9b9-4b72-8211-d2d68695775a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f4071e8279c2c4ab615ff625c1bbedebfd8e64ad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80731079"
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

## <a name="parameters"></a>Parámetros
`pguidEngine`\
enuncia Devuelve el GUID del de.

## <a name="return-value"></a>Valor devuelto
Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
Algunos ejemplos de GUID típicos son `guidScriptEng` , `guidNativeEng` o `guidSQLEng` . Los nuevos motores de depuración crearán su propio GUID para la identificación.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra cómo implementar este método para un `CEngine` objeto simple que implementa la interfaz [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) .

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
