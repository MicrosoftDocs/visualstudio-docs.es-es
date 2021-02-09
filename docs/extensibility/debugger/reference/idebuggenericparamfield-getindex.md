---
title: 'IDebugGenericParamField:: GetIndex | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericParamField::GetIndex
ms.assetid: 8e0bdb26-1247-44d9-8d80-ec6e35187fb4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c45f7c83c840566fb494c7944ccab9dbe37c3875
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869705"
---
# <a name="idebuggenericparamfieldgetindex"></a>IDebugGenericParamField::GetIndex
Recupera el índice de este parámetro genérico.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetIndex(
    DWORD* pIndex
);
```

```csharp
int GetIndex(
    out uint pIndex
);
```

## <a name="parameters"></a>Parámetros
`pIndex`\
enuncia Valor de índice de este parámetro genérico.

## <a name="return-value"></a>Valor devuelto
Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Notas
Por ejemplo, para Diccionario (K, V), K es el índice 0, V es el índice 1.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra cómo implementar este método para un objeto **CDebugGenericParamFieldType** que expone la interfaz [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md) .

```cpp
HRESULT CDebugGenericParamFieldType::GetIndex(DWORD* pIndex)
{
    HRESULT hr = S_OK;

    METHOD_ENTRY( CDebugGenericParamFieldType::GetIndex );

    IfFalseGo(pIndex, E_INVALIDARG );
    IfFailGo( this->LoadProps() );
    *pIndex = m_index;

Error:

    METHOD_EXIT( CDebugGenericParamFieldType::GetIndex, hr );
    return hr;
}
```

## <a name="see-also"></a>Vea también
- [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)
