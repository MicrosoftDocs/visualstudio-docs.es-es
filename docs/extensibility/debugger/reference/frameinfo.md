---
title: FRAMEINFO | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
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
Combinación de marcas de la enumeración [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) que especifica qué campos se rellenan.

`m_bstrFuncName`\
Nombre de función asociado al marco de pila.

`m_bstrReturnType`\
El tipo de valor devuelto asociado al marco de pila.

`m_bstrArgs`\
Argumentos de la función asociada al marco de pila.

`m_bstrLanguage`\
Lenguaje en el que se implementa la función.

`m_bstrModule`\
Nombre del módulo asociado al marco de pila.

`m_addrMin`\
Dirección de la pila física mínima.

`m_addrMAX`\
Dirección de la pila física máxima.

`m_pFrame`\
Objeto [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) que representa este marco de pila.

`m_pModule`\
El objeto [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) que representa el módulo que contiene este marco de pila.

`m_fHasDebugInfo`\
Distinto de cero ( `TRUE` ) si la información de depuración existe en el marco especificado.

`m_fStaleCode`\
Distinto de cero ( `TRUE` ) si el marco de pila está asociado a código que ya no es válido.

`m_fAnnotatedFrame`\
Distinto de cero ( `TRUE` ) si el administrador de depuración de la sesión (SDM) anota el marco de pila.

## <a name="remarks"></a>Observaciones
Esta estructura se pasa al método [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) que se va a rellenar. Esta estructura también se incluye en una lista incluida en la interfaz [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) que, a su vez, se devuelve desde una llamada al método [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) .

## <a name="requirements"></a>Requisitos
Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
