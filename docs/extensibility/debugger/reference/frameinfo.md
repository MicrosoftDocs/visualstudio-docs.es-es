---
title: FrameINFO ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO
helpviewer_keywords:
- FRAMEINFO structure
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c40361a9739bf468de2038df4325fa1ac98337c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736782"
---
# <a name="frameinfo"></a>FRAMEINFO
Describe un marco de pila.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct tagFRAMEINFO {
    FRAMEINFO_FLAGS    m_dwValidFields;
    BSTR               m_bstrFuncName;
    BSTR               m_bstrReturnType;
    BSTR               m_bstrArgs;
    BSTR               m_bstrLanguage;
    BSTR               m_bstrModule;
    UINT64             m_addrMin;
    UINT64             m_addrMax;
    IDebugStackFrame2* m_pFrame;
    IDebugModule2*     m_pModule;
    BOOL               m_fHasDebugInfo;
    BOOL               m_fStaleCode;
    BOOL               m_fAnnotatedFrame;
} FRAMEINFO;
```

```csharp
public struct FRAMEINFO {
    public uint              m_dwValidFields;
    public string            m_bstrFuncName;
    public string            m_bstrReturnType;
    public string            m_bstrArgs;
    public string            m_bstrLanguage;
    public string            m_bstrModule;
    public ulong             m_addrMin;
    public ulong             m_addrMax;
    public IDebugStackFrame2 m_pFrame;
    public IDebugModule2     m_pModule;
    public int               m_fHasDebugInfo;
    public int               m_fStaleCode;
    public int               m_fAnnotatedFrame;
} FRAMEINFO;
```

## <a name="members"></a>Miembros
`m_dwValidFields`\
Una combinación de indicadores de la [enumeración FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) que especifica qué campos se rellenan.

`m_bstrFuncName`\
El nombre de la función asociado al marco de pila.

`m_bstrReturnType`\
El tipo de valor devuelto asociado al marco de pila.

`m_bstrArgs`\
Los argumentos de la función asociada al marco de pila.

`m_bstrLanguage`\
El idioma en el que se implementa la función.

`m_bstrModule`\
El nombre del módulo asociado con el marco de pila.

`m_addrMin`\
La dirección de pila física mínima.

`m_addrMAX`\
La dirección máxima de la pila física.

`m_pFrame`\
El [objeto IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) que representa este marco de pila.

`m_pModule`\
El [objeto IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) que representa el módulo que contiene este marco de pila.

`m_fHasDebugInfo`\
No cero`TRUE`( ) si existe información de depuración en la trama dada.

`m_fStaleCode`\
No cero`TRUE`( ) si el marco de pila está asociado con código que ya no es válido.

`m_fAnnotatedFrame`\
No cero`TRUE`( ) si el administrador de depuración de sesión (SDM) anota el marco de pila.

## <a name="remarks"></a>Observaciones
Esta estructura se pasa a la [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) método que se va a rellenar. Esta estructura también está contenida en una lista que se encuentra en el [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) interfaz que, a su vez, se devuelve de una llamada a la [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) método.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
