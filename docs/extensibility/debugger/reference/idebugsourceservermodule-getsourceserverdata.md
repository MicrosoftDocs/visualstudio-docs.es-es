---
title: IDebugSourceServerModule::GetSourceServerData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugSourceServerModule::GetSourceServerData
ms.assetid: f15d86aa-1bd9-4b16-a64a-21b01c27db2e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8880f00528b1c2b1f081b6c306e1f94cccc109ec
ms.sourcegitcommit: 845442e2b515c3ca1e4e47b46cc1cef4df4f08d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2019
ms.locfileid: "56450287"
---
# <a name="idebugsourceservermodulegetsourceserverdata"></a>IDebugSourceServerModule::GetSourceServerData
Recupera una matriz de información del servidor de origen.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetSourceServerData(
    ULONG* pDataByteCount,
    BYTE** ppData
);
```

```csharp
public int GetSourceServerData(
    out uint  pDataByteCount,
    out int[] ppData
);
```

#### <a name="parameters"></a>Parámetros
`pDataByteCount`  
[out] Número de bytes en la matriz de datos.

`ppData`  
[out] Referencia a la matriz de datos.

## <a name="return-value"></a>Valor devuelto
Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="example"></a>Ejemplo
El ejemplo siguiente muestra cómo implementar este método para un **CModule** objeto que expone el [IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md) interfaz.

```cpp
HRESULT CModule::GetSourceServerData(ULONG* pDataByteCount, BYTE** ppData)
{
    HRESULT hr = S_OK;
    CComPtr<ISymUnmanagedReader> pSymReader;
    CComPtr<ISymUnmanagedSourceServerModule> pSourceServerModule;

    IfFalseGo( pDataByteCount && ppData, E_INVALIDARG );
    *pDataByteCount = 0;
    *ppData = NULL;

    IfFailGo( this->GetUnmanagedSymReader( &pSymReader ) );
    IfFailGo( pSymReader->QueryInterface( &pSourceServerModule ) );

    IfFailGo( pSourceServerModule->GetSourceServerData( pDataByteCount, ppData ) );

Error:

    return hr;
}
```

## <a name="see-also"></a>Vea también
[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)
