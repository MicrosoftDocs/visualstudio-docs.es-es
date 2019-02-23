---
title: IDebugBeforeSymbolSearchEvent2::GetModuleName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetModuleName
- IDebugBeforeSymbolSearchEvent2::GetModuleName
ms.assetid: 0b4abeac-2eaf-4b2e-a2d5-c9ec303bc869
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d30b9559ab26e4634b82332de538cfe181bb106b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56713573"
---
# <a name="idebugbeforesymbolsearchevent2getmodulename"></a>IDebugBeforeSymbolSearchEvent2::GetModuleName
Recupera el nombre del módulo que se está depurando actualmente.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetModuleName(
    BSTR *pbstrModuleName
);
```

```csharp
public int GetModuleName (
    string pbstrModuleName
);
```

#### <a name="parameters"></a>Parámetros
`pbstrModuleName`

 [out] Nombre del módulo.

## <a name="return-value"></a>Valor devuelto
Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="example"></a>Ejemplo
El ejemplo siguiente muestra cómo implementar este método para un **CDebugBeforeSymbolSearchEventBase** objeto que expone el [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) interfaz.

```cpp
STDMETHODIMP CDebugBeforeSymbolSearchEventBase::GetModuleName(BSTR *pbstrModuleName)
{
    HRESULT hRes = E_FAIL;

    if (m_bstrModuleName)
    {

        *pbstrModuleName = SysAllocString( m_bstrModuleName);

        if (*pbstrModuleName)
        {
            hRes = S_OK;
        }
    }

    return ( hRes );
}
```

## <a name="see-also"></a>Vea también
- [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md)
