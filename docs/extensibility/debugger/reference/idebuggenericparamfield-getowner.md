---
description: Recupera el tipo o el propietario del método de este parámetro genérico.
title: 'IDebugGenericParamField:: GetOwner | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericParamField::GetOwner
ms.assetid: c7f6d166-a69e-40c4-bd0b-1a1fdf9aaacf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4278fdde2b660e722c92f95e076d47c004ebfc4b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091986"
---
# <a name="idebuggenericparamfieldgetowner"></a>IDebugGenericParamField::GetOwner
Recupera el tipo o el propietario del método de este parámetro genérico.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetOwner(
    IDebugField** ppOwner
);
```

```csharp
int GetOwner(
    out IDebugField ppOwner
);
```

## <a name="parameters"></a>Parámetros
`ppOwner`\
enuncia Devuelve el objeto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que posee este parámetro genérico.

## <a name="return-value"></a>Valor devuelto
Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra cómo implementar este método para un objeto **CDebugGenericParamFieldType** que expone la interfaz [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md) .

```cpp
HRESULT CDebugGenericParamFieldType::GetOwner(IDebugField** ppOwner)
{
    HRESULT hr = S_OK;
    CComPtr<IMetaDataImport> pMetadata;

    METHOD_ENTRY( CDebugGenericParamFieldType::GetOwner );

    IfFalseGo(ppOwner, E_INVALIDARG );
    *ppOwner = NULL;

    IfFailGo( this->LoadProps() );
    IfFailGo( m_spSH->GetMetadata( m_idModule, &pMetadata ) );

    switch (TypeFromToken(m_tokOwner))
    {
        case mdtMethodDef:
            {
                mdTypeDef tokClass;
                CComPtr<IDebugField> pClass;
                CDEBUG_ADDRESS caddr;
                CComPtr<IDebugContainerField> pContainer;

                IfFailGo( pMetadata->GetMethodProps( m_tokOwner, &tokClass, NULL, 0, NULL, NULL, NULL, NULL, NULL, NULL ) );
                IfFailGo( m_spSH->CreateClassType(m_idModule, tokClass, &pClass) );
                IfFailGo( pClass->QueryInterface( &pContainer ) );
                IfFailGo( caddr.InitializeMethod( m_idModule, tokClass, m_tokOwner, 0, 0 ) );
                IfFailGo( m_spSH->CreateMethodSymbol( pContainer, caddr, FIELD_SYM_MEMBER, ppOwner ) );
                break;
            }
        case mdtTypeDef:
            {
                IfFailGo( m_spSH->CreateClassType(m_idModule, m_tokOwner, ppOwner) );
                break;
            }
        default:
            {
                ASSERT(!"Unexpected Owner type for Generic Param Field");
                hr = E_FAIL;
            }
    }
Error:

    METHOD_EXIT( CDebugGenericParamFieldType::GetOwner, hr );
    return hr;
}
```

## <a name="see-also"></a>Consulte también
- [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)
